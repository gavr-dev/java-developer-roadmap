# Backend Developer Roadmap (Java)

## Java Core

### Materials

**Books**
- Head first Java - Kathy Sierra
- Core Java, Vol 1 & 2 - Horstmann 
- Core Java for the Impatient - Horstmann
- Effective Java - Joshua Bloch
- Java Concurrency in Practice - Goetz,  Joshua Bloch

**Documentation**
- [JDK 18 Documentation - Home](https://docs.oracle.com/en/java/javase/18/index.html)
- The Java Language Specification
- The Java Virtual Machine Specification

**Курсы**

- https://zhukovsd.github.io/java-backend-learning-course/

### Topics

**Base**
- Syntax
- DataTypes, Variables
- Conditionals
- DataStructures
- OOP, Interfaces, Classes
- Packages
- IO
	- File IO
	- Network IO
	- Sockets
	- NIO
- Loops
- Exception Handling
- Collections

**Intermediate**
- Serialization
- Generics
- Lambdas
- Stream API
- Data Time API
- Concurrency
	- Thread, Runnable
	- volatile
	- synchronize
- Networking & Sockets

**Advanced**
- JVM, Heap, Stack
- GC
- Classloader
- Memory Managment (JMM)
- Concurrency
	- Atomic
	- Executors
	- ReentranceLock
	- Collections
	- Virtual threads
- Profiling
	- jconsole
	- jvisualvm
	- jProfiler
	- thread dump
	- heap dump

## Java EE

### Topics

- Servlets
- JSP
- JMS
- Application Servers
	- Tomcat
	- Jetty
	- WildFly
## Frameworks

### Materials
**Books**
- "Spring in Action" series
  
**Documentation**
- Official documentation
### Topics
**Spring** 
 - Spring Core
     - Configuration
     - DI, IoC
     - AOP
     - Annotations
     - Bean Scope
     - Bean Factory
     - Application Context
 - Spring Boot
     - Starters  
     - Autoconfiguration
     - Actuators
     - Embedded Server
 - Spring MVC
     - Architecture
     - Components
 - Spring Data
     - Spring Data JPA
     - Spring Data JDBC
 - Spring Security
     - Authentification
     - Authorization
     - OAuth2
     - JWT
     - SAML
     - LDAP
    - Databases

**Databases**
 - JDBC
     - JDBI3  
     - JDBC Template
 - ORM/JPA
     - Hibernate
		  - ORM
		  - Persistence Context
		  - Relationships
		  - Lazy, Eager
		  - Entity Lifecycle
		  - Cache
	 - OpenJPA
 - JOOQ     
 - Liquibase/Flyway 

**Other**
- Logging 
	 - Log4j2
	 - Logback     
	 - SLF4J     
- Apache Spark 
- Utils 
	 - Guava     
	 - Apache Commons     
	 - Jackson 
	 - Quartz