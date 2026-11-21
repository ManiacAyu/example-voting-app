FROM maniacayu/worker-base:latest AS build

WORKDIR /code

COPY . .

RUN mvn package -D skipTests

FROM eclipse-temurin:8-jre-jammy AS runtime

WORKDIR /run

COPY --from=build /code/target/worker-jar-with-dependencies.jar worker.jar

CMD java -jar worker.jar
