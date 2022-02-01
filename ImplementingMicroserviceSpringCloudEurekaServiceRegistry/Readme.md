#Implementing Microservices in Spring Cloud Eureka Service Registry#
To register a microservice in spring cloud eureka service registry, create a service registry component for eureka server and annotate in main class. Further, create two microservices: For example, *order_service* and *payment_service*. In microservices, configure the packages and add eureka client annotation to register to eureka server and configure application.yml file to get output in the browser. Eureka Server is an application where microservices can register themselves so others can discover them. Each microservice registers into Eureka server and eureka server knows all client applications running on each port and IP address.
The steps to register Microservice with Eureka Server are as follows: 
1. Create service registry component for eureka server in Intellij idea.  


a.	Create a spring project and add the dependency.
 ![Alt text](https://github.com/Protontech-1803/devops/blob/master/ImplementingMicroserviceSpringCloudEurekaServiceRegistry/img/1a.png)
b.Add the eureka server annotation in main class.
 ![Alt text](https://github.com/Protontech-1803/devops/blob/master/ImplementingMicroserviceSpringCloudEurekaServiceRegistry/img/1b.png)
c.Create and configure application.yml file.
  ![Alt text](https://github.com/Protontech-1803/devops/blob/master/ImplementingMicroserviceSpringCloudEurekaServiceRegistry/img/1c.png)            
2.	Create *order_service* Microservice in *Intellij IDEA*.
a.	Create spring project for order_service and add the dependencies. 
 ![Alt text](https://github.com/Protontech-1803/devops/blob/master/ImplementingMicroserviceSpringCloudEurekaServiceRegistry/img/2a.png)
b.	Create Order class in *entity* package and configure the code.
  ![Alt text](https://github.com/Protontech-1803/devops/blob/master/ImplementingMicroserviceSpringCloudEurekaServiceRegistry/img/2b.png)
c.	Create *OrderService* class in *service* package and configure the code.
 ![Alt text](https://github.com/Protontech-1803/devops/blob/master/ImplementingMicroserviceSpringCloudEurekaServiceRegistry/img/2c.png)
d.	Create *OrderController* class in *controller* package and configure the code.
 ![Alt text](https://github.com/Protontech-1803/devops/blob/master/ImplementingMicroserviceSpringCloudEurekaServiceRegistry/img/2d.png)
e.	Create interface in *repository* package and extend to *JpaRepository*.
 ![Alt text](https://github.com/Protontech-1803/devops/blob/master/ImplementingMicroserviceSpringCloudEurekaServiceRegistry/img/2e.png)
f.	Add the Eureka client annotation in main class of *order_service* microservice.
  ![Alt text](https://github.com/Protontech-1803/devops/blob/master/ImplementingMicroserviceSpringCloudEurekaServiceRegistry/img/2f.png)
h. Create and configure *application.yml* file in *order_service* microservice.
 ![Alt text](https://github.com/Protontech-1803/devops/blob/master/ImplementingMicroserviceSpringCloudEurekaServiceRegistry/img/2h.png)
3.	Similarly, *payment_service* microservice is created.
 ![Alt text](https://github.com/Protontech-1803/devops/blob/master/ImplementingMicroserviceSpringCloudEurekaServiceRegistry/img/3.png)
4.	Execute all the services and verify the microservices registered in Eureka Server.
![Alt text](https://github.com/Protontech-1803/devops/blob/master/ImplementingMicroserviceSpringCloudEurekaServiceRegistry/img/4.png)
 
