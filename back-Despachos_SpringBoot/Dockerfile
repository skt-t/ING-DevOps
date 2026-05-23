# ==========================================
# Etapa 1: Construcción (Build)
# ==========================================
FROM maven:3.9.6-eclipse-temurin-17 AS builder
WORKDIR /app

# Copiamos primero el pom.xml para descargar dependencias
# Esto optimiza el caché de Docker y acelera futuros builds
COPY pom.xml .
RUN mvn dependency:go-offline -B

# Copiamos el código fuente y compilamos
COPY src ./src
# Usamos -DskipTests porque las pruebas las ejecutará GitHub Actions, no el Dockerfile
RUN mvn clean package -DskipTests

# ==========================================
# Etapa 2: Ejecución (Producción)
# ==========================================
FROM eclipse-temurin:17-jre-alpine
WORKDIR /app

# Copiamos solo el .jar compilado desde la etapa anterior
COPY --from=builder /app/target/*.jar app.jar

# Exponemos el puerto estándar de Spring Boot
EXPOSE 8080

# Comando para ejecutar la aplicación
ENTRYPOINT ["java", "-jar", "app.jar"]
