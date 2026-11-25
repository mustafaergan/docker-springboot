# Spring Boot + Docker Örnekleri

Basit bir Spring Boot uygulamasını Docker imajına dönüştürmeyi gösteren iki küçük örnek.

> **Not:** Bu depo 2018 yılında eğitim/örnek amaçlı yazıldı ve artık güncellenmiyor. Bağımlılıkları ve temel Docker imajları eskidir ve bilinen güvenlik açıkları içerir; üretimde kullanmayın.

## İçerik

| Klasör | Ne yapar |
|---|---|
| `sample` | `/greeting` adresinde "Selam" dönen uygulama. Jar yerelde derlenir, `Dockerfile` hazır jar'ı `java:8` imajına kopyalar. Klasördeki README, Dockerfile komutlarını açıklar. |
| `github` | `/github` adresinde "Selam" dönen uygulama. Çok aşamalı `Dockerfile`: kodu GitHub'dan klonlar, `maven:3.5-jdk-8-alpine` ile derler ve `openjdk:8-jre-alpine` üzerinde çalıştırır. |

## Teknolojiler

- Java 8, Maven
- Spring Boot 2.0.5 (Web), H2
- Docker

## Çalıştırma

`sample`:

```bash
cd sample
mvn clean install
docker build -t springdocker .
docker run -p 8080:8080 springdocker
# http://localhost:8080/greeting
```

`github`:

```bash
cd github
docker build -t github-ornek .
docker run -p 8080:8080 github-ornek
# http://localhost:8080/github
```

`github/Dockerfile` derleme sırasında `settings.xml` adında bir Maven ayar dosyası bekler, ama bu dosya depoda
yoktur. Klasöre kendi `settings.xml` dosyanızı koyun ya da ihtiyacınız yoksa ilgili `ADD` satırını kaldırın.
