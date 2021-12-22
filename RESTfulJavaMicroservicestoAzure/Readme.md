 # Deploy a Microservices based RESTful Java Application to Microsoft Azure #

Deploying a microservices based RESTful Java application to Microsoft Azure. The RESTful Java application used here is part of examples of project Helidon in github. Helidon is a lightweight microservices framework introduced by Oracle in September 2018. The application was initially built on Windows 10 PC and verified prior to deploying to Azure Kubernetes service.


**Given below are the prerequisites to implement this POC:**

•	Java SE Development Kit - 8 or higher

•	Maven - 3.5 or higher

•	 Azure cloud account, Azure CLI installed on Windows PC

•	Docker Desktop v 4.3.1

•	 Kubectl v1.20 or higher

•	 Minikube v1.24


1. Run the microservice based Java application locally. 

a. Execute and test the Java application locally on a Windows PC before containerizing.

 ![Alt text](https://github.com/Protontech-1803/devops/blob/master/RESTfulJavaMicroservicestoAzure/img/1a.png)


b. In a browser, go to http://localhost:8080/public/index.html. Verify the Employee app page as shown  below.

 ![Alt text](https://github.com/Protontech-1803/devops/blob/master/RESTfulJavaMicroservicestoAzure/img/1b.png)


2. Create Resource group for Azure Kubernetes service, Azure Container Registry from  Azure CLI in Windows Command prompt as given below.

Note: AKS and ACR created above should belong to same resource group.

    az login

    az group create --name <myResourceGroup> --location <region> 

    az acr create --resource-group <myResourceGroup> --name <acrName> --sku Basic 

    az aks create  --resource-group <myResourceGroup> --name <myAKSCluster> --node-count 2 --generate-ssh-keys  --attach-acr <acrName> 



3. On Windows PC, ensure login to Docker Desktop to a valid account. 

 ![Alt text](https://github.com/Protontech-1803/devops/blob/master/RESTfulJavaMicroservicestoAzure/img/3.png)


4. Open command prompt and start power shell and minikube.

 ![Alt text](https://github.com/Protontech-1803/devops/blob/master/RESTfulJavaMicroservicestoAzure/img/4.png)

  
5. Connect minikube to local docker environment.

       & minikube -p minikube docker-env | Invoke-Expression
      

6. Build the docker image to be deployed. 

       docker build -t employee-app . 
      

7. Kubectl is pointing to AKS cluster as shown in image given below.

 ![Alt text](https://github.com/Protontech-1803/devops/blob/master/RESTfulJavaMicroservicestoAzure/img/7.png)

8.  Push the docker image to Azure container registry using terminal commands.

        az acr login --name <registry name>
 

        # Tag the docker image
        docker tag <image name> <registry name>.azurecr.io/employee-app
        docker push <registry name>.azurecr.io/employee-app

9. Deploy the docker image to Azure Kubernetes cluster.

       az aks get-credentials 
      
Output:

      Merged "Cluster" as current context in /Users/.kube/config
      
command:
      
      # from employee-app directory
      kubectl create –f app.yaml 

Output:

    service/employee-app created

    deployment/employee-app created

    service/employee-helidon-lb created

  
10. Run the app from the AKS cluster and fetch the public IP to verify the Employee-app application as shown below.

 ![Alt text](https://github.com/Protontech-1803/devops/blob/master/RESTfulJavaMicroservicestoAzure/img/10.png)
  


