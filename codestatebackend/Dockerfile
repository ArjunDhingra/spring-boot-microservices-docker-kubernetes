# Start with a base image containing Java runtime
#FROM openjdk:8u212-jdk-slim
# Add Maintainer Info
#LABEL maintainer="savindi.narmada@gmail.com"
# Add a volume pointing to /tmp
#VOLUME /tmp
#ADD ./ app/
#WORKDIR /app
# Make port 8080 available to the world outside this container
#EXPOSE 9090
# The application's jar file (when packaged)
#COPY --from=build /app/target/codestatebackend-0.0.1-SNAPSHOT.jar codestatebackend.jar
#ARG JAR_FILE=target/codestatebackend-0.0.1-SNAPSHOT.jar
# Add the application's jar to the container
#ADD ${JAR_FILE} codestatebackend.jar
# Run the jar file 
#ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/codestatebackend.jar"]
#ENTRYPOINT ["java","-jar","codestatebackend.jar"]

FROM maven:3.6-jdk-8-alpine as build
ADD ./ app/
WORKDIR /app
RUN mvn install

FROM openjdk:8-jdk-alpine
COPY --from=build /app/target/codestatebackend-0.0.1-SNAPSHOT.jar codestatebackend.jar
EXPOSE 8081
ENTRYPOINT ["java","-jar","codestatebackend.jar"]