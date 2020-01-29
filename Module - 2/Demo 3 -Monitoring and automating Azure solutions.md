<h1>Monitoring and automating Azure solutions</h1>

<h2>Introduction</h2>
<p>This article helps you to perform Azure automating solutions. Here you are going to create a Linux Virtual Machine, Azure Automation account. Also, you are going to create a DCS configuration to the Linux Virtual Machine using PowerShell.</p>

<h2>Prerequisites</h2>
<p>To perform this demo user must have a valid Azure subscription and some basic knowledge on DSC and Linux.</p>

<h2>Demo</h2>
<p>Log-in to Azure portal with your account using www.portal.azure.com. In Azure portal start a Bash session with the Cloud Shell.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/01.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/02.jpg"/>
<p>In the bash panel click on upload and upload the template file linux-template.json.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/03.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/04.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/05.jpg"/>
<p>After uploading the template file run the following commands to create a new resource group.</p>
	<p>RESOURCE_GROUP='Name of your resource group'	</p>
	<p>LOCATION='<Azure region>'	</p>
	<p>az group create --name $RESOURCE_GROUP --location $LOCATION	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/06.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/07.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/08.jpg"/>
<p>After creating the resource group run the following command to deploy a Azure resource manager template with the specified parameters in the uploaded template file.</p>
	<p>az group deployment create --resource-group $RESOURCE_GROUP --template-file ~/linux-template.json --parameters password=Pa55w.rd1234	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/09.jpg"/>
<p>Close the bash session and back to Azure portal. In Azure portal click on create a new resource and search for Automation.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/10.jpg"/>
<p>When it prompts create an automation account with following configurations.</p>
	<p>•Name: For your choice</p>
	<p>•Subscription: Select a valid subscription</p>
	<p>•Resource group: Create a new resource group</p>
	<p>•Location: Select a valid location</p>
	<p>•Create Azure run as account: Yes</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/11.jpg"/>
<p>Wait until the deployment gets complete. After the deployment gets compete navigate to the newly created Automation account.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/12.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/13.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/14.jpg"/>
<p>In the Automation account navigate to the Modules gallery.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/15.jpg"/>
<p>In the modules gallery panel search for nx when it prompts click on Import. In the import panel click on OK.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/16.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/17.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/18.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/19.jpg"/>
<p>After the importing process gets completed navigate back to the Automation account overview panel. From the overview panel navigate to the Desired State Configuration (DSC) panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/20.jpg"/>
<p>In the DSC panel select configuration and click on add.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/21.jpg"/>
<p>When it prompts upload the lampserver.ps1 file and click on ok.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/22.jpg"/>
<p>In the import panel paste the following content in the description panel and click on ok. (Description: LAMP Server configuration using PHP and MySQL)</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/23.jpg"/>
<p>Refresh the DSC panel to list the newly created lampserver configuration.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/24.jpg"/>
<p>Navigate to the lampserver configuration and click on Compile. When it prompts click on ok.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/25.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/26.jpg"/>
<p>Navigate back to the Automation panel and click on Node. In the node blade click add to add a node.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/27.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/28.jpg"/>
<p>When it prompt select the Linux Virtual Machine which you have crated earlier in this session.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/29.jpg"/>
<p>Click on connect and in the registration blade configure the required settings. After configuring the following settings click on ok.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/30.jpg"/>
<p>Navigate back to the Automation panel and click on the Virtual Machine node that you added before.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/31.jpg"/>
<p>In the Virtual Machine node panel click on Assign node configuration. When it prompts select the lampserver.host and click on ok.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-11/32.jpg"/>
<p>Refresh the DCS panel and verify that the Linux Virtual Machine has complaint status.</p>



















