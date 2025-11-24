#Copy the work enviroment & Build the maven project
FROM maven:3.8.5-openjdk-17 AS build
WORKDIR /myapp
COPY pom.xml ./
COPY src ./src
RUN mvn -B package --file pom.xml

#Run the compiled project
FROM openjdk:17.0.1-jdk-slim
ARG version
COPY --from=build target/myapp-$version.jar myapp-$version.jar
ENTRYPOINT ["java", "-jar", "myapp.jar"]
