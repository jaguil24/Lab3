# Use a multi-stage build

# Build stage
FROM maven:3.8.4-jdk-11 AS build

WORKDIR /app

COPY pom.xml .
COPY src /app/src

RUN mvn clean install

# Stage 1
FROM openjdk:11-jre-slim

WORKDIR /app

# Copy the built WAR file from the previous build stage
COPY --from=build /app/target/comp367-webapp.war /app/comp367-webapp.war

# Expose port 8080 (or any port your app uses)
EXPOSE 8080

# Command to run the application
CMD ["java", "-jar", "/app/comp367-webapp.war"]
