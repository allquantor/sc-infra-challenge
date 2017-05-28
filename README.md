<center>
     <h2>Cyber Security Venture - Stealth</h2> 
     <h3>Software Engineer Challenge - Site Reliability</h3>
</center>
 
**Assignment:**

Write an application `Consumer` to consume and write (inside of a text file) the requests made by the `Publisher` (`publisher.jar`). Dockerize both `Publisher` && `Consumer`. Connect the Docker containers. `Consumer` should be able to run N instances.


   
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
        |publisher --------------------> ??????????    -----+-------> app2    +
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

* Your App should receive messages on address and port that you have to  specify as Environment Variables.
( Hint: _A dockerized Bash Script with netcat would be enough._)
* Your App should write the messages inside a text file.
* Rollout should be made by starting of one file/binary...

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
    * The `Publisher` Can be started with (`java -jar publisher.jar`)
    * Java 8 is required
    * The `Publisher` require demo data, is inside of `./data/`  

5. Deliverable:

* The solution should contain:
    * Dockerfile to build your app
    * Dockerfile for the LoadBalancer functionality
    * Dockerfile for `Publisher`
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


  








