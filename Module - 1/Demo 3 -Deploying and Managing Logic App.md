<h1>Deploying and Managing Logic App</h1>

<h2>Introduction</h2>
<p>In this article you are going to learn about how to deploy and manage Logic App using Azure portal.</p>

<h2>Pre-requisites</h2>
<p>To perform this demo, you must have valid Azure subscription and some basic knowledge on Azure Logic App.</p>

<h2>Demo</h2>
<h2>Creating logic app:</h2>
<p>1.Sing in to your Azure Portal by using https://portal.azure.com/</p>
<p>2.Select Create a resource > Integration > Logic App on the top left of the screen.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-02/01.jpg"/>
<p>3.After getting in to the creating menu enter the details required. For resource create a new one and select the region. Then click on create option.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-02/02.jpg"/>
<p>4.After the Logic app deploys select the logic app designer on the overview page. In the designer page select Blank Logic app.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-02/03.jpg"/>

<h2>Check RSS feed with a trigger:</h2>
<p>1.Open the designer tool box and search for rss in the search box.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-02/04.jpg"/>
<p>2.Enter the details required. For Rss feed URL enter the below one and click on New Step.</p>
	<p>http://feeds.reuters.com/reuters/topNews	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-02/05.jpg"/>

<h2>Sending an email with action:</h2>
<p>1.Under Choose an action, enter "send an email" in the search box. Under the search box, choose All. From the actions list, select the "send an email" action for the email provider that you want.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-02/06.jpg"/>
<p>2.Enter the subject and body to the mail and click on New Step.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-02/07.jpg"/>

<h2>Run your Logic App:</h2>
<p>To manually start your logic app, on the designer toolbar bar, choose Run.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-02/08.jpg"/>
