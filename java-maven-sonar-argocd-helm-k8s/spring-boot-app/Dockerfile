# Build stage (uses JDK 17 + Maven to compile)
FROM maven:3.8.6-openjdk-17 AS builder

# Copy source and build (retains your artifact path logic)
WORKDIR /build
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

# Runtime stage (uses your original JRE config)
FROM adoptopenjdk/openjdk17:alpine-jre

# Preserve your exact original lines
ARG artifact=target/spring-boot-web.jar
WORKDIR /opt/app
COPY --from=builder /build/${artifact} app.jar

# Unchanged entrypoint
ENTRYPOINT ["java","-jar","app.jar"]
