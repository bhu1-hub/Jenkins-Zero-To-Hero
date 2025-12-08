# Jenkins build agent base: Maven + JDK 17 + Docker CLI
FROM maven:3.9.6-eclipse-temurin-17

USER root

# Install Docker CLI (if you really need it in this image)
RUN apt-get update && \
    apt-get install -y docker.io && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /app

# Copy pom and download dependencies
COPY pom.xml .
RUN mvn dependency:go-offline

# Copy source code
COPY src ./src

# Build the Spring Boot JAR
RUN mvn clean package -DskipTests

# Expose Spring Boot port
EXPOSE 8080

# 👇 IMPORTANT: use the JAR name from <finalName> in pom.xml
CMD ["java", "-jar", "target/spring-boot-web.jar"]
