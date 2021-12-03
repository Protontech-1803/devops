  # Setting Up Grafana Dashboard with CloudWatch in AWS Cloud #
  
Grafana dashboard is used for continuous monitoring the access to AWS lambda functions and Amazon EC2 by considering AWS CloudWatch. AWS Cloud Watch Logs the data, and provides features to query, visualize logs, view and trace metrics in Grafana dashboard.

**This POC, shows Steps for creating Grafana Dashboard with CloudWatch for Continues Monitoring on AWS**

1.	Login into AWS Console Account. 
a.	Navigate to Amazon Managed Grafana home page and Create a Workspace as shown below.
 
b.	Workspace name and description is provided for workspace details.
 
c.	In Configuration setting page, enable the AWS Single Sign-On (AWS SSO) and    Permission type as Service managed as shown below.
 
d.	In Service managed permission settings, select Current account and provide Data sources and notification channels.
 
 
e.	Review the details to create the Grafana workspace in AWS.
 
 

2.	In AWS Single Sign-On page create user group.
a.	Select Add user and provide user details as shown below.  
 
b.	Add user to groups, create groups and provide Group name and Description then create.
 

3.	In Grafana workspace, configure groups to add users and make admin users. 
 
 

4.	Verify the user is added, and copy required credentials with the URL as shown below.
 


5.	On successful login into AWS Grafana dashboard.
a.	It provides the Grafana dashboard with General Home page as shown below.
 
b.	Select AWS icon to select the Data sources and provide the Service as CloudWatch. Navigate to Setting as shown below.
 
c.	In settings pages, navigate to dashboards to select import for Amazon EC2, AWS Lambda and Amazon CloudWatch Logs.
 
d.	Navigate to Amazon EC2 dashboard and select the respective region for instance to monitor. The image shows how the instances can be monitored through the Grafana dashboard.

 

e.	Monitor the AWS lambda, lambda function using Grafana dashboard.
 

