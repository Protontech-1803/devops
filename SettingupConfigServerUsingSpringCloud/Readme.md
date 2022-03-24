# Setting up Config server using Spring Cloud #
Spring Cloud Config is Spring's client/server approach for storing and serving distributed configurations across multiple applications and environments. This configuration store is ideally versioned under git version control and can be modified during application runtime. Importantly, SpringCloudConfigServer stores configuration for multiple services. It can also store configuration for each of the services for different environments.
**The steps to set up config server using spring cloud are as follows**
1.	Create a cloudconfigserver component for config server.

    a. Create a spring project and add the dependency.

   ![Alt text](https://github.com/Protontech-1803/devops/blob/master/SettingupConfigServerUsingSpringCloud/img/1.a.png)

   b. Add the Eureka Client annotation in the main class of order-service.
   
 
   ![Alt text](https://github.com/Protontech-1803/devops/blob/master/SettingupConfigServerUsingSpringCloud/img/1.b.png)
   
i. In the CloudConfigServer.java main class, add the given annotation as shown below.

           -@EnableEurekaClient.
           -@EnableEurekaClient.  
    
   ![Alt text](https://github.com/Protontech-1803/devops/blob/master/SettingupConfigServerUsingSpringCloud/img/1.b.i.png)
   
 
 c.	To create YAML file in the resource folder, navigate to resources, select New and click File and add the following code.
    
    spring:
      application:
        name:Config-Server
    server:
        port: 9196
        
   ![Alt text](https://github.com/Protontech-1803/devops/blob/master/SettingupConfigServerUsingSpringCloud/img/1.c.png)
 
  i. Copy the configuration code given below and paste it in application.yml as shown below.
      
      eureka:
         client:
          register-with-eureka:true
          fetch-registry:true
          service-url:
           defaultZone:http://localhost:8761/eureka/
        instance:
          hostname: localhost
          
   ![Alt text](https://github.com/Protontech-1803/devops/blob/master/SettingupConfigServerUsingSpringCloud/img/1.c.i.png) 

  d.	Configure git in application.yml file.
  
  i. Copy the configuration code given below and paste it in application.yml as shown below.
    
     cloud:
      config:
       server:
        git:
         uri:
            
   ![Alt text](https://github.com/Protontech-1803/devops/blob/master/SettingupConfigServerUsingSpringCloud/img/1.d.i.png)
 
  ii. Open Github and copy the git url as shown below.
 
   ![Alt text](https://github.com/Protontech-1803/devops/blob/master/SettingupConfigServerUsingSpringCloud/img/1.d.ii.png)
      
  iii. Open application.yml file and paste the url as shown below.

   ![Alt text](https://github.com/Protontech-1803/devops/blob/master/SettingupConfigServerUsingSpringCloud/img/1.d.iii.png)



