# Build argument for Java version

# Stage 1: Build the application
FROM maven:3.9.9-eclipse-temurin-23 AS builder
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package

# Stage 2: Run the application
FROM eclipse-temurin:23-jre
WORKDIR /app
COPY --from=builder /app/target/product-service.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
