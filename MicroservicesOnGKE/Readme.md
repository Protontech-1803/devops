# Microservices Implementation on GKE #

This POC, show how to implement a simple Microservices based application on GKE. Here a Monolith application is split into three microservices. These microservices are built based on docker image and deployed on GKE, and made available as services a Kubernetes service type Load Balancer.

To Start, with a monolithic application deployed on the GKE, which implements services such as UI, products and orders. The following are the brief steps to implement the same.

1.Login into GCP Console.

   a. Create a New Project. And Active the Cloud shell from the Cloud Console.

   b. Set the project and default zone, using the below commands.

		gcloud config set project <PROJECT_ID>
		gcloud config set compute/zone us-central-f
      
   c. Clone the source from git repository. Change to the directory and install the dependencies needed to run the application locally.
   
   ![Alt text](https://github.com/Protontech-1803/devops/blob/master/terrasible/output2.png)
 
 2. Create a Google Kubernetes Engine (GKE) cluster.

   a.Before creating a cluster, make sure the proper API's are enabled.  

   b.Verify the Kubernetes cluster is created and related information is displayed in Google Cloud console.

3. Deploy a monolith application to GKE cluster. 

4. Verify the Deployment of monolith application. Find the external IP address for the monolith application. Copy the IP address. Point the browser to this URL (such as http:// IP address) to check if the monolith is accessible.
 

**The Following are steps to break the monolith application into Microservices.**

1. Migrate Orders to Microservice.

a. Create New Orders Microservice. The first service breaks out is the Orders service and create a separate Docker container for this service. 

b. Create Docker Container with Google Cloud Build.

i. Create a Docker container of Order service using Google Cloud Build.

ii. Google Cloud Build will compress the files from the directory and move them to a Google Cloud Storage bucket.

iii. Build the Docker container and push it to the Google Container Registry, Run the following commands.

 
c. Deploy Containers to GKE.

i. To deploy and manage applications on a GKE cluster, you must communicate with the Kubernetes cluster management system.

ii. The Deployment will be running only one Pod of the application. Run the following command to deploy the application.
 

d. Expose GKE Container.

i. A Service provides networking and IP support to the application's Pods.

ii. GKE creates an external IP and a Load Balancer for the application.

iii. Find out the external IP that GKE provisioned for the application. Run the following command to expose the website to the Internet.

 

e. Reconfigure Monolith.

i. Update our config file in our monolith to point to the new Orders microservices IP address.

ii. Editor to replace the local URL with the IP address of our new Orders microservice. Run the following command to edit.
 
 

f. Create Docker Container with Google Cloud Build. Run the following commands to create a docker container with google
 
 
	
g. Deploy Container to GKE as shown below.
 

h. Verify the application is now hitting the new Orders microservice by going to the monolith application in the browser and navigating to the Orders page.

 

2. Migrate Products to microservice.
a. Create New products Microservice.
i. Run the following commands to build a Docker container
 
 

b. Deploy Container to GKE. Run the following command to deploy container to GKE
 

c. Expose GKE Container. Run the following command to Expose GKE Container.
 

d. Reconfigure Monolith.

i. The nano editor to replace the local URL with the IP address of our new Products microservices.

ii. Run the following command to edit.
 
	       
e. Create Docker Container with Google Cloud Build.
 

f. Deploy Container to GKE. Verify the application is now hitting the new Orders microservice by going to the monolith application in the browser and navigating to the products page.


3. Migrate Frontend to Microservice.

a. Create new Frontend Microservice.

i. The same config for our Frontend microservice.

ii. Run the following commands to copy our microservices URL config files to the Frontend microservice codebase.
 

b. Create Docker Container with Google Cloud Build.

i. Run the following commands to Create a Docker Container.


4. Deploy Container to GKE.
 

5. Expose Google Kubernetes Engine
 

6. Find the External IP address. 
 
7. Copy the IP address. Point the browser to this URL (such as http:// IP address) to check if you are accessible.
   


