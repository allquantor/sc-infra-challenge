<center>
     <h2>Cyber Security Venture - Stealth</h2> 
     <h3>Software Engineer Challenge - Site Reliability</h3>
</center>
 
**Assignment:**

Dockerize a given application `publisher.jar`. Write a basic application in a language of your choice to listen and write the 
 input sent by `publisher` in a text file. Your written application should be dockerized as well. A load balancer should distribute the load
  produced by the `publisher` to N instances of your application.
  

   
    Setup
    ======================
            
                                                                   +----------+
                                                                   |          |
                                                            +-------> app1    +
                                                            |      |          |
                                                            |      +----------+
                                                            |
                                                            |
        +----------+                   +--------------+     |      +----------+
        |          |     messages      |              |     |      |          |
        |publisher --------------------> loadbalancer  -----+-------> app2    +
        |          |                   |              |     |      |          |
        +----------+                   +--------------+     |      +----------+
                                                            |                               -
                                                            |
                                                            |
                                                            |      +----------+
                                                            |      |          |
                                                            +-------> appN    +
                                                                   |          |
                                                                   +----------+
  
  

1. Rules:

* You have up to 6 hours to complete the tasks, be careful with your time, make sure you understand the requirements correctly.
* Try not to over-optimize. An MVP with good documentation counts more than a single polished component.
* We are interested how you handle the provisioning of context information (ENV Variables), how you stick everything together,
 what other components you will use, which security rules will you ensure? 


2. User stories:

* Your App should receive messages on address and port you specify as ENV Variables in the environment `publisher.jar` will run. 
( Hint: _A dockerized Bash Script with netcat would be enough._)
* Your App should simply write the messages inside a text file.
* Your should Dockerize your app as well as the `publisher` app.
* A load balancer should distribute the load on your apps coming from the `publisher`.

3. Specifications:

*  **Messages examples**
  ```
  | Coordinates(-149.4331873,60.12892832,Starbucks - AK - Seward  00025) |
                   
  | Greets(Privet: {815548195}) |
  ```
  Type Specifications:
  ```
  Coordinates(long: Double, lat: Double, name: String)
  Greets(greet: String)
  ```
  The messages are divided by a CRLF. 
  
* **Dockerizing**
 
    Environment Variables accepted by `publisher.jar`.

  ```
    C_TARGET_HOST // Client Target Host (Default 127.0.0.1)
    C_TARGET_PORT // Client App Port (Default 9011)
    C_DATA_PATH // Path to data.csv (Default "data.csv")
  ```
    * The `publisher` Can be started with (`java -jar publisher.jar`)
    * Java 8 is required
    * The `publisher` require demo data, is inside of `./data/`  

5. Deliverable:

* The solution should contain:
    * Dockerfile to build your app
    * Dockerfile for the LoadBalancer functionality
    * Dockerfile for `publisher`
    * A script/provision functionality to bring it up locally on a UNIX machine with docker and test the functionality.
    * The write results of your app shold be stored outside of docker.
    
* The solution should have a comprehensive documented functionality and running instructions. 
* You can use any language/technology/framework of your choice. But we will ask for the rationale of your decision. 
* You can provide a github link to the solution or send us a tar ball with the sourcecode. 

6. Bonus Points when:

* What are the critical structures of the application, what are the possible bottlenecks, what you had did when you had more time. We are curious of your thoughts! 
* User Kubernetes or Swarm! 

_The Bonus points don't have to be delivered on time - you can submit them later!_ 

Looking forward for your result, have fun with this task and good luck! 


  








