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
