# syntax = docker/dockerfile:1.3
FROM maven:3.8.4-openjdk-8-slim as build
WORKDIR /code
COPY ./gs-accessing-data-mysql/complete/pom.xml .
RUN --mount=type=cache,target=/root/.m2/repository mvn dependency:go-offline
COPY ./gs-accessing-data-mysql/complete/. .
RUN --mount=type=cache,target=/root/.m2/repository mvn clean package
RUN mv ./target/*.jar ./target/app.jar
#RUN --mount=type=cache,target=/root/.m2/repository mvn package

FROM openjdk:8-jre-alpine as runner 
WORKDIR /code
COPY --from=build /code/target/app.jar .
CMD [ "java","-jar","app.jar" ]




####### syntax = docker/dockerfile:1.3
######FROM maven:3.8.4-openjdk-8-slim as build
######WORKDIR /code
######COPY pom.xml .
######RUN --mount=type=cache,target=/root/.m2/repository mvn dependency:go-offline -B
######COPY ./src .
######RUN --mount=type=cache,target=/root/.m2 mvn clean package 
######RUN mv ./target/*.jar ./target/app.jar
######## java -classpath . com.example.accessingdatamysql.AccessingDataMysqlApplication
######FROM openjdk:8-jre-alpine as runtime
######WORKDIR /code
######COPY --from=build /code/target/app.jar .
######CMD [ "java","-jar","app.jar"]

#CMD ["java", "-jar", "cfve","app.jar","AccessingDataMysqlApplication","*.class"]