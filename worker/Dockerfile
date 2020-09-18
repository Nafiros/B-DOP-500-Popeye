FROM maven:3.5-jdk-8-alpine as builder
WORKDIR /my/builder
COPY . /my/builder

RUN mvn dependency:resolve
RUN mvn package 



FROM openjdk:8-jre-alpine
COPY --from=builder /my/builder/target/worker-jar-with-dependencies.jar /java-binks-jar.jar

CMD ["java", "-jar", "/java-binks-jar.jar"]