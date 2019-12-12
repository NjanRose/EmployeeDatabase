# EmployeeDatabase
<h2>Microservice Deployment using Spring Boot, Mysql and Pivotal Cloud Foundry:

<h3>Aim</h3><br>
To Deploy a microservice using Spring Boot and Pivotal Cloud Foundry keeping MySQL as database.This project is developed using the employee database.

<h3>Requirements</h3>
  
1) Latest JDK[Using Version 13.0.1 in this project]<br>
2) Eclipse IDE + Spring Tool Suite[4.4.2 RELEASE used]<br>
3) SoapUI for testing REST API<br>
4) Xampp for MYSQL[using phpMyAdmin]<br>
5) Cloud Foundry CLI for hosting<br>

<h3>Steps to Set Up Your Database:</h3>
  
1)  Download and Install Xampp <br> 
2) Open Xampp_control
3) Click on Start for Mysql
4) Open browser,go to https:/localhost/dashboard/
5) Select phpMyAdmin and configure any credentials(username,password) if needed before
6) Create your project database(here Employee Database) and the required relations and constraints
7) One can manually insert data into this as well. Now, you are ready to connect your spring boot application.

<h3>Steps to connect to database:</h3>
  
1) Install Eclipse if not already installed.
2) Download STS from Eclipse MarketPlace to run Spring Boot Application
3) New/Open a Spring Boot Starter Project
4) Add the following dependencies in the pom.xml file:<h6>&lt;dependency><br>
			&lt;groupId>org.springframework.boot</groupId><br>
			&lt;artifactId>spring-boot-starter-jdbc</artifactId><br>
		&lt;/dependency><br>
		&lt;dependency><br>
			&lt;groupId>mysql</groupId><br>
			&lt;artifactId>mysql-connector-java</artifactId><br>
			&lt;scope>runtime</scope><br>
		&lt;/dependency></h6>
5) Create an application.properties file under src/main/resources
6) Add the following details so that the application can find your database to connect:<h6>spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver<br>
spring.datasource.url=jdbc:mysql://localhost/mydb?useUnicode=true&useJDBCCompliantTimezoneShift=true&useLegacyDatetimeCode=false&serverTimezone=UTC<br>
spring.datasource.username = root<br>
spring.datasource.password = <br></h6>
7) Next write classes for the controller, service, Dao and Model
8) Run the Application and test CRUD operations to know that you have successfully connected to your Database.

<h3>Steps to Deploy on Pivotal Cloud Foundry:</h3>
  
1)  Install CF from CLI executable. <br> 
2) Sign Up to cloud foundry and go to your account.
3) Create your company under development space, Add Mysql (SparkDB plan) under services.
4) Go to where Cloud Foundry is installed and open cmd there.
5) Login using: cf login -a api.run.pivotal.io,then enter your credentials.
6) Package your Application as .war by including the below in pom.xml:<h6>&lt;packaging>war&lt;/packaging></h6>
7) Maven Clean,Maven Install(this will generate the .war file in target folder)
8) Create manifest.yml file and add the necessary details like follows:<h6>applications:<br>- name: demoutkanurose<br>path:target\demoutkanurose.war<br>
domain: cfapps.io<br>
memory: 1G<br>
instances: 1<br>
services:<br>- mysql</h6>
9) Go to your project folder and open cmd here.
10) Execute: cf push
11) One app should be seen running in your console.
12) Click on the url and test your Deployed Application.
13) In case of sql error, one can download PivotalMySQLWeb which is a user-friendly UI tool to handle Cloud Foundry Mysql Database
14) Push it to your account using: cf push and then consequently use it to debug.
