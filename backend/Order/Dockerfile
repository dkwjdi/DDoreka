FROM openjdk:8-jdk-alpine AS builder
COPY gradlew .
COPY gradle gradle
COPY build.gradle .
COPY settings.gradle .
COPY src src
RUN chmod +x ./gradlew
RUN ./gradlew bootJar

FROM openjdk:8-jdk-alpine
COPY --from=builder build/libs/*.jar app.jar

EXPOSE 8084
ENTRYPOINT ["java","-jar","/app.jar"]
