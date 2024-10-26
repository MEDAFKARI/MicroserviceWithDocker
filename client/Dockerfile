# Build stage
FROM maven:3.8.4-openjdk-17 AS builder
WORKDIR /app
COPY ./src ./src
COPY ./pom.xml .
RUN mvn clean package

# Run stage
FROM openjdk:17-jdk-alpine
WORKDIR /app
VOLUME /tmp
ARG JAR_FILE=target/*.jar
COPY --from=builder /app/${JAR_FILE} client-service.jar
ENTRYPOINT ["java", "-jar", "/app/client-service.jar"]
