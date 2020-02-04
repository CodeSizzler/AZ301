<h1>Implementing and Managing Azure Web Apps</h1>

<h2>Introduction</h2>
<p>In this article you are going to learn about how to create and configure your Web app using Azure portal.</p>

<h2>Pre-requisites</h2>
<p>To perform this demo, you must have valid Azure subscription and some knowledge on Azure Web app.</p>

<h2>Demo</h2>
<p>Log-in with Azure portal with your account using www.portal.azure.com. In Azure portal click on Create a new resource>Web>Web app.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/01.jpg"/>
<p>Create a web app with following configuration and click on create.</p>
	<p>•App name: codesizzleroffecial</p>
	<p>•Subscription: Select a valid subscription</p>
	<p>•Resource group: Create a new resource codesizzleroffecial</p>
	<p>•OS: Windows</p>
	<p>•Publish: Code</p>
	<p>•App Service plan and Location: Create a new app service plan</p>
	<p>•Name: codesizzlerdemo</p>
	<p>•Location: Select a valid location</p>
	<p>•Pricing tier: S1 Standard</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/02.jpg"/>
<p>Navigate to the newly created web app and note the URL, service plan. In the overview page of web app click on browse icon. It will display the default App Service home page.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/03.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/04.jpg"/>
<p>Close the browser and navigate to the Deployment slot of created web app. In the deployment slot panel click on +Add a slot to add a slot with following setting.</p>
	<p>•Name: codesizzlerdeploymentslot</p>
	<p>•Configuration Source: Do not clone settings</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/05.jpg"/>
<p>Navigate to the newly created deployment slot.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/06.jpg"/>
<p>In the web app blade, use the Browser toolbar icon to open a new browser.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/07.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/08.jpg"/>
<p>Close the browser.</p>
<p>In the Azure portal, from the web app blade, display its Deployment slot blade.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/09.jpg"/>
<p>On the staging - Deployment Center blade, configure the following settings :</p>
	<p>•Source control: Local Git</p>
	<p>•Build provider: App Service Kudu build server</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/10.jpg"/>
<p>Navigate to the Deployment center and press the local Git to mark it.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/11.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/12.jpg"/>
<p>In the deployment slots blade, add a slot with the following settings :</p>
	<p>•Name : Codesizzlerdemo</p>
	<p>•Configuration Source: Don't clone configuration from an existing slot</p>
<p>Deployment center blade, use the Deployment Credentials toolbar icon to display User Credentials pane.</p>
	<p>•Name: Codesizzlerdemo</p>
	<p>•Password: for your choice</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/13.jpg"/>
<p>Deploy code to the staging deployment slot and perform a slot swap.</p>
	<p>•Azure- Portal, start Azure-shell session in the Cloud Shell pane.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/14.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/15.jpg"/>
<p>In the PowerShell pane run the following commands.</p>
	<p>git clone https://github.com/Azure-Samples/php-docs-hello-world	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/16.jpg"/>
	<p>Set-Location -Path $HOME/php-docs-hello-world/	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/17.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/18.jpg"/>
<p>Close the browser tab the Hello World.</p>
<p>On the Swap blade, slot swap with the following settings:</p>
	<p>•Swap type: swap</p>
	<p>•Source: staging</p>
	<p>•Destination: production</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/19.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/20.jpg"/>
<p>On the staging blade, use the Browse toolbar icon to open a new browser tab.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/21.jpg"/>
<p>Close the browser.</p>
<p>From the staging blade, display its Deployment slots blade.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/22.jpg"/>
	<p>•Use the Browse toolbar icon to open a new browser tab.</p>
	<p>•Displaying the Hello World.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/23.jpg"/>
<p>Close the browser.</p>
<p>Configure and test autoscaling of the Azure:</p>
	<p>•Azure portal, from the web app blade.</p>
	<p>•Scale out (App Service plan) blade, enable auto-scale with the following settings:</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/24.jpg"/>
<p>Scale out App service plan:</p>
	<p>•Auto-scale setting name: Codesizzler Autoscale</p>
	<p>•Resource group: for your choice</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/25.jpg"/>
<p>The Created scale condition:</p>
	<p>•Scale out: Scale based on a metric</p>
	<p>•Rules: Scale out</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/26.jpg"/>
	<p>•Time aggregation: Average</p>
	<p>•Metric name: Data In</p>
	<p>•Time grain statistics: Average</p>
	<p>•Operator: Greater than</p>
	<p>•Threshold: 1048576 bytes</p>
	<p>•Duration: 5 minutes</p>
	<p>•Cool down (minutes): 5</p>
	<p>•Instance limits (Minimum): 1</p>
	<p>•Instance limits (Maximum): 2</p>
	<p>•Instance limits (Default): 1</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/27.jpg"/>
<p>Add auto created scale condition:</p>
<p>Schedule: Repeat specific days</p>
	<p>•Repeat days:Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday</p>
	<p>•Time zone: (UTC-5:00) Eastern Time (US & Canada)</p>
	<p>•Start time: 00:00</p>
	<p>•End time: 23:59</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/28.jpg"/>
<p>Configure Content Delivery Network (CDN) for the Azure web app.</p>
	<p>•Azure-portal navigate to the Create a resource blade.</p>
	<p>•Create a resource.</p>
	<p>•Search the results to navigate to the CDN profile blade.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/29.jpg"/>
<p>Create a CDN profile with the following settings:</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/30.jpg"/>
	<p>•App Name: CodesizzlerCDN</p>
	<p>•Subscription: Azure pass</p>
	<p>•Resource group: CodesizzlerCDNrg</p>
	<p>•Location: Central US</p>
	<p>•Pricing tier: Standard Microsoft</p>
<p>Create a new CDN endpoint now</p>
	<p>•CDN endpoint name: Codesizzlercdn</p>
	<p>•Origin type: Web App</p>
	<p>•Origin hostname: codesizzlerofficial.azurewebsites.net</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/31.jpg"/>
<p>In the Azure portal, navigate to the CodesizzlerCDN</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/32.jpg"/>
<p>list of endpoints and use it to navigate to the new created endpoint.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/33.jpg"/>
<p>Note the value of the Endpoint hostname.</p>
<p>Open the tab of browse to the URL representing the Endpoint hostname.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/34.jpg"/>
<p>Note the Browser displays on Hello World.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-01/35.jpg"/>




























