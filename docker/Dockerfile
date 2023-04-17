# Stage 1: Clone the repository to an alpine image
FROM alpine/git as repo
RUN git clone https://github.com/xi3161-sregoti/java-web-server /repo

# Stage 2: Build the application and generate a jar executable
FROM openjdk:17-alpine as builder
COPY --from=repo /repo /app
ENV CONN=""
WORKDIR /app
RUN ./mvnw clean package
RUN cp target/rest-service-complete-0.0.1-SNAPSHOT.jar /app.jar

# Stage 3: Run the application using the jar executable
FROM openjdk:17-alpine
COPY --from=builder /app.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]