# Etapa 1: Compilar o projeto
FROM eclipse-temurin:23-jdk AS build

WORKDIR /app

COPY . .

RUN chmod +x mvnw && ./mvnw clean package -DskipTests

# Etapa 2: Executar a aplicação
FROM eclipse-temurin:23-jre

WORKDIR /app

COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]