FROM maven AS build 

COPY . .

RUN mvn clean package -DskipTests


FROM openjdk:17-oracle


COPY --from=build ./target/user-service*.jar user-service.jar

CMD ["java","-jar","user-service.jar"]
