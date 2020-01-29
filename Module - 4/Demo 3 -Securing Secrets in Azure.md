<h1>Securing Secrets in Azure</h1>

<h2>Introduction</h2>
<p>This article helps you to secure your secrets in Azure Vault. Azure Key Vault stores your secrets like passwords, meta data to the Vault. Also, you can able to learn how to deploy a Virtual Machines and Azure Key Vault using Azure ARM Template (Custom Deployment).</p>

<h2>Prerequisites</h2>
<p>To perform this demo user must have a valid Azure subscription and some knowledge on Azure Key Vault, Azure ARM Templates.</p>

<h2>Demo</h2>
<p>Log-in to Azure portal with your account using www.portal.azure.com. In Azure portal click on create a new resource and search for Key Vault.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/01.jpg"/>
<p>When it prompts create a Key Vault with following configurations.</p>
	<p>•Name: CodeSizzlerKeyVault</p>
	<p>•Subscription: Select a valid subscription</p>
	<p>•Resource group: Create a new resource group</p>
	<p>•Location: Select a valid location</p>
	<p>•Pricing tier: Standard</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/02.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/03.jpg"/>
<p>Wait until the deployment gets succeed. After the deployment gets completed navigate to the created resource group and click on the Key Vault.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/04.jpg"/>
<p>From the overview panel navigate to the Secret panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/05.jpg"/>
<p>In the secret panel click on +Generate/Import. When it prompts provide the following details and click on create.</p>
	<p>•Upload option: Manual</p>
	<p>•Name: CodeSizzlerSecret</p>
	<p>•Value: Provide a valid secret</p>
	<p>•Enabled: Yes</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/06.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/07.jpg"/>
<p>After creating the secret navigate to the secret panel and refresh it. Note that you can able to see the created secret.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/08.jpg"/>
<p>In Azure portal start a PowerShell Bash within the Cloud Shell panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/09.jpg"/>
<p>In the Bash session run the following command to log-in with your account in Azure portal.</p>
	<p>az login	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/10.jpg"/>
<p>After logging in to the Azure portal run the following command to retrieve the resource group name an Key Vault.</p>
	<p>RESOURCE_GROUP='CodeSizzler-Rg'	</p>
	<p>KEY_VAULT_NAME=$(az keyvault list --resource-group $RESOURCE_GROUP --query "[0].name" --output tsv)	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/11.jpg"/>
<p>Note: If you have more than one subscription run the following command to select a subscription - az account set --subscription "Subscription I’d" otherwise ignore it.</p>
<p>Run the following command to list the secrets in the created Key Vault.</p>
	<p>az keyvault secret list --vault-name $KEY_VAULT_NAME	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/12.jpg"/>
<p>To display the value of secret run the following command in the Bash panel and note that the output shows the secret which you have provided during the deployment.</p>
	<p>az keyvault secret show --vault-name $KEY_VAULT_NAME --name CodeSizzlerSecret --query value --output tsv	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/13.jpg"/>
<p>After identifying the secret run the following command to add a new secret to the Key Vault.</p>
	<p>az keyvault secret set --vault-name $KEY_VAULT_NAME --name CodeSizzlerSecret --value 8973425150	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/14.jpg"/>
<p>Run the following command to list the secrets in the Key Vault that you have created.</p>
	<p>az keyvault secret list --vault-name $KEY_VAULT_NAME --query "[*].{Id:id,Created:attributes.created}" --out table	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/15.jpg"/>
<p>Close the Bash panel and click on create a new resource. In the search place search for Template deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/16.jpg"/>
<p>When it prompts click on create and select Build you own template in editor.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/17.jpg"/>
<p>In the template editor panel click on upload and upload the secret-template.json template file.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/18.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/19.jpg"/>
<p>After uploading the template file, review it and click on save.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/20.jpg"/>
<p>When you click on save it will navigate you to the custom deployment panel. In the custom deployment panel provide the following details and proceed.</p>
	<p>•Subscription: Select a valid subscription</p>
	<p>•Resource group: Select the existing resource group which contains the Key Vault.</p>
	<p>•Vault Name: Provide a valid name</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/21.jpg"/>
<p>Navigate to the home page of Azure portal. In Azure portal click on create a new resource and search for Template deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/22.jpg"/>
<p>When it prompts click on create and select Build you own template in editor.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/23.jpg"/>
<p>In the template editor panel click on upload and upload the storage-template.json template file. This will create a Storage account using the template deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/24.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/25.jpg"/>
<p>After uploading the template file review the content and click on save.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/26.jpg"/>
<p>When you click on save it will navigate you to the custom deployment panel. In the custom deployment panel provide the following details and proceed.</p>
	<p>•Subscription: Select a valid name</p>
	<p>•Resource group: Select the existing resource group which you are using in this lab</p>
	<p>•Value name: Provide a valid name</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/27.jpg"/>
<p>Wait until the deployment gets complete. After the deployment gets completed navigate to the resource and review the secrets created in this session.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/28.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/29.jpg"/>
<p>In the secrets panel click on vmSecrets. When it prompts click on Show hidden value to view the secret.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/30.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/31.jpg"/>
<p>In Azure portal start a Bash session within the Cloud Shell panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/32.jpg"/>
<p>In the Bash panel run the following command to log-in with you account in Azure portal.</p>
	<p>az login	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/33.jpg"/>
<p>After getting logged in to the Azure portal run the following command to retrieve the resource group and resource id of the Key Vault which you have created earlier in this lab.</p>
	<p>RESOURCE_GROUP='CodeSizzler-Rg'	</p>
	<p>KEY_VAULT_ID=$(az keyvault list --resource-group $RESOURCE_GROUP --query "[0].id" --output tsv)	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/34.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/35.jpg"/>
<p>Note: If you have multiple subscriptions run the command az account set --subscription "Subscription I’d" to select a subscription, otherwise ignore it.</p>
<p>Run the following command to create a variable to the Key Vault.</p>
	<p>KEY_VAULT_ID_REGEX="$(echo $KEY_VAULT_ID | sed -e 's/\\/\\\\/g; s/\//\\\//g; s/&/\\\&/g')"	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/36.jpg"/>
<p>After creating the variable click on the upload icon in the bash panel to upload the template files.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/37.jpg"/>
<p>When it prompts upload the vm-template.parameters.json and vm-template files.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/38.jpg"/>
<p>After uploading the template and parameter files run the following command to replace the Key Vault ID.</p>
	<p>sed -i.bak1 's/"$KEY_VAULT_ID"/"'"$KEY_VAULT_ID_REGEX"'"/' ~/vm-template.parameters.json	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/39.jpg"/>
<p>To verify that the Key Vault ID is replaced successfully run the following command.</p>
	<p>cat ~/vm-template.parameters.json	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/40.jpg"/>
<p>Close the Bash panel and navigate to the created resource group. From the resource group navigate to the created Key Vault.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/41.jpg"/>
<p>From the Key Vault overview panel navigate to the Access policies blade. In the access policies blade click on Click to show advanced access policies.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/42.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/43.jpg"/>
<p>When it prompts click on the check box of Enable access to Azure Resource Manager for template deployment and click on save.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/44.jpg"/>
<p>In Azure portal start a Bash session and log-in to Azure portal by using the command az login, after logging in to the Azure portal run the following commands to deploy a Virtual Machine using the Azure resource manager template with specified parameters.</p>
	<p>az group deployment create --resource-group $RESOURCE_GROUP --template-file ~/vm-template.json --parameters @~/vm-template.parameters.json	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/45.jpg"/>
<p>Wait until the deployment gets complete. After the deployment gets completed run the following commands to retrieve the Azure Key Vault, resource group name and the password of the Virtual Machine.</p>
	<p>RESOURCE_GROUP='CodeSizzler-Rg'	</p>

	<p>KEY_VAULT_NAME=$(az keyvault list --resource-group $RESOURCE_GROUP --query "[0].name" --output tsv)	</p>

	<p>az keyvault secret show --vault-name $KEY_VAULT_NAME --name vmPassword --query value --output tsv	</p>

	<p>PUBLIC_IP=$(az network public-ip list --resource-group $RESOURCE_GROUP --query "[0].ipAddress" --output tsv)	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/46.jpg"/>
<p>After retrieving all the details run the following command to connect with the Virtual Machine using SSH. When it prompts type yes and click on enter.</p>
`	<p>ssh Student@$PUBLIC_IP	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/47.jpg"/>
<p>Provide the password of the Virtual Machine which you have provided while deploying the Virtual Machine.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/48.jpg"/>
<p>By providing the password you can able to connect with the Virtual Machine.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-10/49.jpg"/>













