## What is Maven ?


Maven is a powerful build automation tool used primarily for Java projects. 

It simplifies the process of building, testing, and deploying applications by managing project dependencies and configuration. 

Maven uses an XML file called `pom.xml` (Project Object Model) to manage project settings and dependencies.




## The Purpose of Using Maven


Maven's primary goal is to allow a developer to comprehend the complete state of a development effort in the shortest period. 

Using Maven, you can manage your project lifecycle, dependencies, and contributions from multiple team members effectively. 

This tool helps to ensure that everyone on your team is using the same versions of libraries and plugins, leading to a smoother collaboration.


## Why Use Maven in DevOps ?


In a DevOps environment, automation and integration are key. Maven fits well into this ecosystem by:

`Automating Builds` Compile code, run tests, and package applications automatically.

`Managing Dependencies` Easily manage and update project libraries.

`Consistent Builds` Ensure builds are consistent across different environments.


## Key Features of Maven


`Ease of setup` Simple project setup that follows best practices - get a new project or module started in seconds

`Consistency` Consistent usage across all projects - means no ramp-up time for new developers coming onto a project

`Model-based builds` Maven can build any number of projects into predefined output types such as a JAR, WAR, or distribution based on metadata about the project.

`Dependency Management` Automatically downloads and manages libraries needed for your project, reducing conflicts and streamlining builds.

`Project Lifecycle Management` Helps in organizing the entire build lifecycle from compilation to packaging to deployment in a structured way.

`Integration with IDEs` Works well with popular Integrated Development Environments (IDEs) like Eclipse and IntelliJ.


## Setting Up Maven


You can install Maven on Ubuntu in a quick and easy way through the apt command.

#### 1. Open the terminal on Ubuntu and type the command that follows

```
sudo apt update -y && sudo apt upgrade -y
```

#### 2. Install Maven on Ubuntu


```
sudo apt install maven -y
```

#### 3. Verifying installation

```
mvn -version
```

---------------------------------------------



## mvn-proj


### Install Java & Maven on Ubuntu

```
sudo apt update
sudo apt install -y openjdk-17-jdk maven
java -version
mvn -v
```

### Clone your repo


`pom.xml` The configuration file for your Maven project.

`src/main/java` Contains your application's source code.

`src/test/java` Contains your test code.


### Build the Project

```
mvn compile
```

### Run Tests

```
mvn test
```

### Package the Application

```
mvn package
```

(After packaged, A jar file created)


### Now Deploy

```
java -jar target/springboot-static-app-1.0.0.jar
```

`server pub-ip:8082`


**NB**

Maven Clean `mvn clean`

Maven Clean Package `mvn clean package`


------------------------------------------



