FROM ubuntu
#Install necessary packages
RUN apt-get update && apt-get install -y 
RUN apt install openjdk-17-jre-headless -y
RUN apt install maven -y

#set the working directory
WORKDIR /app

#Copy source files and pom.xml to the working directory
COPY ./src /app/src
COPY pom.xml /app

#Build the application using Maven
RUN mvn -f /app/pom.xml clean package -DskipTests

#copy the built jar file to the container.
COPY ./target/*.jar /app/app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/app/app.jar"]

# FROM eclipse-temurin:25
# RUN mkdir /opt/app
# COPY japp.jar /opt/app
# CMD ["java", "-jar", "/opt/app/japp.jar"]