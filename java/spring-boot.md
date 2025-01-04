# DI injection methods in spring boot

### Constructor Injection

**Description:** Dependencies are provided through the class constructor. Spring injects the dependencies when it instantiates the bean.

**Pros:**
- Ensures immutability since dependencies are provided at object creation and cannot be changed afterward.
- Makes the dependencies explicit and easy to understand.
- Dependencies are required to instantiate the object, reducing the chances of null values.
- Ideal for mandatory dependencies.
- Detects circular dependencies early.

**Cons:**
- Can become cumbersome with too many dependencies, leading to long constructors.

### Setter Injection

**Description:** Dependencies are injected via public setter methods after the object is created.

**Pros:**
- Useful for optional dependencies, since you can choose whether or not to set the dependency.
- More flexible, allowing you to change the dependencies later.
- Avoids cluttered constructors in case of too many dependencies.

**Cons:**
- Does not guarantee immutability, as the dependencies can be changed after object creation.
- The object can be in an incomplete state if the setter is not called, leading to potential NullPointerExceptions.
- Less suitable for required dependencies.

### Field Injection

**Description:** Dependencies are injected directly into the class fields, usually by annotating the fields with `@Autowired`.

**Pros:**
- Very simple to use and less boilerplate code (no need for setters or constructors).

**Cons:**
- Violates encapsulation since the dependencies are not set through constructors or setters, but directly injected into the fields.
- Harder to test: Mocking and injecting dependencies in unit tests is more difficult.
- Dependencies are less visible, making it harder to understand what the class depends on.
- Immutability is not ensured since fields can be modified post-construction.
- Not ideal for required dependencies, as it can lead to uninitialized or null values.
- Spring discourages field injection due to its downsides, like violating best practices in object-oriented design.

## Bean Scope

- **Singleton:** Only one object gets created when you use `getBean`.
- **Prototype:** Different object is created every time you use `getBean`.
- **Request**
- **Session**

## JSP

Spring Boot does not support JSP by default, we have to install Tomcat Jasper same version of Tomcat Jasper as Tomcat server that we will use to convert JSP to servlet.

**Spring Boot does not support JSP by default:**
Spring Boot prefers using Thymeleaf or Freemarker for rendering views because JSP has several limitations when working with embedded servlet containers (like the embedded Tomcat Spring Boot uses by default). JSP requires specific servlet handling and configurations which don't work well with Spring Boot's default setup.

**Tomcat Jasper for JSP compilation:**
To use JSP with Spring Boot, you do need Jasper, the JSP engine for Apache Tomcat. Spring Boot does not include the Jasper dependency by default, so you'll need to add it manually. You need to include the `tomcat-jasper` dependency in your `pom.xml` (for Maven) or `build.gradle` (for Gradle). The version of `tomcat-jasper` should match the version of the embedded Tomcat that Spring Boot uses. If you are using an external Tomcat server (not the embedded one), the version should align with that.

**Limitations of JSP with Spring Boot:**
- JSP files need to be placed in `src/main/webapp/WEB-INF/jsp/`, and you might need to customize your ViewResolver bean.
- Some features like hot reloading may not work as smoothly with JSP, especially when using embedded containers.

In summary: yes, you need Tomcat Jasper for JSP compilation, but keep in mind that using JSP with Spring Boot is not recommended, and it might require additional setup and careful handling.

# Aspect-Oriented Programming (AOP)

Aspect-Oriented Programming (AOP) is a programming paradigm that helps in separating cross-cutting concerns from the main business logic. Here's a breakdown of the core AOP concepts:

1. **Aspect:** An aspect encapsulates a concern that cuts across multiple classes or modules. For example, logging, security, or transaction management. It contains the logic that is applied to multiple points in an application.
2. **Join Point:** A specific point in the execution of the program where an aspect can be applied. Examples include method calls, object instantiations, or field access.
3. **Advice:** The actual code that is executed at a join point. Different types of advice include:
   - **Before Advice:** Runs before a join point.
   - **After Advice:** Runs after a join point.
   - **Around Advice:** Runs both before and after the join point, allowing more control.
4. **Pointcut:** A set of join points where the advice should be applied. Pointcuts are typically defined using expressions to match specific join points in the code (e.g., all methods in a certain class).
5. **Weaving:** The process of linking aspects with other application code at specified join points. Weaving can occur at different times:
   - **Compile-time Weaving:** Aspects are woven into the code at compile time.
   - **Load-time Weaving:** Aspects are woven during class loading, after the code is compiled but before it is executed.
   - **Runtime Weaving:** Aspects are applied during program execution.
6. **Target Object:** The object whose method or behavior is being advised or intercepted by an aspect.

By using AOP, developers can modularize concerns that span multiple parts of an application, improving code readability, maintainability, and separation of concerns.


# EnableJpaAuditing

1. `@EnableJpaAuditing` annotation is used to enable JPA Auditing, annotate main class with `@EnableJpaAuditing` annotation.
2. `@EntityListeners(AuditingEntityListener.class)` annotation on the entity class to enable auditing for that entity.
3. `@CreatedDate`, `@LastModifiedDate`, `@CreatedBy`, `@LastModifiedBy` annotations are used to enable auditing fields in the entity class.
4. `@EnableJpaAuditing(dateTimeProviderRef = "dateTimeProvider")` annotation is used to provide custom DateTimeProvider.
5. Implement `AuditorAware` interface to provide the current logged-in user.

# DTO Validation

1. Annotate the DTO attributes with
   - `@NotNull`, `@Size`, `@Email`, `@Pattern`, `@Min`, `@Max`, `@Positive`, `@PositiveOrZero`, `@Negative`, `@NegativeOrZero`, `@NotBlank`, `@NotEmpty`, `@Null`, `@Future`,
     `@Past`, `@FutureOrPresent`, `@PastOrPresent` annotations.
2. Use `@Valid` annotation to validate the nested DTO objects.
3. Use `@Validated` annotation to validate the DTO object.

# JPA Notes

1. `@Entity` annotation is used to mark the class as an entity.
2. `@Table` annotation is used to provide the table name for the entity.
3. `@Id` annotation is used to mark the field as primary key.
4. `@GeneratedValue` annotation is used to generate the primary key value.
5. `@Column` annotation is used to provide the column name for the field.
6. `@Transient` annotation is used to mark the field as not persistent.
7. `@OneToOne`, `@OneToMany`, `@ManyToOne`, `@ManyToMany` annotations are used to define the relationship between entities.
8. `@JoinColumn` annotation is used to provide the join column name for the relationship.
9. `@JoinTable` annotation is used to provide the join table name for the many-to-many relationship.
10. `@Embedded` annotation is used to embed the object into the entity.
11. `@Embeddable` annotation is used to mark the class as embeddable.
12. `@MappedSuperclass` annotation is used to mark the class as a superclass.
13. `@Inheritance(strategy = InheritanceType.SINGLE_TABLE)` annotation is used to define the inheritance strategy.
14. `@DiscriminatorColumn` annotation is used to provide the discriminator column name.
15. `@DiscriminatorValue` annotation is used to provide the discriminator value for the entity.
16. `@EntityListeners(AuditingEntityListener.class)` annotation is used to enable auditing for the entity.
17. `@CreatedDate`, `@LastModifiedDate`, `@CreatedBy`, `@LastModifiedBy` annotations are used to enable auditing fields in the entity.
18. `@EnableJpaAuditing` annotation is used to enable JPA Auditing.
19. `@EnableJpaRepositories(basePackages = "com.example.repository")` annotation is used to enable JPA repositories.
20. `@Query` annotation is used to define the custom query in the repository.
21. `@Modifying` annotation is used to mark the query as modifying query.
22. `@Transactional` annotation is used to mark the method as transactional.
23. `@EntityGraph(attributePaths = "department")` annotation is used to fetch the associated entity eagerly.
24. `@NamedEntityGraph(name = "Employee.department", attributeNodes = @NamedAttributeNode("department"))` annotation is used to define the named entity graph.
25. `@NamedAttributeNode` annotation is used to define the attribute node in the named entity graph.
26. `@NamedSubgraph` annotation is used to define the subgraph in the named entity graph.
27. `@NamedEntityGraphs({@NamedEntityGraph(name = "Employee.department", attributeNodes = @NamedAttributeNode("department"))})` annotation is used to define multiple named entity graphs.
28. `@EntityGraph(attributePaths = {"department", "projects"})` annotation is used to fetch multiple associated entities eagerly.

# How to build REST API?

1. Define the API endpoints using `@RestController` and `@RequestMapping` annotations.
2. Define the request mapping using `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping` annotations.
3. Use `@PathVariable` and `@RequestParam` annotations to get the request parameters.
4. Use `@RequestBody` annotation to get the request body.
5. Use `ResponseEntity` class to return the response with status code.
6. Use `@ResponseStatus` annotation to set the status code for the response.
7. Use `@ControllerAdvice` and `@ExceptionHandler` annotations to handle exceptions globally.
8. Use `@Valid` annotation to validate the request body.
9. Use `@Validated` annotation to validate the request parameters.
10. Use `@CrossOrigin` annotation to enable cross-origin requests.
11. Use `@Async` annotation to make the method asynchronous.
12. Use `@Scheduled` annotation to schedule the method execution.
13. Use `@EnableScheduling` annotation to enable scheduling.
14. Use `@EnableAsync` annotation to enable asynchronous processing.
15. Use `@EnableWebMvc` annotation to enable Web MVC configuration.
16. Use `@EnableWebSecurity` annotation to enable Web security configuration.
17. Use `@EnableGlobalMethodSecurity` annotation to enable global method security.
18. Use `@EnableJpaAuditing` annotation to enable JPA Auditing.
19. Use `@EntityListeners(AuditingEntityListener.class)` annotation to enable auditing for the entity.
20. Use `@CreatedDate`, `@LastModifiedDate`, `@CreatedBy`, `@LastModifiedBy` annotations to enable auditing fields in the entity.

# Most used Dependencies

- `spring-boot-starter-actuator`
- `spring-boot-starter-data-jpa`
- `spring-boot-starter-validation`
- `spring-boot-starter-web`
- `spring-boot-devtools`
- `spring-boot-starter-test`
- `spring-boot-starter-security`
- `spring-boot-starter-oauth2-client`
- `spring-boot-starter-oauth2-resource-server`
- `spring-boot-starter-oauth2-authorization-server`
- `com.h2database:h2`
- `org.projectlombok:lombok`
- `org.springframework.boot:spring-boot-starter-test`
- `org.springdoc:springdoc-openapi-starter-webmvc-ui:2.7.0`

# Spring Boot Annotations

1. The `@SpringBootApplication` annotation is a convenience annotation that combines the following three annotations:

   - `@EnableAutoConfiguration`: This annotation tells Spring Boot to start adding beans based on classpath settings, other beans, and various property settings. For example, if `spring-webmvc` is on the classpath, this annotation flags the application as a web application and activates key behaviors, such as setting up a `DispatcherServlet`.
   - `@ComponentScan`: Enables component scanning so that the web controller classes and other components you create will be automatically discovered and registered as beans in Spring’s application context.
   - `@Configuration`: Allows you to register extra beans in the context or import additional configuration classes.

By using `@SpringBootApplication`, you can simplify your main class configuration. Here is an example:

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class MySpringBootApplication {
    public static void main(String[] args) {
        SpringApplication.run(MySpringBootApplication.class, args);
    }
}
```

This single annotation is often placed on the main class of your Spring Boot application, which serves as the entry point for the application.

Behind the scenes it:

- Scans classpath for Spring components
- Auto-configures beans based on dependencies
- Sets up embedded servers if present
- Configures logging, security, etc.
- Processes property files
- Creates ApplicationContext

2. `@RestController`: This annotation is a specialized version of the `@Controller` annotation. It is used to create RESTful web services using Spring MVC. It combines `@Controller` and `@ResponseBody`, eliminating the need to annotate every request handling method with `@ResponseBody`.

3. `@RequestMapping`: This annotation is used to map web requests to specific handler classes and/or handler methods. It can be applied at the class level and/or at the method level in a controller.

4. `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`: These are shortcut annotations for `@RequestMapping` with specific HTTP methods. They are used to map HTTP GET, POST, PUT, and DELETE requests to specific handler methods.

5. `@PathVariable`: This annotation is used to extract values from the URI path and bind them to method parameters in a controller.

6. `@RequestParam`: This annotation is used to extract query parameters from the request URL and bind them to method parameters in a controller.

7. `@RequestBody`: This annotation is used to bind the HTTP request body to a method parameter in a controller.

8. `@ResponseBody`: This annotation is used to indicate that the return value of a method should be used as the response body of the HTTP response.

9. `@ResponseStatus`: This annotation is used to set the HTTP status code for the response.

10. `@ControllerAdvice`: This annotation is used to define global exception handling and data binding rules for all controllers in the application.

11. `@ExceptionHandler`: This annotation is used to define a method that handles specific exceptions thrown by controller methods.

12. `@Valid`: This annotation is used to trigger validation on the annotated object, typically a request body or a method parameter.

13. `@Validated`: This annotation is used to trigger validation on the annotated object, typically a request parameter.

14. `@CrossOrigin`: This annotation is used to enable cross-origin requests for a specific controller or method.

15. `@Async`: This annotation is used to indicate that a method should be executed asynchronously.

16. `@Scheduled`: This annotation is used to schedule a method to be executed at fixed intervals or cron expressions.

17. `@EnableScheduling`: This annotation is used to enable scheduling support in the application.

18. `@EnableAsync`: This annotation is used to enable asynchronous processing support in the application.

19. `@EnableWebMvc`: This annotation is used to enable Web MVC configuration in the application.

20. `@EnableWebSecurity`: This annotation is used to enable Web security configuration in the application.

21. `@EnableGlobalMethodSecurity`: This annotation is used to enable global method security in the application.

22. `@EnableJpaAuditing`: This annotation is used to enable JPA Auditing in the application.

23. `@EntityListeners(AuditingEntityListener.class)`: This annotation is used to enable auditing for the entity.

24. `@CreatedDate`, `@LastModifiedDate`, `@CreatedBy`, `@LastModifiedBy`: These annotations are used to enable auditing fields in the entity.

# AOP Notes

Aspect-Oriented Programming (AOP) is a programming paradigm that aims to increase modularity by allowing the separation of cross-cutting concerns. In Spring, AOP is used to define common behaviors that can be applied across various points in an application, such as logging, transaction management, and security.

Key concepts in AOP:

1. **Aspect**: A module that encapsulates a concern that cuts across multiple classes. An aspect is a combination of advice and pointcuts.
2. **Advice**: Action taken by an aspect at a particular join point. Types of advice include:
   - `@Before`: Runs before the method execution.
   - `@After`: Runs after the method execution.
   - `@AfterReturning`: Runs after the method returns a result.
   - `@AfterThrowing`: Runs after the method throws an exception.
   - `@Around`: Runs before and after the method execution.
3. **Join Point**: A point during the execution of a program, such as the execution of a method or the handling of an exception.
4. **Pointcut**: A predicate that matches join points. Advice is associated with a pointcut expression and runs at any join point matched by the pointcut.
5. **Weaving**: The process of linking aspects with other application types or objects to create an advised object. This can be done at compile time, load time, or runtime.

Example of AOP in Spring:

```java
import org.aspectj.lang.annotation.Aspect;
import org.aspectj.lang.annotation.Before;
import org.springframework.stereotype.Component;

@Aspect
@Component
public class LoggingAspect {

    @Before("execution(* com.example.service.*.*(..))")
    public void logBeforeMethod() {
        System.out.println("Method execution started");
    }
}
```

In this example, the `LoggingAspect` class is an aspect that contains a `@Before` advice. The advice is applied to all methods in the `com.example.service` package, and it logs a message before the method execution.

To enable AOP in a Spring Boot application, use the `@EnableAspectJAutoProxy` annotation in your main configuration class:

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.annotation.EnableAspectJAutoProxy;

@SpringBootApplication
@EnableAspectJAutoProxy
public class MySpringBootApplication {
    public static void main(String[] args) {
        SpringApplication.run(MySpringBootApplication.class, args);
    }
}
```

This annotation enables support for handling components marked with `@Aspect` annotations, allowing Spring to process and apply the aspects.

# Spring Boot Request Lifecycle

## Complete Request Flow
1. **Client Request**
   - HTTP request initiated from client

2. **Embedded Server** (Tomcat/Jetty/Undertow)
   - Receives HTTP request
   - Handles connection management

3. **Filter Chain** (Pre-processing)
   - Security filters
   - CORS filters
   - Custom filters

4. **DispatcherServlet**
   - Front controller pattern
   - Central entry point for handling requests

5. **Handler Mapping**
   - Determines which controller handles request
   - Maps URLs to handler methods

6. **Handler Interceptors** (PreHandle)
   - Method interceptors
   - Can block request processing
   - Authentication/authorization checks

7. **Argument Resolvers**
   - Resolves method parameters
   - Handles @PathVariable, @RequestBody, etc.

8. **Message Converters** (Request)
   - Converts request payload
   - JSON/XML deserialization

9. **AOP Aspects**
   - Cross-cutting concerns
   - Method execution aspects

10. **Controller/Handler Execution**
    - Actual business logic
    - Service layer calls
    - Database operations

11. **Message Converters** (Response)
    - Converts response objects
    - JSON/XML serialization

12. **Handler Interceptors** (PostHandle)
    - Post-processing of response
    - Modify response if needed

13. **Exception Handlers**
    - Global exception handling
    - @ControllerAdvice processing
    - Error response generation

14. **Handler Interceptors** (AfterCompletion)
    - Final interceptor phase
    - Cleanup operations

15. **Filter Chain** (Post-processing)
    - Reverse order execution
    - Response modifications

16. **Response**
    - Final response sent to client

## Visual Flow
```
Client Request -> Embedded Server -> Filter Chain -> DispatcherServlet -> Handler Mapping -> Handler Interceptors (PreHandle) -> Argument Resolvers -> Message Converters (Request) -> AOP Aspects -> Controller/Handler Execution -> Message Converters (Response) -> Handler Interceptors (PostHandle) -> Exception Handlers -> Handler Interceptors (AfterCompletion) -> Filter Chain -> Response
```

# Explain Servlet and Servlet Container

## Servlet
A Servlet is a Java class used to process HTTP requests and generate HTTP responses in web applications. It follows the Java Servlet API and runs on a web server or servlet container.

### Key Characteristics:
- **Lifecycle Methods**:
  - `init()`: Initializes the servlet.
  - `service()`: Handles incoming requests (GET, POST, etc.) and generates responses.
  - `destroy()`: Cleans up resources before the servlet is destroyed.
- **Request-Response Model**:
  - Uses the `HTTPServletRequest` and `HTTPServletResponse` objects to handle client-server communication.
- **Annotations or Configurations**:
  - Can be configured in `web.xml` or using annotations like `@WebServlet`.
- **Purpose**:
  - Servlets are typically used for tasks like processing form data, managing session state, and dynamically generating web content.

## Servlet Container
A Servlet Container (or Web Container) is a component of a web server or application server that provides the runtime environment for servlets. Examples include Apache Tomcat, Jetty, and WildFly.

### Responsibilities:
- **Servlet Lifecycle Management**:
  - Manages the lifecycle of servlets (initialization, execution, and destruction).
- **Request Handling**:
  - Routes incoming HTTP requests to the appropriate servlet based on the URL mapping.
- **Multithreading**:
  - Handles multiple client requests simultaneously by creating threads for each request.
- **Session Management**:
  - Provides built-in mechanisms to handle sessions (e.g., cookies, URL rewriting).
- **JSP Support**:
  - Converts JavaServer Pages (JSP) into servlets for execution.
- **Security and Configuration**:
  - Handles authentication, authorization, and secure communication protocols (e.g., HTTPS).

# Explain Spring Boot Container

A Spring Boot container refers to the runtime environment where Spring Boot applications operate. It includes the following components and responsibilities:

### Dependency Injection (DI) Container:
- Manages the lifecycle and configuration of Spring beans (Java objects managed by Spring).
- Uses the Inversion of Control (IoC) principle to inject dependencies into components.

### Application Context:
- The heart of the Spring container.
- Manages bean creation, wiring, and lifecycle, along with resources like property files and message sources.

### Embedded Server Support:
- Spring Boot integrates with embedded servers like Tomcat, Jetty, or Undertow, allowing applications to run independently without requiring an external server setup.

### Auto-Configuration:
- Spring Boot simplifies configuration by automatically setting up beans and services based on dependencies in the classpath.

### Bean Scanning and Configuration:
- Scans for components annotated with `@Component`, `@Service`, `@Repository`, or `@Controller`.
- Configures beans using annotations like `@Configuration`, `@Bean`, and `@ComponentScan`.

### Environment Abstraction:
- Provides tools to access environment variables and properties for application configuration, supporting profiles like dev, prod, etc.

# Explain Bean Container

A Bean Container is a core component of the Spring Framework that manages Java objects (beans) and their dependencies. It provides a runtime environment for creating, configuring, and managing beans within a Spring application.

### Key Features of a Bean Container:
- **Dependency Injection (DI)**: Manages bean dependencies and injects them into other beans.
- **Inversion of Control (IoC)**: Allows beans to be configured and managed by the container, reducing tight coupling between components.
- **Lifecycle Management**: Handles bean lifecycle events like initialization and destruction.
- **Scoping**: Supports different bean scopes like singleton, prototype, request, session, etc.
- **Configuration**: Provides mechanisms for configuring beans using XML, JavaConfig, or annotations.
- **Bean Post-Processing**: Allows custom processing of beans before or after initialization.
- **Autowiring**: Automatically wires dependencies based on type, name, or qualifiers.
- **Bean Definition**: Defines bean metadata like class, scope, dependencies, and initialization methods.

### Bean Factory vs. Application Context:
- **Bean Factory**: The simplest container providing basic DI features.
- **Application Context**: A more advanced container that extends Bean Factory with additional features like event propagation, resource loading, and internationalization support.

### Types of Bean Containers:
- **ClassPathXmlApplicationContext**: Loads bean definitions from XML configuration files.
- **AnnotationConfigApplicationContext**: Loads bean definitions from JavaConfig classes annotated with `@Configuration`.
- **GenericWebApplicationContext**: Web-specific container for web applications.
- **WebApplicationContext**: Interface for web application contexts.

### Bean Scopes:
- **Singleton**: A single instance per container.
- **Prototype**: A new instance for each request.
- **Request**: A single instance per HTTP request.
- **Session**: A single instance per HTTP session.
- **Global Session**: A single instance per global HTTP session.

# What is Bean?

In Spring, a bean is an object that is managed by the Spring IoC container. Beans are created, configured, and managed by the container, allowing for loose coupling and easy dependency injection.

### Key Characteristics of Beans:
- **Java Objects**: Beans are regular Java objects managed by the Spring container.
- **Configuration Metadata**: Beans are defined in configuration files (XML, JavaConfig) or using annotations.
- **Lifecycle Management**: Beans can have lifecycle callbacks like initialization and destruction methods.
- **Dependency Injection**: Beans can have dependencies injected by the container.
- **Scoping**: Beans can have different scopes like singleton, prototype, request, session, etc.

### Types of Beans:
- **Singleton**: A single instance per container.
- **Prototype**: A new instance for each request.
- **Request**: A single instance per HTTP request.
- **Session**: A single instance per HTTP session.
- **Global Session**: A single instance per global HTTP session.

### Bean Definition:
A bean definition is a configuration metadata that defines how a bean should be created, configured, and managed by the container. It includes information like the bean's class, dependencies, scope, initialization methods, and destruction methods.