FROM openjdk:17.0.1-jdk-slim
WORKDIR /target
ARG version
COPY target/myapp-$version.jar myapp-$version.jar
ENTRYPOINT ["java", "-jar", "myapp.jar"]
