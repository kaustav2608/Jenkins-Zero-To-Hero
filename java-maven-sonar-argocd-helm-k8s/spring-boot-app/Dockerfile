# Use the official Eclipse Temurin base image for Java 17
FROM eclipse-temurin:17-jre-alpine

# Define the artifact path
ARG artifact=target/spring-boot-web.jar

# Set working directory inside the container
WORKDIR /opt/app

# Copy the built Spring Boot JAR file into the container
COPY ${artifact} app.jar

# Run the Spring Boot application
ENTRYPOINT ["java", "-jar", "app.jar"]

