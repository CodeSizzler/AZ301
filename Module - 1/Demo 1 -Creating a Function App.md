<h1>Creating a Function App</h1>

<p>1.Sign in to the Azure portal using https://portal.azure.com.</p>
<p>2.Select Create new resource>Compute > Function App on the top left of the screen and enter the details required.For resource group select create new and create a new resource group. Then click on the Create option.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-06/01.jpg"/>
<p>3.After the completion of your deployment go to the resource page and open your resource.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-06/02.jpg"/>
<p>4.Select + button next to Functions, choose In-portal, and select Continue.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-06/03.jpg"/>
<p>5.Choose WebHook + API and then select Create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-06/04.jpg"/>

<h2>Testing the function:</h2>
<p>1.Click on the HttpTrigger1 of your resource.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-06/05.jpg"/>
<p>2.Then select </>Get function URL and copy the URL.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-06/06.jpg"/>
<p>3.Paste the function URL into your browser's address bar. Add the below query string value to the end of this URL and press the enter key.</p>
	<p>name=yourname	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-06/07.jpg"/>
<p>4.To view the trace output from the previous execution, return to your function in the portal and click the arrow at the bottom of the screen to expand the Logs.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-06/08.jpg"/>








