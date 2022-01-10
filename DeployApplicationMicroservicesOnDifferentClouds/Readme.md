# Deploy Application with Database and Frontend Microservices on different Clouds

A web application with frontend written in Python language and deployed in a Microsoft Azure container uses Redis database from Amazon web services (AWS) container.

1. Verify sample web application deployed using Docker containers works locally.

   ![Alt text](https://github.com/Protontech-1803/devops/blob/master/DeployApplicationMicroservicesOnDifferentClouds/img/1.png)
   
2. Push the Redis database to AWS.

a. Create a public Elastic Container Registry (ECR) in AWS account. 

   ![Alt text](https://github.com/Protontech-1803/devops/blob/master/DeployApplicationMicroservicesOnDifferentClouds/img/2.%20a.png)
 
b. Tag Redis’ local docker image with the URI of the AWS Elastic container registry before pushing with AWS CLI.

      aws ecr-public get-login-password --region region | docker login --username AWS --password-stdin public.ecr.aws/<ecrname>
      docker build -t avote .
      docker tag avote:latest public.ecr.aws/<ecrname>/avote:latest
      docker push public.ecr.aws/<ecrname>/avote:latest


3. Push the frontend code to Azure and deploy app in Azure Kubernetes service.

a. Create a resource group for Azure Kubernetes service, Azure Container Registry from  Azure CLI in Windows Command prompt.

**Note:** AKS and ACR created above should belong to same resource group.

b. Verify the **.yaml** file shows container images on different clouds before deployment.


      apiVersion: apps/v1
      kind: Deployment
      …...
            - name: azure-vote-back
              image: public.ecr.aws/<ecrname>/avote:latest
      …..

      apiVersion: v1
      kind: Service
      metadata:
        name: azure-vote-back
      …….
      ---
      apiVersion: apps/v1
      kind: Deployment
      metadata:
        name: azure-vote-front
      …….
              image: avote.azurecr.io/azure-vote-front:v1
      …….
      ---
      apiVersion: v1
      kind: Service
      metadata:
        name: azure-vote-front
      ……

4. Notice that only the IP address changes after deployment with microservices from different clouds.

    ![Alt text](https://github.com/Protontech-1803/devops/blob/master/DeployApplicationMicroservicesOnDifferentClouds/img/4.png)


