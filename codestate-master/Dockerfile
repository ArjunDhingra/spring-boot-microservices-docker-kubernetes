FROM maven:3.6-jdk-8-alpine as build
ADD ./ app/
WORKDIR /app
#RUN mvn install
RUN mvn clean package
# Start with a base image containing Java runtime
FROM openjdk:8u212-jdk-slim

# Add Maintainer Info
LABEL maintainer="savindi.narmada@gmail.com"

# Add a volume pointing to /tmp
VOLUME /tmp

RUN mvn clean package

# Make port 8080 available to the world outside this container
EXPOSE 8080

# The application's jar file
ARG JAR_FILE=target/codestate-0.0.1-SNAPSHOT.jar

# Add the application's jar to the container
ADD ${JAR_FILE} codestate.jar

# Run the jar file 
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/codestate.jar"]
