## Spring Boot Interview Questions and Answers

### 1. What is Spring Boot?
Spring Boot is an open-source Java-based framework used to create stand-alone, production-grade Spring-based applications with minimal configuration. It simplifies the development process by providing defaults for code and annotation configuration.

### 2. What are the key features of Spring Boot?
- **Auto-Configuration**: Automatically configures Spring application based on the dependencies present in the classpath.
- **Standalone**: Creates stand-alone applications that can run independently without requiring an external application server.
- **Production-Ready**: Provides production-ready features such as metrics, health checks, and externalized configuration.
- **Spring Initializer**: A web-based tool to generate Spring Boot projects quickly.
- **Embedded Servers**: Supports embedded servers like Tomcat, Jetty, and Undertow.

### 3. What is the purpose of the `@SpringBootApplication` annotation?
The `@SpringBootApplication` annotation is a convenience annotation that combines `@Configuration`, `@EnableAutoConfiguration`, and `@ComponentScan` annotations. It enables auto-configuration and component scanning in a Spring Boot application.

### 4. How does Spring Boot achieve auto-configuration?
Spring Boot achieves auto-configuration by using the `@EnableAutoConfiguration` annotation and various `spring.factories` files. It scans the classpath and automatically configures beans based on the dependencies present.

### 5. What is Spring Boot Starter?
Spring Boot Starters are a set of convenient dependency descriptors that you can include in your application. They provide a ready-to-use set of dependencies for various functionalities like web, data access, security, etc. For example, `spring-boot-starter-web` includes dependencies for building web applications.

### 6. How do you create a Spring Boot application?
You can create a Spring Boot application using Spring Initializer (a web-based tool), Spring Boot CLI, or manually by adding the necessary dependencies to your `pom.xml` or `build.gradle` file and creating a main class with the `@SpringBootApplication` annotation.

### 7. What is the Spring Boot Actuator?
Spring Boot Actuator is a sub-project of Spring Boot that provides production-ready features to help monitor and manage applications. It includes endpoints for health checks, metrics, info, environment, and more.

### 8. How do you externalize configuration in Spring Boot?
Spring Boot allows you to externalize configuration using properties files (`application.properties` or `application.yml`), environment variables, command-line arguments, and more. This helps in separating configuration from code and makes it easier to manage different environments.

### 9. What is the use of `application.properties` file in Spring Boot?
The `application.properties` file is used to define configuration properties for a Spring Boot application. It allows you to customize various settings such as server port, database connection, logging, and more.

### 10. How do you handle exceptions in Spring Boot?
You can handle exceptions in Spring Boot using `@ControllerAdvice` and `@ExceptionHandler` annotations. `@ControllerAdvice` is used to define a global exception handler, while `@ExceptionHandler` is used to handle specific exceptions in a controller.

### 11. What is Spring Boot DevTools?
Spring Boot DevTools is a set of tools that can help improve the development experience. It includes features like automatic restarts, live reload, and configurations for enhanced development.

### 12. How do you enable hot swapping in Spring Boot?
You can enable hot swapping in Spring Boot by including the `spring-boot-devtools` dependency in your project. This enables automatic restarts and live reloads when changes are made to the code.

### 13. What is the difference between `@RestController` and `@Controller` in Spring Boot?
`@RestController` is a convenience annotation that combines `@Controller` and `@ResponseBody`. It is used to create RESTful web services and automatically serializes return objects to JSON or XML. `@Controller` is used to define a standard web controller and requires `@ResponseBody` on each method to serialize return objects.

### 14. How do you configure a datasource in Spring Boot?
You can configure a datasource in Spring Boot by defining properties in the `application.properties` or `application.yml` file. For example, you can set properties like `spring.datasource.url`, `spring.datasource.username`, and `spring.datasource.password`.

### 15. What is Spring Boot CLI?
Spring Boot CLI is a command-line tool that allows you to quickly create and run Spring Boot applications. It uses Groovy scripts to build applications and provides commands for managing dependencies, running applications, and more.

### 16. How do you secure a Spring Boot application?
You can secure a Spring Boot application using Spring Security. By including the `spring-boot-starter-security` dependency, you can configure security settings such as authentication, authorization, and protection against common vulnerabilities.

### 17. What is the purpose of `@SpringBootTest` annotation?
The `@SpringBootTest` annotation is used to create an application context for integration tests. It loads the full application context and allows you to test the application as a whole, including its interactions with other components.

### 18. How do you monitor a Spring Boot application?
You can monitor a Spring Boot application using Spring Boot Actuator, which provides various endpoints for health checks, metrics, and other monitoring information. Additionally, you can integrate with external monitoring tools like Prometheus, Grafana, and ELK stack.

### 19. What is the difference between `@Component`, `@Service`, `@Repository`, and `@Controller`?
`@Component` is a generic stereotype annotation for any Spring-managed component. `@Service` is a specialization of `@Component` for service layer components. `@Repository` is a specialization of `@Component` for data access components and provides additional persistence exception translation. `@Controller` is a specialization of `@Component` for web controllers.

### 20. How do you handle application properties for different environments in Spring Boot?
You can handle application properties for different environments in Spring Boot by using profile-specific properties files (e.g., `application-dev.properties`, `application-prod.properties`). You can activate a specific profile using the `spring.profiles.active` property.

### 21. How do you customize the Spring Boot banner?
You can customize the Spring Boot banner by placing a `banner.txt` file in the `src/main/resources` directory. You can also use `banner.location` property to specify a custom location for the banner file. Additionally, you can programmatically set the banner using the `SpringApplication.setBanner()` method.

### 22. What is the use of `@Conditional` annotations in Spring Boot?
`@Conditional` annotations are used to conditionally enable or disable beans based on certain conditions. Spring Boot provides several conditional annotations like `@ConditionalOnProperty`, `@ConditionalOnClass`, `@ConditionalOnMissingBean`, etc., to control bean creation based on the presence of properties, classes, or other conditions.

### 23. How do you create a custom starter in Spring Boot?
To create a custom starter in Spring Boot, you need to create a new Maven or Gradle project and include the necessary dependencies. You should also provide an `auto-configuration` class annotated with `@Configuration` and `@EnableAutoConfiguration`. Finally, you need to create a `spring.factories` file under `META-INF` directory to register your auto-configuration class.

### 24. How do you implement caching in Spring Boot?
You can implement caching in Spring Boot by including the `spring-boot-starter-cache` dependency and enabling caching using the `@EnableCaching` annotation. You can then use annotations like `@Cacheable`, `@CachePut`, and `@CacheEvict` to manage caching behavior on methods.

### 25. How do you configure logging in Spring Boot?
Spring Boot uses `Logback` as the default logging framework. You can configure logging by creating a `logback-spring.xml` or `logback.xml` file in the `src/main/resources` directory. You can also configure logging properties in the `application.properties` file using properties like `logging.level`, `logging.file`, and `logging.pattern`.

### 26. What is the purpose of `@SpringBootConfiguration` annotation?
The `@SpringBootConfiguration` annotation is a specialized form of the `@Configuration` annotation. It indicates that the class provides Spring Boot application configuration. It is typically used in combination with `@EnableAutoConfiguration` and `@ComponentScan` to create a Spring Boot application.

### 27. How do you create a custom health indicator in Spring Boot?
You can create a custom health indicator in Spring Boot by implementing the `HealthIndicator` interface and overriding the `health()` method. You can then register your custom health indicator as a Spring bean.

### 28. How do you use profiles in Spring Boot?
Profiles in Spring Boot are used to segregate parts of your application configuration and make it available only in certain environments. You can use the `@Profile` annotation to mark beans that should be included or excluded based on the active profile. You can activate profiles using the `spring.profiles.active` property in the `application.properties` file or as a command-line argument.

### 29. How do you handle circular dependencies in Spring Boot?
Circular dependencies in Spring Boot can be handled by using the `@Lazy` annotation to delay the initialization of one of the beans involved in the circular dependency. Alternatively, you can refactor your code to eliminate the circular dependency by breaking the dependency chain.

### 30. How do you configure multiple data sources in Spring Boot?
To configure multiple data sources in Spring Boot, you need to define multiple `DataSource` beans and mark one of them as the primary data source using the `@Primary` annotation. You also need to configure `EntityManagerFactory` and `TransactionManager` beans for each data source.

### 31. How do you handle multi-threading in Spring Boot?
You can handle multi-threading in Spring Boot by using the `@Async` annotation on methods that should run asynchronously. You also need to enable asynchronous processing by adding the `@EnableAsync` annotation to a configuration class.

### 32. How do you configure a thread pool in Spring Boot?
You can configure a thread pool in Spring Boot by defining a `ThreadPoolTaskExecutor` bean. You can set properties like core pool size, max pool size, and queue capacity to customize the thread pool.

### 33. What is the purpose of `@Scheduled` annotation in Spring Boot?
The `@Scheduled` annotation is used to schedule tasks to run at fixed intervals or cron expressions. You need to enable scheduling by adding the `@EnableScheduling` annotation to a configuration class.

### 34. How do you handle concurrency in Spring Boot?
You can handle concurrency in Spring Boot by using synchronization mechanisms provided by Java, such as `synchronized` blocks, `ReentrantLock`, and `Semaphore`. Additionally, you can use Spring's `@Transactional` annotation to manage concurrent access to database resources.

### 35. How do you implement a scheduled task in Spring Boot?
You can implement a scheduled task in Spring Boot by creating a method annotated with `@Scheduled` and specifying the fixed rate or cron expression. You also need to enable scheduling by adding the `@EnableScheduling` annotation to a configuration class.

### 36. How do you handle exceptions in asynchronous methods in Spring Boot?
You can handle exceptions in asynchronous methods in Spring Boot by using a custom `AsyncUncaughtExceptionHandler`. You need to implement the `AsyncConfigurer` interface and override the `getAsyncUncaughtExceptionHandler` method to provide your custom exception handler.

### 37. How do you use `CompletableFuture` in Spring Boot?
You can use `CompletableFuture` in Spring Boot to handle asynchronous computations. You can return a `CompletableFuture` from a method annotated with `@Async` and use methods like `thenApply`, `thenAccept`, and `thenCombine` to compose asynchronous tasks.

### 38. How do you monitor thread pool usage in Spring Boot?
You can monitor thread pool usage in Spring Boot by exposing metrics using Spring Boot Actuator. You can create custom metrics for thread pool usage and expose them through Actuator endpoints.

### 39. How do you ensure thread safety in Spring Boot applications?
You can ensure thread safety in Spring Boot applications by using thread-safe data structures, avoiding shared mutable state, and using synchronization mechanisms like `synchronized` blocks, `ReentrantLock`, and `Atomic` classes.

### 40. How do you handle long-running tasks in Spring Boot?
You can handle long-running tasks in Spring Boot by running them asynchronously using the `@Async` annotation or scheduling them using the `@Scheduled` annotation. You can also use message queues like RabbitMQ or Kafka to offload long-running tasks to separate worker processes.
