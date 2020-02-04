<h1>Create a Service Bus namespace using the Azure portal</h1>

<h2>Introduction</h2>
<p>In this article you are going to learn about how to deploy a Service Bus name space using Azure portal.</p>

<h2>Pre-requisites</h2>
<p>To perforrm this demo, you must have valid Azure subscription and some basic knowledge on Azure Service Bus.</p>

<h2>Demo</h2>
<p>Log-in with Azure portal with your account using www.portal.azure.com. In Azure portal click on Create a new resource>Service bus.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-09/01.jpg"/>
<p>Create a service bus with the configuration and on create the namespace blade, perform the following:</p>
	<p>•Name: codesizzlerservicebus</p>
	<p>•Pricing tier: basic</p>
	<p>•Subscription: Azure Pass-Sponsorship</p>
	<p>•Resource group: codesizzler11</p>
	<p>•Location: West Us</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-09/02.jpg"/>
<p>Finally Click on create button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-09/03.jpg"/>
<p>Confirm that the service bus namespace is deployed successfully. To see the notifications, select the bell icon (Alerts) on the toolbar.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-09/04.jpg"/>
<p>Navigate on the created resource and select your service bus namespace.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-09/05.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-09/06.jpg"/>
<p>Monitor the overview panel of your service bus namespace.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-09/07.jpg"/>

<h2>Get the connection string</h2>
<p>Creating a new namespace automatically Shared Access Signature (SAS) rule with an associated. And click on the service bus   of the namespace.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-09/08.jpg"/>
<p>In the namespace window, click on the Shared access policies and navigate the Shared access policies screen, click Root Manage Shared Access Key.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-09/09.jpg"/>
<p>In the Root Manage shared Access key configuration of following setting:</p>
	<p>•Click on manage key</p>
	<p>•Leave at another two keys</p>
	<p>•Copy on the Primary key and Secondary Key for later used.</p>
<p>Finally Click on Save Button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-09/10.jpg"/>














