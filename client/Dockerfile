FROM ubuntu:latest
LABEL authors="elmehdinidazi"

# Stage 1: Build the application
#FROM maven:3.8.4-openjdk-17 AS builder
WORKDIR /app
COPY ./src ./src
COPY ./pom.xml .
RUN mvn clean package

# Stage 2: Create the final image
FROM openjdk:17-jdk-alpine
VOLUME /tmp
ARG JAR_FILE=target/*.jar
COPY --from=builder /app/${JAR_FILE} client-service.jar
ENTRYPOINT ["java", "-jar", "/app.jar"]
