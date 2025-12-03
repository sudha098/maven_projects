# Build stage
FROM maven:3.6.3-jdk-11 AS build
WORKDIR /workspace
COPY pom.xml .
COPY src ./src
RUN mvn -B -DskipTests package

# Runtime stage
FROM openjdk:11.0.11-jre-slim
WORKDIR /app
COPY --from=build /workspace/target/maven-cicd-demo-1.0.0-jar-with-dependencies.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/app/app.jar"]
