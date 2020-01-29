<h1>Deploying Key Vault using Azure Portal</h1>

<h2>Introduction</h2>
<p>In this article you are going to learn about how to deploy an Azure Key Vault and store a secret in it using Azure portal.</p>

<h2>Pre-requisite</h2>
<p>To perform this demo, you must have valid Azure subscription and some basic knowledge on Azure Key Vault.</p>

<h2>Demo</h2>
<p>Log in to Azure portal with your account using www.portal.azure.com. In Azure porta click on create a new resource.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-014/01.jpg"/>
<p>When it prompts search for Key Vault and create a new Key Vault with the following configurations.</p>
	<p>•Name: Give a unique name for your Key Vault</p>
	<p>•Subscription: Select a valid subscription</p>
	<p>•Resource group: Create a new resource group</p>
	<p>•Location: Select a data centre which is near to your location</p>
	<p>•Pricing tier: Standard</p>
<p>After configuring all the settings click on Review + Create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-014/02.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-014/03.jpg"/>
<p>Once the validation gets passed click on create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-014/04.jpg"/>
<p>Wait until the deployment gets complete. After the deployment gets completed navigate to the created resource.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-014/05.jpg"/>
<p>From the overview panel of the Key Vault navigate to the Secrets panel and +Generate/Import to add a new Key Vault secret.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-014/06.jpg"/>
<p>When it prompts provide a valid secret and click on create.</p>
	<p>•Upload option: Manual</p>
	<p>•Name: Give a valid name</p>
	<p>•Value: Provide the secret which you want to create</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-014/07.jpg"/>
<p>Once it gets created you can able to view your secret through the portal.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-014/08.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-014/09.jpg"/>


