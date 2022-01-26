# syntax = docker/dockerfile:1.3
FROM maven:3.8.4-openjdk-8-slim as build
WORKDIR /code
COPY ./gs-rest-service/complete/pom.xml .
RUN --mount=type=cache,target=/root/.m2/repository mvn dependency:go-offline -B
COPY ./gs-rest-service/complete/ .
RUN --mount=type=cache,target=/root/.m2/repository mvn package

FROM openjdk:8-jre-alpine
WORKDIR /code
COPY --from=build /code/target/rest-service-complete-0.0.1-SNAPSHOT.jar .
CMD [ "java","-jar","rest-service-complete-0.0.1-SNAPSHOT.jar" ]