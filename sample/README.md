
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



Docker File İlgili Komutlar:
```
FROM java:8 #Uygulamımızın Docker Hub kayıt servisinde bulunan java 8 image ile başlamaktadır. 

MAINTAINER Mustafa ERGAN <mustafaergan@blabla.com> #Uygulamayı geliştiren kişi ya da kişiler

RUN git clone https://github.com/mustafaergan/docker-springboot.git springdocker #Git aracı kodları çeker. RUN komutu image derleme sırasında tetikler ve farklı RUN komutları çalıştırabiliriz. Linuz komut dizine uygun RUN komuyları girilebilir.

WORKDIR springdocker #Kopyalanan projenin springdocker dizini altında atılır.

EXPOSE 8080 #docker container içeresinde hangi porta çalıştırılacağını bildiriyoruz. Burada 8080 portunda çalıştırılıyor.

CMD ["mvn","spring-boot:run"] # Uygulamanın hangi komutlar ve parametrelerle ayağa kaldıracağını bildiriyoruz.

ENTRYPOINT ["java","-jar","SpringDocker.jar"] #Uygulama java komutlarını tetikliyoruz.

```