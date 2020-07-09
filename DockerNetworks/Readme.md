# Communication Between Docker Containers in Different Networks


This POC, illustrates an example where Containers running in different Docker networks are able to communicate with each other by adding the **Iptables Rules** to DOCKER-USER chain.

**The following are the steps followed in the example:**
 
1.	Create a Docker networks in a Linux Instance.

       docker network create --driver bridge <Network_Name>
   ![Alt text](https://github.com/Protontech-1803/devops/blob/master/terrasible/output2.png)
       
       
2.	Create the containers and connect to the Docker network.

       docker run -d --name <Container_Name> <Image_Name>
       

       docker network connect <Network_Name> <Container_Name>
       



3.	List the Containers created.

       docker ps



4. Get the IP address of Docker containers by running the below command.

       docker inspect <Container_ID> | grep "IPAddress"


5. Verify the connectivity between the containers by running the command **ping <container_ipaddress>** in the container. The Container will not be able to ping the other container.

       docker exec -it <Container1_ID> /bin/bash

       ping <Container2_IPAddress>


6.	Set the IPtables rules to allow the connectivity between containers in different network.

    a)	Compare the Gateway of network with Bridge interface.
    
       docker inspect <Network_Name>
    
    b) Run the command ifconfig to get the bridge interface names of the network created.  
    **Note: Compare the gateway of network created to get the bridge Interface.**
    
       ifconfig
    

    c)	Set the Iptables rules for containers with bridge interface.
   
       iptables -I DOCKER-USER -i <Bridge_Interface_Name_Network1> -o <Bridge_Interface_Name_Network2> -s <Container1_IPAddress> -d <Container2_IPAddress> -j ACCEPT
    
    
 
5. Verify the communication between the containers in different network. Now Container will be able to ping the other container.

       docker exec -it <Container1_ID> /bin/bash

       ping <Container2_IPAddress>



The