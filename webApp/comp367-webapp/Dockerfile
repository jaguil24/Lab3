# Use an official Maven image to build the project
FROM maven:3.8.4-jdk-11 as build

# Set the working directory in the container
WORKDIR /app

# Copy the pom.xml and source code
COPY pom.xml .
COPY src /app/src

# Build the project using Maven
RUN mvn clean install

# Use an openjdk image to run the application
FROM openjdk:11-jre-slim

# Set the working directory in the container
WORKDIR /app

# Copy the built JAR file from the previous build stage
COPY --from=build /app/target/your-webapp.jar /app/your-webapp.jar

# Expose port 8080 (or any port your app uses)
EXPOSE 8080

# Command to run the app
CMD ["java", "-jar", "your-webapp.jar"]
