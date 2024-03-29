# Creating and Managing Webserver Instance Using Terraform OpenStack Provider
In this POC, terraform is used to create a Webserver instance on open stack, using open stack services.  To implement this POC, a Centos VM is used. Using Putty client connection is established to the Centos VM. 
1.	Install OpenStack using Packsack Installation using the below steps:

Step 1: Make the IP static and disable the selinux

                  $ sudo systemctl disable firewalld
                  $ sudo systemctl stop firewalld
                  $ sudo systemctl disable NetworkManager
                  $ sudo systemctl stop NetworkManager
                  $ sudo systemctl enable network
                  $ sudo systemctl start network	   

               # egrep --color 'vmx|svm' /proc/cpuinfo | wc –l

Step 2:   Update the VM
               
                # sudo yum update -y   

Step 3:   To create a repository 	   
	  
                 # yum install -y https://rdoproject.org/repos/rdo-release.rpm
        
                # yum install vim wget net-tools java -y

Step 4:  Once, you installed the rocky and enabled the repository update the VM
                
                 # sudo yum update -y	   

Step 5:    Now, Install the Packstack	   
	   
                 # sudo yum install -y openstack-packstack      	   

Step 6:   Generate OpenStack answer file for customized login details.
              
                   # packstack --gen-answer-file=/root/answer.txt

Step 7:   Edit the answer file.
            
    # vi /root/answer.txt	   

           # Skip the provision of Demo project
              CONFIG_PROVISION_DEMO=n 	

      # Change Admin Password - Used to Login to OpenStack Dashboard
                    CONFIG_KEYSTONE_ADMIN_PW=<password>

      # Map physical network bridge to the logical name. <Logical Name: Bridge Name>
                          CONFIG_NEUTRON_OVS_BRIDGE_MAPPINGS=extnet:br-ex

       # Create bridge for external connectivity. <Bridge Name: NW card name>
                           CONFIG_NEUTRON_OVS_BRIDGE_IFACES=br-ex:ens33 	
 
       
       extnet : Logical name for our external physical connection.
      br-ex : Bridge adapter
       eth0 or ens33 : Network Interface name        


Step 8:   Run the PackStack installer with the answer file we just modified according to our requirement.
           
           # packstack --answer-file=/root/answer.txt
         			 
Step 9: To access OpenStack Dashboard, open up a browser and visit URL https://<ipaddress>/dashboard, login with configured credentials.
	![Alt text](https://github.com/Protontech-1803/devops/blob/master/Creating%26ManagingWebserverInstance/img/1.1.png)
	
Step 10: On successful login, on navigation to overview page, the page lists the instances that are running, storage used, ram allocation, CPUs, security groups etc.
        ![Alt text](https://github.com/Protontech-1803/devops/blob/master/Creating%26ManagingWebserverInstance/img/1.2.png)	
2.	Install Terraform in the VM using below steps
	
Step 1: Get Unzip if not available on the VM using the command.  
	
     	  #    yum install wget unzip
	
Step 2: Update the System
	
           # yum update – y 
	
 Step 3: Download Terraform Package
	
	#wget https://releases.hashicorp.com/terraform/1.1.2/terraform_1.1.2_linux_amd64.z
	
 Step 4: Unzip Package
	
           #   unzip terraform_1.1.2_linux_amd64.zip -d /usr/local/bin/
	
Step 5: Check Terraform Version
	
           # terraform-v

3.	Create a file named main.tf file using an editor, with below script. The Script is used to create the webserver instance on execution in terraform.
	![Alt text](https://github.com/Protontech-1803/devops/blob/master/Creating%26ManagingWebserverInstance/img/1.3.png)
	
4.	Execute above main.tf Terraform Script using the commands init, plan and apply, shown below.
	
a.	Initialize Terraform with the command # terraform init 
	![Alt text](https://github.com/Protontech-1803/devops/blob/master/Creating%26ManagingWebserverInstance/img/1.4.a.png)
	
b.	Check that the changes proposed with the command # terraform plan
	![Alt text](https://github.com/Protontech-1803/devops/blob/master/Creating%26ManagingWebserverInstance/img/1.4.b.png)
	
c.	Create the instance by applying the script using the command # terraform apply
	![Alt text](https://github.com/Protontech-1803/devops/blob/master/Creating%26ManagingWebserverInstance/img/1.4.c.png)
	
5.	To Delete the instance created use the command # terraform destroy, as shown below.
	![Alt text](https://github.com/Protontech-1803/devops/blob/master/Creating%26ManagingWebserverInstance/img/1.5.png)
	
As illustrated, Terraform Openstack provider is used to manage the infrastructure for instances on openstack.
