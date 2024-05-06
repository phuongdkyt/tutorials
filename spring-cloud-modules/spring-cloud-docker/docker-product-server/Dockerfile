FROM maven:3.8.3-openjdk-17 as appBuilder

# set working directory
WORKDIR /opt/app
# copy project files
COPY . .
# compile the source code and package it in a jar file
RUN mvn clean package -Dmaven.test.skip=true


FROM openjdk:17-jdk-alpine

WORKDIR /opt/app

COPY --from=appBuilder  /opt/app/target/*.jar /opt/app/app.jar

ENTRYPOINT ["java","-jar","/opt/app/app.jar"]
