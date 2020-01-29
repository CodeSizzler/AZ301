<h1>Creating Managed Server Applications in Azure</h1>

<h2>Introduction</h2>
<p>This article helps you to deploy a managed containerized workload to Azure. Also, you can learn to create a managed server application in Azure.</p>

<h2>Prerequisites</h2>
<p>To perform this demo user must have a valid Azure subscription and some basic knowledge on Azure containers, ARM template, Bash, Azure Kubernetes Services.</p>

<h2>Demo</h2>
<p>Log-in to Azure portal with your account using www.portal.azure.com. In Azure portal start a bash session. If this is the first time that you are going to use the Cloud Shell then you need to create a storage account.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/01.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/02.jpg"/>
<p>In the Bash panel run the following commands to create a resource group.</p>
	<p>RESOURCE_GROUP='Codesizzler-Rg'	</p>
	<p>LOCATION="CentralUS"	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/03.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/04.jpg"/>
<p>After creating the resource group using the above command run the following command to create a new AKS cluster.</p>
	<p>az aks create --resource-group $RESOURCE_GROUP --name codecluster --node-count 1 --node-vm-size Standard_DS1_v2 --generate-ssh-keys	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/05.jpg"/>
<p>Wait until the deployment gets complete. After the deployment gets completed run the following command to identify the credentials to access the AKS cluster.</p>
	<p>az aks get-credentials --resource-group $RESOURCE_GROUP --name codecluster	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/06.jpg"/>
<p>Run the following command to identify the connectivity of your AKS cluster. After running the command note that the output returns Ready.</p>
	<p>kubectl get nodes	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/07.jpg"/>
<p>Run the following command to nginx image from the Docker Hub.</p>
	<p>kubectl run codecluster --image=nginx --replicas=1 --port=80	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/08.jpg"/>
<p>Run the following command to verify that the Kubernetes pods has been created.</p>
	<p>kubectl get pods	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/09.jpg"/>
<p>To identify the deployment state run the following command.</p>
	<p>kubectl get deployment	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/10.jpg"/>
<p>Run the following command to make the pod available from the internet.</p>
	<p>kubectl expose deployment codecluster --port=80 --type=LoadBalancer	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/11.jpg"/>
<p>To identify the Public Ip address of your AKS Cluster run the following command and wait until the external Ip turns to Public Ip address.</p>
	<p>kubectl get service --watch	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/12.jpg"/>
<p>After finding the Public Ip address, copy the Ip address and browse for it.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/13.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/14.jpg"/>
<p>Note that the Ip address navigates you to the home page of nginx.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/15.jpg"/>
<p>Navigate back to the Azure portal and run the following command to scale your deployment.</p>
	<p>kubectl scale --replicas=2 deployment/codecluster	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/16.jpg"/>
<p>After scaling your deployment run the following command to verify the outcome of scaling deployment.</p>
	<p>kubectl get pods	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/17.jpg"/>
<p>To scale out the number of cluster nodes in the deployment.</p>
	<p>az aks scale --resource-group $RESOURCE_GROUP --name codecluster --node-count 2</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/18.jpg"/>
<p>Run the following command to scale out the number of cluster nodes and note that the instance has increased.</p>
	<p>kubectl get nodes	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/19.jpg"/>
<p>To scale the deployment run the following command in the bash panel.</p>
	<p>kubectl scale --replicas=10 deployment/codecluster	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/20.jpg"/>
<p>After scaling the deployment run the following command to scale the deployment and note the number of pods has increased.</p>
	<p>kubectl get pods	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/21.jpg"/>
<p>To review the cluster node distribution run the following command and note that the clusters are distributed across both nodes.</p>
	<p>kubectl get pod -o=custom-columns=NODE:.spec.nodeName,POD:.metadata.name	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/22.jpg"/>
<p>Run the following command to delete the deployment.</p>
	<p>kubectl delete deployment codecluster	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/23.jpg"/>
<p>Download the sample containerized application by running the following command.</p>
	<p>git clone https://github.com/Azure-Samples/azure-voting-app-redis.git	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/24.jpg"/>
<p>Change the directory to the downloaded voting app by the running the following command.</p>
	<p>cd azure-voting-app-redis	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/25.jpg"/>
<p>List the content of the downloaded application .yaml file run the following command and note the output.</p>
	<p>cat azure-vote-all-in-one-redis.yaml	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/26.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/27.jpg"/>
<p>To deploy the application based on .yaml run the following command.</p>
	<p>kubectl apply -f azure-vote-all-in-one-redis.yaml	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/28.jpg"/>
<p>Run the following command to verify the Kubernetes pods.</p>
	<p>kubectl get pods	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/29.jpg"/>
<p>By running the following command, you can identify the Public Ip address for the containerized application.</p>
	<p>kubectl get service azure-vote-front --watch	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/30.jpg"/>
<p>Copy the Public Ip address and browse for it. Note that this time you can able to see the voting app.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/31.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/32.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/33.jpg"/>
<p>Navigate back to Azure portal and run the following command in the bash panel to download a sample containerized application.</p>
	<p>git clone https://github.com/kubernetes-incubator/metrics-server.git	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/34.jpg"/>
<p>To install metrices server run the following command.</p>
	<p>kubectl create -f ~/metrics-server/deploy/1.8+/	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/35.jpg"/>
<p>In the bash session run the following command to configure auto-scaling for the voting application.</p>
	<p>kubectl autoscale deployment azure-vote-front --cpu-percent=50 --min=3 --max=10	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/36.jpg"/>
<p>To identify the status of autoscaling run the following command.</p>
	<p>kubectl get hpa	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/37.jpg"/>
<p>Run the following command in the bash session to view the pods of voting application.</p>
	<p>kubectl get pods	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/38.jpg"/>
<p>To delete the deployment run the following commands.</p>
	<p>kubectl delete deployment azure-vote-front	</p>
	<p>kubectl delete deployment azure-vote-back	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/39.jpg"/>
<p>Run the following command to identify that the previous commands were completed successfully.</p>
	<p>kubectl get pods	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/40.jpg"/>
<p>Run the following command to delete the created AKS cluster.</p>
	<p>az aks delete --resource-group Codesizzler-Rg --name codecluster --yes --no-wait	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/41.jpg"/>
<p>Generate the pair of SSH key which is used to access the Linux VM running the Jenkins instance and Grafana console by running the following command.</p>
	<p>ssh-keygen -t rsa -b 2048	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/42.jpg"/>
<p>To create a variable which value designates the public key of the newly generated key pair run the following command.</p>
	<p>PUBLIC_KEY=$(cat ~/.ssh/id_rsa.pub)	</p>
	<p>PUBLIC_KEY_REGEX="$(echo $PUBLIC_KEY | sed -e 's/\\/\\\\/g; s/\//\\\//g; s/&/\\\&/g')"	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/43.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/44.jpg"/>
<p>Run the following command to designate the name of your new resource group.</p>
	<p>RESOURCE_GROUP='Code_sizzler-Rg'	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/45.jpg"/>
<p>To designate location of your resource group run the following command.</p>
	<p>LOCATION=$(az group list --query "[?name == 'Code_sizzler-Rg'].location" --output tsv)	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/46.jpg"/>
<p>To create a new resource group run the following command and to create a service principal for the newly created resource group.</p>
	<p>az group create --name $RESOURCE_GROUP --location $LOCATION	</p>
	<p>SERVICE_PRINCIPAL=$(az ad sp create-for-rbac --name Code_sizzler-Rg-SP)	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/47.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/48.jpg"/>
<p>To retrieve the application ID of the newly created service principal run the following command.</p>
	<p>APP_ID=$(echo $SERVICE_PRINCIPAL | jq .appId | tr -d '"')	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/49.jpg"/>
<p>Identify the password for the newly created service principal by running the following command.</p>
	<p>PASSWORD=$(echo $SERVICE_PRINCIPAL | jq .password | tr -d '"')	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/50.jpg"/>
<p>To create a parameter file for the deployment using the VI interface run the following command.</p>
	<p>vi ~/parameters.json	</p>
<p>After opening the VI interface type a and press the enter key to enter the VI interface. Then paste the parameter file and type wq! to save the parameter file in the Vi interface.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/51.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/52.jpg"/>
<p>Exit the VI interface and run the following command to replace the application Id, password and SSH public key with the parameter file.</p>
	<p>sed -i.bak1 's/"$APP_ID"/"'"$APP_ID"'"/' ~/parameters.json	</p>

	<p>sed -i.bak2 's/"$PASSWORD"/"'"$PASSWORD"'"/' ~/parameters.json	</p>

	<p>sed -i.bak3 's/"$PUBLIC_KEY_REGEX"/"'"$PUBLIC_KEY_REGEX"'"/' ~/parameters.json	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/53.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/54.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/55.jpg"/>
<p>To verify that the replacements were made successfully run the following command.</p>
	<p>cat ~/parameters.json	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az301-05/56.jpg"/>
<p>After getting the parameters run the following command to deploy a sample solution using Azure Resource Manager template in the GitHub repository.</p>
	<p>az group deployment create --resource-group $RESOURCE_GROUP --template-uri https://raw.githubusercontent.com/cjpluta/AZ-301-MicrosoftAzureArchitectDesign/master/allfiles/AZ-301T03/Module_02/LabFiles/Starter/azuredeploy.json --parameters @parameters.json	</p>
<p>Wait until the deployment gets complete. After the deployment gets completed navigate to the created resource group and monitor the deployment.</p>































