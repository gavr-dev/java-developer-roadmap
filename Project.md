## Technologies
- Java 21
- Spring (Boot, Core, MVC, Security, Data, AOP)
- Hibernate, Jooq, Liquibase/Flyway
- PostgreSQL
- ActiveMQ/RabbitMQ
- Kafka
- Hazelcast IMDG
- Activiti/Camunda BPM
- JUnit, Mockito, H2, JaCoCo, JBehave
- Swagger, Open API, REST, gRPC
- Logback / Log4j2, SL4J 
- JMX, JProfiler, VisualVM
- Redis, Cassandra
- Reactive Streams, Akka Actors
- Docker, Kubernetes, Helm

## Project Example

Managing an investment portfolio (example, [https://intelinvest.ru](https://intelinvest.ru)), the following functionalities must be implemented:
- Adding transactions for depositing money, buying or selling securities
- A dashboard displaying the current value of the portfolio, all transactions, and changes in value
- The ability to view details about securities
- An example business process - running every N minutes/hours for each client or for a specific client at the push of a button; steps:
	- Retrieving the value of securities (stocks, bonds) from an external system
	- Recalculating the total portfolio value
	- Recalculating the proportions and returns of individual securities
	- (Optionally) Exporting a brief summary to a file

## Project

### General Points
- Using Java 21 and features from versions 8+
- All modules based on Spring Boot
- Logging using Logback or Log4j (slf4j)
### Module 0
- Centralized module for authorization/authentication (registration can be added) using Spring Security
- Creates a user session, stores it in Hazelcast
- Information about users, roles stored in PostgreSQL
- Database access through Jooq
### Module 1.1
- Business module, provides REST API
	- Part described in Swagger, generating code and setting up REST
- Data model - minimum 5-7 related tables
- Information stored in PostgreSQL - 1 module = 1 database
- Database scripts deployed using Liquibase
- Database access through Hibernate and Spring Data JPA
### Module 1.2
- Business module with a process described using BPMN
- Using Activiti or Camunda
- Ideally, calling some external system through integration
### Module 2.1
- Collection and aggregation of logs
- All modules log in Kafka
- Reading logs and breaking down statistics, for example, the number of messages of each log level per hour
- Logic implemented using Reactive Streams and Reactor
- Result written in Redis/MongoDB
### Module 2.2
- Collection and aggregation of logs 
- All modules log in ActiveMQ/RabbitMQ
- Reading logs and breaking down statistics, for example, the number of messages of each log level per hour
- Logic implemented using Akka Actor
- Result written in Cassandra
### Module 3
- Health check verification
- All modules send their status via gRPC every n seconds (using heap, memory, etc.)
- Can simply write to log or save in a new database
## Frontend
1. JSP, Thymeleaf, FreeMarker
2. React, Vue
## Functional Testing
1. Junit + Mockito
2. Adding H2 + Jbehave

## CI/CD
- Git
- Using GitHub or GitLab
- Module 1, distribution - fat jar, app config, log config, start-up script, database update scripts
- Module 2, distribution - jar, lib, app config, log config, start-up .sh file, database update scripts

### Stage 1
- CI
  - Project build - Maven assembly plugin
  - Run PMD and Checkstyle -> report
  - Run unit tests + coverage percentage with JaCoCo -> report
  - Release version + tag
  - Automated tests (component or integration)
  - Distribution assembly
  - Snapshot version
- CD
  - Get familiar with Docker
  - Set up Jenkins in Docker - pull project from Git, build, add test, Docker image, store in Docker registry
  - Configure a job that takes the distribution (ZIP), creates folders/updates version
    - Install distribution - ZIP with jar, configs, etc.
    - Update relational database using Liquibase
    - Consider new deployment (folder structure) and update (logs preserved)
    - Restart/launch service
### Stage 2
- CI
	- Assemble distribution -> Create Docker Image
- CD
	- Deploy artifacts -> Launch container(s) using docker-compose (consider updating individual modules)
### Stage 3
- CI
	- Create Docker Image -> Create Helm Chart
- CD
	- Launch containers -> Deploy to Kubernetes
## Load Testing
- Write a script in bash/python

 to generate load on the business module
- Analyze behavior of all modules and database using jconsole, visualvm, jprofiler