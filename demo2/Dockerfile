# Builder
FROM maven:3.6.3-openjdk-15 AS build

WORKDIR /app
COPY . .
RUN mvn compile \
  && mvn package

WORKDIR /app/target

# Production stage
FROM mcr.microsoft.com/java/jre-headless:11-zulu-alpine as prod
EXPOSE 8080

WORKDIR /app
COPY --from=build /app/target/demo-0.0.1-SNAPSHOT.jar /app

CMD ["java", "-jar", "demo-0.0.1-SNAPSHOT.jar"]
