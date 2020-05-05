FROM maven:3.6-openjdk-8

WORKDIR /usr/src/app

COPY . .

RUN mvn clean install -Dmaven.test.skip=true

EXPOSE 8080

CMD ["java", "-jar", "target/spring-boot-mysql-0.0.1-SNAPSHOT.jar"]