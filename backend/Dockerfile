# Build stage
FROM maven:3.9-openjdk-17 AS build

WORKDIR /app

COPY pom.xml .
COPY src ./src

RUN mvn clean package -DskipTests

# Runtime stage
FROM openjdk:17-jdk-slim

WORKDIR /app

COPY --from=build /app/target/expense-tracker-0.0.1-SNAPSHOT.jar .

EXPOSE 8080

CMD ["java", "-jar", "expense-tracker-0.0.1-SNAPSHOT.jar"]