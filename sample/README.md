
Docker File:

```
FROM java:8
EXPOSE 8080
ADD /target/SpringDocker.jar SpringDocker.jar
ENTRYPOINT ["java","-jar","SpringDocker.jar"]
```

mvn clean compile install

docker build -f Dockerfile -t springdocker .

docker images

docker run -p 8080:8080 springdocker

docker-machine ls


