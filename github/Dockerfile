FROM alpine/git as clone
WORKDIR /app
#ENV http_proxy
#ENV https_proxy
RUN git clone https://github.com/mustafaergan/docker-springboot.git

FROM maven:3.5-jdk-8-alpine as build
WORKDIR /app
COPY --from=clone /app/docker-springboot/github /app
ADD settings.xml /root/.m2/settings.xml
RUN mvn install

FROM openjdk:8-jre-alpine
WORKDIR /app
COPY --from=build /app/target/github.jar /app
EXPOSE 8080
ENTRYPOINT ["java","-jar","github.jar"]