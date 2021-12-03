  # Setting Up Grafana Dashboard with CloudWatch in AWS Cloud #
  
Grafana dashboard is used for continuous monitoring the access to AWS lambda functions and Amazon EC2 by considering AWS CloudWatch. AWS Cloud Watch Logs the data, and provides features to query, visualize logs, view and trace metrics in Grafana dashboard.

**This POC, shows Steps for creating Grafana Dashboard with CloudWatch for Continues Monitoring on AWS**

1.	Login into AWS Console Account. 

a.	Navigate to Amazon Managed Grafana home page and Create a Workspace as shown below.

    ![Alt text](https://github.com/Protontech-1803/devops/blob/master/GrafanaDashboardAWSCloud/img/1a.png)
 
b.	Workspace name and description is provided for workspace details.

    ![Alt text](https://github.com/Protontech-1803/devops/blob/master/GrafanaDashboardAWSCloud/img/1b.png)
    
 
c.	In Configuration setting page, enable the AWS Single Sign-On (AWS SSO) and Permission type as Service managed as shown below.

    ![Alt text](https://github.com/Protontech-1803/devops/blob/master/GrafanaDashboardAWSCloud/img/1c.png)
    
 
d.	In Service managed permission settings, select Current account and provide Data sources and notification channels.

    ![Alt text](https://github.com/Protontech-1803/devops/blob/master/GrafanaDashboardAWSCloud/img/1d.png)
 
 
e.	Review the details to create the Grafana workspace in AWS.

    ![Alt text](https://github.com/Protontech-1803/devops/blob/master/GrafanaDashboardAWSCloud/img/1ei.png)
    
    ![Alt text](https://github.com/Protontech-1803/devops/blob/master/GrafanaDashboardAWSCloud/img/1eii.png)
 
 

2.	In AWS Single Sign-On page create user group.

a.	Select Add user and provide user details as shown below.  
    
    ![Alt text](https://github.com/Protontech-1803/devops/blob/master/GrafanaDashboardAWSCloud/img/2a.png)
    
 
b.	Add user to groups, create groups and provide Group name and Description then create.

   ![Alt text](https://github.com/Protontech-1803/devops/blob/master/GrafanaDashboardAWSCloud/img/2b.png)
 

3.	In Grafana workspace, configure groups to add users and make admin users. 

    ![Alt text](https://github.com/Protontech-1803/devops/blob/master/GrafanaDashboardAWSCloud/img/3ai.png)
    
    
    ![Alt text](https://github.com/Protontech-1803/devops/blob/master/GrafanaDashboardAWSCloud/img/3aii.png)
 
 

4.	Verify the user is added, and copy required credentials with the URL as shown below.

    ![Alt text](https://github.com/Protontech-1803/devops/blob/master/GrafanaDashboardAWSCloud/img/4.png)
 


5.	On successful login into AWS Grafana dashboard.

a.	It provides the Grafana dashboard with General Home page as shown below.

    ![Alt text](https://github.com/Protontech-1803/devops/blob/master/GrafanaDashboardAWSCloud/img/5a.png)

 
b.	Select AWS icon to select the Data sources and provide the Service as CloudWatch. Navigate to Setting as shown below. 

    ![Alt text](https://github.com/Protontech-1803/devops/blob/master/GrafanaDashboardAWSCloud/img/5b.png)

 
c.	In settings pages, navigate to dashboards to select import for Amazon EC2, AWS Lambda and Amazon CloudWatch Logs.

    ![Alt text](https://github.com/Protontech-1803/devops/blob/master/GrafanaDashboardAWSCloud/img/5c.png)

 
d.	Navigate to Amazon EC2 dashboard and select the respective region for instance to monitor. The image shows how the instances can be monitored through the Grafana dashboard.

    ![Alt text](https://github.com/Protontech-1803/devops/blob/master/GrafanaDashboardAWSCloud/img/5d.png)


e.	Monitor the AWS lambda, lambda function using Grafana dashboard.

    ![Alt text](https://github.com/Protontech-1803/devops/blob/master/GrafanaDashboardAWSCloud/img/5e.png)

 

