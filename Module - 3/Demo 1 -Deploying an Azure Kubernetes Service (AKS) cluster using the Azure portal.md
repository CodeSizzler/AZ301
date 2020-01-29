<h1>Deploying an Azure Kubernetes Service (AKS) cluster using the Azure portal</h1>

<h2>Introduction</h2>
<p>In this article you are going to learn about how to deploy and manage an Azure Kubernetes Cluster.</p>

<h2>Prerequisites</h2>
<p>To perform this demo user must have valid Azure subscription and some knowledge on Azure Kubernetes, Bash, Containers and Clusters.</p>

<h2>Demo</h2>
<p>Log-in with your Azure account in Azure portal using www.portal.azure.com. In Azure portal click on Create a new resource and search for Kubernetes Services.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/01.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/02.jpg"/>
<p>Create a Kubernetes Service with following settings:</p>
	<p>•Cluster name: codesizzleraks</p>
	<p>Subscription: Select a valid subscription</p>
	<p>•Region: Select a valid location</p>
	<p>•Resource group: Create a new resource group codesizzleraks-rg</p>
	<p>•Kubernetes version: Default</p>
	<p>•DNS name prefix: codesizzleraks-dns</p>
	<p>•Node size: Default</p>
	<p>•Node count: 1</p>
<p>After setting the basic configurations click on Authentication</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/03.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/04.jpg"/>
<p>In the authentication panel configure the following settings and click on Networking.</p>
	<p>•Service principal: Create a new service principal default service principal</p>
	<p>•Enable RBAC:  Yes</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/05.jpg"/>
<p>In the Networking panel configure the following settings and click on Monitoring.</p>
	<p>•HTTP application routing: No</p>
	<p>•Networking configuration: Basic</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/06.jpg"/>
<p>In the Monitoring panel configure the following settings and click on Tag.</p>
	<p>•Enable container monitoring: Yes</p>
	<p>•Log analytics workspace: Create a new one</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/07.jpg"/>
<p>Navigate to the tag panel and click on Review+Create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/08.jpg"/>
<p>Once your validation gets paused click on create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/09.jpg"/>
<p>After the deployment completes navigate to the created kubernetes service and review the settings.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/10.jpg"/>
<p>In Azure portal start a Bash session in PowerShell and run the following command to connect with the Kubernetes.</p>
	<p>az aks get-credentials --resource-group codesizzleraks-rg --name codesizzleraks	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/11.jpg"/>
<p>Run the following command to verify the connection of your Kubernetes cluster.</p>
	<p>kubectl get nodes	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/12.jpg"/>
<p>Create a yaml file by running the command.</p>
	<p>Vi azure-vote.yaml	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/13.jpg"/>
<p>Run the following script in Bash.</p>
	<p>apiVersion: apps/v1	</p>
	<p>kind: Deployment	</p>
	<p>metadata:	</p>
	  <P>name: azure-vote-back	</p>
	<p>spec:	</p>
	  <p>replicas: 1	</p>
	  <p>selector:	</p>
	    <p>matchLabels:	</p>
	      <p>app: azure-vote-back	</p>
	  <p>template:	</p>
	    <p>metadata:	</p>
	      <p>labels:	</p>
	        <p>app: azure-vote-back	</p>
	    <p>spec:	</p>
	      <p>nodeSelector:	</p>
	        <p>"beta.kubernetes.io/os": linux	</p>
	      <p>containers:	</p>
	      <p>- name: azure-vote-back	</p>
	        <p>image: redis	</p>
	        <p>resources:	</p>
	          <p>requests:	</p>
	            <p>cpu: 100m	</p>
	            <p>memory: 128Mi	</p>
	          <p>limits:	</p>
	            <p>cpu: 250m	</p>
	            <p>memory: 256Mi	</p>
	        <p>ports:	</p>
	        <p>- containerPort: 6379	</p>
	          <p>name: redis	</p>
		<p>---	</p>
		<p>apiVersion: v1	</p>
		<p>kind: Service	</p>
		<p>metadata:	</p>
	  	<p>name: azure-vote-back	</p>
		<p>spec:	</p>
	  	<p>ports:	</p>
	  <p>- port: 6379	</p>
	  <p>selector:	</p>
	    	<p>app: azure-vote-back	</p>
	<p>---	</p>
	<p>apiVersion: apps/v1	</p>
	<p>kind: Deployment	</p>
	<p>metadata:	</p>
	  <p>name: azure-vote-front	</p>
	<p>spec:	</p>
	  <p>replicas: 1	</p>
	  <p>selector:	</p>
	    <p>matchLabels:	</p>
	      <p>app: azure-vote-front	</p>
	  <p>template:	</p>
	    <p>metadata:	</p>
	      <p>labels:	</p>
	        <p>app: azure-vote-front	</p>
	    <p>spec:
	      <p>nodeSelector:	</p>
	        <p>"beta.kubernetes.io/os": linux	</p>
	      <p>containers:	</p>
	      <p>- name: azure-vote-front	</p>
	        <p>image: microsoft/azure-vote-front:v1	</p>
	        <p>resources:	</p>
	          <p>requests:	</p>
	            <p>cpu: 100m	</p>
	            <p>memory: 128Mi	</p>
	          <p>limits:	</p>
	            <p>cpu: 250m	</p>
	            <p>memory: 256Mi	</p>
	        <p>ports:	</p>
	        <p>- containerPort: 80	</p>
	        <p>env:	</p>
	        <p>- name: REDIS	</p>
	          <p>value: "azure-vote-back"	</p>
	<p>---	</p>
	<p>apiVersion: v1	</p>
	<p>kind: Service	</p>
	<p>metadata:	</p>
	  <p>name: azure-vote-front	</p>
	<p>spec:	</p>
	  <p>type: LoadBalancer	</p>
	  <p>ports:	</p>
	  <p>- port: 80	</p>
	  <p>selector:	</p>
	    <p>app: azure-vote-front	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/14.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/15.jpg"/>
<p>Deploy the application by running the command.</p>
	<p>kubectl apply -f azure-vote.yaml	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/16.jpg"/>
<p>After running the command note the output.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/17.jpg"/>
<p>By running the below command monitor the Kubernetes.</p>
	<p>kubectl get service azure-vote-front --watch	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/18.jpg"/>
<p>After running the command note the output.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/19.jpg"/>
<p>Note the External IP. Open the browser and browse with the external IP. It will display the Azure Voting App.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/20.jpg"/>
<p>In Azure portal navigate to the codesizzleraks and display the Insights panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/21.jpg"/>
<p>In the insights panel click on Add filter and <All but kube-system>.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/22.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/23.jpg"/>
<p>After applying the filter navigate to the Containers panel and monitor the health status of the containers.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/24.jpg"/>
<p>In the container panel click on View container logs.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/25.jpg"/>
<p>In the container logs panel monitor the container logs.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/26.jpg"/>
<p>After monitoring the container logs delete the resources by running the following command.</p>
	<p>az aks delete --resource-group codesizzleraks-rg --name codesizzleraks --no-wait	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/27.jpg"/>
<p>When it prompts confirm it by typing Y.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/28.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-04/29.jpg"/>






