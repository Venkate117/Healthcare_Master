# Healthcare Program

  This application is a spring boot micro-service. It holds a eureka registry which manages micro-serivces and a micro-service called service.
  Added Zuul capability to the application.
  
## How to run
 
 1) Maven install 
 
    mvn -U clean install
    
 2) Run eureka-registry as a spring boot application and launch following url in the browser
 
    http://localhost:8006
 
    Eureka server dashboard will be shown
    
 3) Run service as a spring boot application and refresh eureka server dashboard, observe one micro-service with service will be shown.
 
 4) Run Zuul server and access service from zuul service with the following endpoint
 
 	http://localhost:8005/service/swagger-ui.html#/enrollee-controller
    
 
## Test application

 1) Launch swagger-url to see all the implemented webservices
 
    http://localhost:8005/service/swagger-ui.html#/enrollee-controller
    
 2) Test screenshots of swagger page are attached in the project folder 
    
 3) Used h2 db to test the functionality, following are the db details
 
    - Launch following url for h2 client, http://localhost:8007/h2-console/   and fill in below details,
    - Driver Class : org.h2.Driver
    - Jdbc Url :    jdbc:h2:mem:testdb
    - Username : sa
    - Password : password
    

## URL versioning

1) Url versioning is implemented to two web services, saveEnrollee and getEnrolleeById. Two versions endpoints are below,

   - POST http://localhost:8005/service/enrollee/v1
   - POST http://localhost:8005/service/enrollee/v2
   - GET http://localhost:8005/service/enrollee/v1
   - GET http://localhost:8005/service/enrollee/v2
   
2) I did not add any functionality to the version 2 services. Added a place-holder for it.
   
## Added integration tests for the end points in controller. Used spring mock mvc to mock the services

## Containerization
 
1) Added docker capabilities by adding independent container definitions to three micro services
2) Docker images will be created on maven build. Used Spotify maven plugin for this.
3) Defined a docker compose file to spin all the required containers using below command

    - docker-compose up
4)  ** Container to Container communication is not working now. Its taking time for the fix. I happened to jump to my office work. 
5) So, submitting without container to container communication fix.    
   
    
    