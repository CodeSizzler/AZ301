<h1>Deploying a Virtual Machine using Key Vault Secret</h1>

<h2>Introduction</h2>
<p>In this article you are going to learn about deploying the Virtual Machine using the Key Vault secret in Windows PowerShell.</p>

<h2>Pre-requisite</h2>
<p>To perform this demo, you must have valid Azure subscription and some basic knowledge on Windows PowerShell, Key Vault.</p>

<h2>Demo</h2>
<p>Run the PowerShell ISE as an administrator in your machine and run the following command to log in with your Azure account.</p>
	<p>Connect-AzureRmAccount	</p>
<p>When it prompts log-in with your Azure account which has the valid Azure subscription.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-013/01.jpg"/>
<p>Then set the parameters to your requirements by running the following command.</p>
	<p>$vaultName = "contosovault"	</p>
	<p>$resourceGroup = "contosovaultrg"	</p>
	<p>	$location = "local"	</p>
	<p>$secretName = "MySecret"	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-013/02.jpg"/>
<p>Then run the following commands to create a resource group.</p>
	<p>New-AzureRmResourceGroup `	</p>
  	<p>-Name $resourceGroup `	</p>
  	<p>-Location $location	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-013/03.jpg"/>
<p>After creating the resource group run the following command to create a key vault.</p>
	<p>New-AzureRmKeyVault `	</p>
 	<p>-VaultName $vaultName `	</p>
  	<p>-ResourceGroupName $resourceGroup `	</p>
  	<p>-Location $location	</p>
	<p>-EnabledForTemplateDeployment	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-013/04.jpg"/>
<p>Now set the key vault secret value by running the following command. Replace the Password for your virtual machine with the password you need.</p>
	<p>$secretValue = ConvertTo-SecureString -String '<Password for your virtual machine>' -AsPlainText -Force
	<p>Set-AzureKeyVaultSecret `	</p>
	<p>-VaultName $vaultName `	</p>
  	<p>-Name $secretName `	</p>
  	<p>-SecretValue $secretValue	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-013/05.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-013/06.jpg"/>
<p>Then navigate to Azure portal using www.portal.azure.com. In Azure portal open the Key Vault which you have created in this session. From the overview panel of your Key Vault navigate to the Access Policies panel and enable the Azure Resource Manager for Template Deployment. After enabling that option save the process and get back to the PowerShell session.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-013/07.jpg"/>
<p>Now download the template files from - http://bit.ly/keyvaultvm. Open the azuredeploy.parameters.json file and replace it with the following content.</p>
	<p> "$schema":
	<p>"https://schema.management.azure.com/schemas/2015-01-01/deploymentParameters.json#",
	<p>    "contentVersion":  "1.0.0.0",	</p>
	<p>    "parameters":  {	</p>
	<p>       "adminUsername":  {	</p>
	<p>         "value":  "demouser"	</p>
	<p>               },
	<p>       "adminPassword":  {	</p>
	<p>         "reference":  {	</p>
	<p>            "keyVault":  {	</p>
	<p>              "id":	</p>
	<p>"/subscriptions/xxxxxx/resourceGroups/RgKvPwd/providers/Microsoft.KeyVault/vaults/KvPwd"	</p>
	<p>               },	</p>
	<p>            "secretName":  "MySecret"	</p>
	<p>               }	</p>
	<p>              },	</p>
	<p>       "dnsLabelPrefix":  {	</p>
	<p>          "value":  "mydns123456"	</p>
	<p>              },	</p>
	<p>    "windowsOSVersion":  {	</p>
	<p>         "value":  "2016-Datacenter"	</p>
	<p>               }	</p>
	<p>              }	</p>
	<p>             }	</p>
<p>Save it and get back to the PowerShell session. Now run the following command to deploy a Virtual Machine using the Key Vault Secret.</p>
	<p>New-AzureRmResourceGroupDeployment `	</p>
 	<p>-Name KVPwdDeployment	</p>
 	<p> -ResourceGroupName $resourceGroup `	</p>
 	<p>-TemplateFile "<Fully qualified path to the azuredeploy.json file>" `	</p>
 	<p>-TemplateParameterFile "<Fully qualified path to the azuredeploy.parameters.json file>"	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-013/08.jpg"/>
<p>Once the deployment gets completed navigate to the Azure portal and check that the Virtual Machine is deployed.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-013/09.jpg"/>






