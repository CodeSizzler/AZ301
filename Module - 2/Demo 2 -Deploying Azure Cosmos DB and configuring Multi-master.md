<h1>Deploying Azure Cosmos DB and configuring Multi-master</h1>

<h2>Introduction</h2>
<p>This article helps you to create and manage the Azure Cosmos DB account using Azure portal.</p>

<h2>Pre-requisites</h2>
<p>To perform this demo you must have valid Azure subscription and some basic knowledge on Azure Cosmos DB.</p>

<h2>Demo</h2>
<p>Log-in to Azure portal with your account using www.portal.azure.com. In Azure portal click on create a new resource and under the Database category select Cosmos DB.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-12/01.jpg"/>
<p>When it prompts configure the following settings and click on Review+Create.</p>
	<p>•Subscription: Select a valid</p> 
	<p>•Resource group: Create a new resource group</p>
	<p>•Location: Select a valid location</p>
	<p>•Name: Give a valid name</p>
	<p>•API: Code (SQL)</p>
	<p>•Geo-Redundancy: Enabling this option will activate the automatic failover.</p>
	<p>•Multi-region writes: Enabling this option gives access for the multiple region.</p>
	<p>•Availability zone: Disable</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az301-12/02.jpg"/>
<p>Wait until the validation gets complete. Once your validation gets completed click on create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-12/03.jpg"/>
<p>Wait until the deployment gets complete. After the deployment gets completed navigate to the deployed resource.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-12/04.jpg"/>
<p>From the overview panel of the Cosmos DB account navigate to the Replicate data globally panel. In the replicate data globally blade you can able to enable the Multi Region Writes if you do not enable that while deploying. In that panel you can able to add and delete the regions. After making the changes click on save to save the process.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-12/05.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-12/06.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-12/07.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-12/08.jpg"/>
