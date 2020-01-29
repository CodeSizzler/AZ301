<h1>Integrating Azure Solution Components using Messaging Services</h1>

<h2>Introduction</h2>
<p>In this article you are going to deploy a service bus and going to integrate the Azure solution components using message service.</p>

<h2>Prerequisites</h2>
<p>To perform this demo, you need a valid Azure subscription and some knowledge on Service bus.</p>

<h2>Create a Service Bus namespace</h2>
<p>Log in to Azure Portal with your account using www.portal.azure.com. In Azure portal click on Create a Resource and search for Service Bus.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/01.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/02.jpg"/>
<p>Create Service bus with following configurations and click on create</p>
	<p>•Name: Demouser1</p>
	<p>•Pricing tier: Basic</p>
	<p>•Subscription: Visual Studio Enterprises</p>
	<p>•Resource Group: Codesizzler-RG1</p>
	<p>•Location: West US</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/03.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/04.jpg"/>

<h2>Create a Service Bus Queue</h2>
<p>In the Azure portal click on a Resource group blade Click on Codesizzler-RG1.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/05.jpg"/>
<p>The Codesizzler-RG1 blade click the created Demouser1.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/06.jpg"/>
<p>Demouser Service bus namespace blade click the Entities blade select the Queues. and click the +Queue Button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/07.jpg"/>
<p>Create the queue pane following settings:</p>
	<p>•Name: codesizzlerqueue</p>
	<p>•Leave all remaining Setting to default.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/08.jpg"/>

<h2>Get Service Bus Connection String</h2>
<p>Back on the Demouser Service bus namespace click on Shared access policies. And click on the RootManageSharedAccesskey</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/09.jpg"/>
<p>RootManageSharedAccessKey pane, locate the record value Copy of the Primary Connection.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/10.jpg"/>

<h2>Create a logic app</h2>
<h2>Create an Azure Storage account</h2>
<p>In the Azure portal click on  Create a resource and search for Storage Account.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/11.jpg"/>
<p>Click on Storage account create Button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/12.jpg"/>
<p>Storage Account Configuration of the following settings:</p>
	<p>•Name: Cloud user</p>
	<p>•Choose on the Deployment model</p>
	<p>•Account kind: Storage (general purpose v1)</p>
	<p>•Location: (Asia pacific) Southeast Asia</p>
	<p>•Replication: Locally-redundant storage (LRS)</p>
	<p>•Performance: Standard</p>
<p>Click on Next Page.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/13.jpg"/>
	<p>•Secure transfer required section Select the Disabled Option.</p>
<p>Finally click the Review+ create button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/14.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/15.jpg"/>
<p>In the Azure portal Click on a resource group. Resource group blade click on Codesizzler-RG1.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/16.jpg"/>
<p>Resource group (Codesizzler-RG1) Created on the Click on the Storage account blade. (Cloud user).</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/17.jpg"/>
<p>Cloud user storage Blade Click on the Blobs Site.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/18.jpg"/>
<p>Cloud user storage account blade and blobs site navigate on Click the +Container.</p>
<p>New Container blade configuration of following settings:</p>
	<p>•Name: codesizzlercontainer</p>
	<p>•Public access level: Blob (anonymous read access for blobs only)</p>
<p>Finally Click on the Ok Button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/19.jpg"/>

<h2>Create a logic app</h2>
<p>In the Azure portal click on Create a resource blade>Search the Marketplace>Type the Logic App.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/20.jpg"/>
<p>Logic App Create Click Button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/21.jpg"/>
<p>Logic App Configuration the configuration of following Settings:</p>
`	<p>•Name: ServiceBusWorkflow</p>
	<p>•Subscription: The Subscription drop-down list set to its default value.</p>
	<p>•Resource group: Use existing</p>
	<p>•Location: (Southest Asia) Previous task</p>
	<p>•Log Analytics: Select the of Button.</p>
<p>Finally Click the create button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/22.jpg"/>

<h2>Configure logic app steps</h2>
<p>In the portal click on a resource group Codesizzler-RG1 blade. Codesizzler-RG1 Click on the Created the ServiceBusWorkflow Logic App early previous task.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/23.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/24.jpg"/>
<p>ServiceBusWorkflow Logic App Click the Logic Apps Designer blade. Logic App Designer Click the Blank Logic App tile in the Templates section.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/25.jpg"/>
<p>Logic App Designer Configuration Following Settings:</p>
	<p>•In the Search on the text box on Service Bus</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/26.jpg"/>
	<p>•In the search select the trigger named When a message is received in a queue (auto-complete) - Service Bus.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/27.jpg"/>
	<p>•Next Step on the In the Connection Name type the Service Bus Connection. And Service Bus Policy Type RootManage Shared AccessKey.</p>
<p>Finally Click the create button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/28.jpg"/>
<p>In the When a message is received in a queue (auto-complete) step Configuration of following Settings:</p>
	<p>•Queue name: Codesizzlerqueue</p>
	<p>•Interval: 30 min</p>
	<p>•Frequency: Choose on Second Entry</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/29.jpg"/>
<p>Finally click on +New step Button.</p>
<p>Logic Apps Designer blade, perform the configuration of following Settings:</p>
	<p>•In the Search on the text box on Storage blob. and select the action named Create blob - Azure Blob Storage.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/30.jpg"/>
<p>Next Step the Connection name type the Storage Connection. Finally Click the create button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/31.jpg"/>
<p>In the Create Blob step, the configuration of following Settings:</p>
	<p>•Folder Path Name: /codesizzlercontainer</p>
	<p>•Blob Name: Content Type</p>
	<p>•Blob content: String (…)</p>
<p>Finally Click the Save Button at the Logic Apps Designer blade.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/32.jpg"/>

<h2>Open Cloud Shell</h2>
<h2>Validate Logic App using Node.js</h2>
<p>In the portal, click on the Cloud Shell icon to open a new shell instance. Click the Create storage button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/33.jpg"/>
<p>Cloud Shell command prompt at the bottom of the portal, type in the following command and press and enter.</p>
	<p>npm install azure	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/34.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-07/35.jpg"/>



















