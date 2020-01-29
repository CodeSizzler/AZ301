<h1>Getting started with Azure Building Blocks</h1>

<h2>Introduction</h2>
<p>In this article you are going to learn about Azure Building Blocks. It is a command line tool accompanied by a set of ARM templates that is designed to simplify the process of ARM deployments for those who lack the skills for full arm deployments.</p>

<h2>Pre-requisites</h2>
<p>To perform this demo, you must have valid Azure subscription and some basic knowledge on Azure Building Blocks, ARM Templates.</p>

<h2>Demo</h2>
<p>Log-in to Azure portal with your account using www.portal.azure.com. In Azure click on create a new resource and search for Template Deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-03/01.jpg"/>
<p>In the template deployment panel click on Build your own template in the editor.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-03/02.jpg"/>
<p>When it prompts click on Load file and upload the vnet-simple-template.json.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-03/03.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-03/04.jpg"/>
<p>After uploading the file click on save.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-03/05.jpg"/>
<p>In the template deployment panel create a new resource group, also edit the parameters that you need. After editing the parameters click the tick box and click on purchase.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-03/06.jpg"/>
<p>Wait until the deployment gets success. After the deployment completes navigate to the created resource. In the overview page monitor the resource settings.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-03/07.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-03/08.jpg"/>
<p>In Azure portal click on Cloud Shell and start a Bash session.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-03/09.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-03/10.jpg"/>
<p>In the Bash panel run the following command to create a local directory and install Azure Building Blocks npm package.</p>
	<p>mkdir ~/.npm-global	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-03/11.jpg"/>
<p>After installing Azure Building Blocks run the following command to update the npm package.</p>
	<p>npm config set prefix '~/.npm-global'	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-03/12.jpg"/>
<p>Run the following command after updating the npm package to open the npm configuration file for editing.</p>
	<p>vi ~/.bashrc	</p>
<p>After running the previous command run the following commands to add the newly created and to install the building blocks. (Note: Type a and press enter to start a new command line)</p>
	<p>export PATH="$HOME/.npm-global/bin:$PATH"	</p>
	<p>npm install -g @mspnp/azure-building-blocks	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-03/13.jpg"/>
<p>After running the command type Exit and press enter to restart the Bash session. Run the following command after restarting the bash session to download the git repository containing Azure Building Blocks template.</p>
	<p>git clone https://github.com/mspnp/template-building-blocks.git	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-03/14.jpg"/>
<p>Run the following command after downloading the git repository to view the content of Azure building blocks.</p>
	<p>cat ./template-building-blocks/scenarios/vnet/vnet-simple.json 	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-03/15.jpg"/>
<p>After reviewing the Azure building blocks content run the following command to designate your subscription.</p>
	<p>SUBSCRIPTION_ID=$(az account list --query "[0].id" | tr -d '"')	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-03/16.jpg"/>
<p>After that run the following command to designate to the name of your resource group and the location of your resource group.</p>
	<p>RESOURCE_GROUP='Codesizzlzer-Rg'	</p>

	<p>LOCATION=$(az group list --query "[?name == 'Codesizzler-Rg'].location" --output tsv)	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-03/17.jpg"/>
<p>Run the following command to deploy a Virtual Network using Azure Building Blocks.</p>
	<p>azbb -g $RESOURCE_GROUP -s $SUBSCRIPTION_ID -l $LOCATION -p ./template-building-blocks/scenarios/vnet/vnet-simple.json --deploy	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-03/18.jpg"/>
<p>Close the Bash session and navigate to the created resource group. In the resource group click on deployment and monitor the newly deployed resource.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-03/19.jpg"/>



















