# practice

I am creating a new Spring Boot project in IntelliJ as a beginner Java developer.

My manager has asked me to create a basic setup of the Unit of Work pattern. I want to implement it using Spring Boot, Spring Data JPA, and @Transactional rather than a custom Java-only implementation.

Please generate a complete beginner-friendly project structure and explain every step.

Requirements:
- Java 17
- Spring Boot 3.x
- Maven
- Spring Web
- Spring Data JPA
- H2 Database
- Demonstrate Unit of Work using @Transactional

Project Name:
sms-workbench

Please provide:

1. Recommended package structure
   - controller
   - service
   - repository
   - entity
   - config (if needed)

2. Complete code for:
   - Main Application class
   - User Entity
   - UserRepository
   - UserService
   - UserController

3. pom.xml dependencies required

4. application.properties configuration

5. Explanation of:
   - What JPA is
   - What Hibernate is
   - What a Repository is
   - What @Transactional does
   - How @Transactional implements the Unit of Work pattern

6. Example API endpoint that creates a User record

7. Explain what happens internally from:
   Controller → Service → Repository → Database

8. Show how transaction rollback works when an exception occurs.

Assume I am an absolute beginner and explain concepts clearly with examples.
