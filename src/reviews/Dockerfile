FROM gradle:7.3.1-jdk11 AS build
COPY --chown=gradle:gradle reviews-application /home/gradle/src
WORKDIR /home/gradle/src
RUN gradle build --no-daemon

FROM tomcat:8-jdk11-openjdk-slim-buster

EXPOSE 8080

RUN mkdir /app

COPY --from=build /home/gradle/src/build/libs/*.war /usr/local/tomcat/webapps/
