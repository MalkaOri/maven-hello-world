#Stage 1 : Import the work enviroment & update the project version RUN echo" Stage 1 : Import the work enviroment & update the project version "
FROM maven:3.8.5-openjdk-17 AS build
WORKDIR /myapp
COPY pom.xml ./
COPY src ./src
ARG version
RUN mvn versions:set -DnewVersion=$version

#Stage 2: Compile the projectRUN echo "Compile the project"
RUN mvn -B package --file pom.xml

#Stage 3: Run the compiled projectRUN echo "Run the compiled project"
RUN echo $version
FROM openjdk:17.0.1-jdk-slim
COPY --from=build target/myapp-$version.jar myapp-$version.jar
ENTRYPOINT ["java", "-jar", "myapp.jar"]
