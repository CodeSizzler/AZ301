<h1>Connecting Azure Search to Azure Cosmos DB account</h1>

<h2>Introduction</h2>

<h2>Pre-requisites</h2>

<h2>Demo</h2>
<p>Log-in with you Azure account using www.portal.azure.com. In Azure portal click on create a new resource and search for Cosmos DB and use the search result to create a Cosmos DB account with the following configurations.</p>
	<p>•Subscription: Select a valid subscription
	<p>•Resource group: Create a new resource group
	<p>•Location: Select a valid location
	<p>•Name: Give a valid name
	<p>•API: SQL API
<p>After configuring all the setting click on Review+Create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-08/01.jpg"/>
<p>Wait until the validation process gets succeed. Then click on create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-08/02.jpg"/>
<p>After the deployment gets completed navigate to the deployed resource.<p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-08/03.jpg"/>
<p>From the overview panel of your Cosmos DB account navigate to Add Azure Search panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-08/04.jpg"/>
<p>In the add Azure Search panel click on add your database to add the existing Azure Search account. If you didn’t have the existing one create the new one by clicking the create option.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-08/05.jpg"/>
<p>When it prompts provide the required details and click on next.</p>
<p>Note: Your Cosmos DB account should contain a valid data set. If not your Cosmos DB endpoint will not valid.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-08/06.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-08/07.jpg"/>
<p>In the indexer panel configure the things as you need and click on create the indexer.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-08/08.jpg"/>
<p>And finally schedule your search and click on submit.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-08/09.jpg"/>
<p>When you click on submit it will add your Azure Search account with your Azure Cosmos DB account.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-08/10.jpg"/>

