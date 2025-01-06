# Dockrise Spring Boot App using Dockerfile

## Generate fat jar

```bash
mvn clean install
```

## Dockerfile

```dockerfile
FROM openjdk:17-jdk-slim

COPY target/dockrise-spring-boot-app-0.0.1-SNAPSHOT.jar dockrise-spring-boot-app-0.0.1-SNAPSHOT.jar

ENTRYPOINT ["java", "-jar", "dockrise-spring-boot-app-0.0.1-SNAPSHOT.jar"]
```

## Build Docker image

```bash
docker build -t dockrise-spring-boot-app .
```

## Run Docker container

```bash
docker run -d -p 8080:8080 dockrise-spring-boot-app
```

# Dockrise Spring Boot App using Buildpacks

This allows you to build a Docker image without a Dockerfile, and following the best practice.

## Check pom.xml

Make sure the `spring-boot-maven-plugin` is included in the `pom.xml` file.

```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
        </plugin>
    </plugins>
</build>
```

Make sure to configure image URI in the `pom.xml` file.

```xml
<configuration>
    <image>
        <name>
            <!-- <dockerUserName/${project.artifactId}:s4> -->
        </name>
    </image>
</configuration>
```

## Build Docker image using Buildpacks

```bash
mvn spring-boot:build-image
```

# Push Docker image to Docker Hub

```bash
docker push docker.io/<dockerUserName/${project.artifactId}:s4>
```
