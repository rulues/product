# Usa una imagen base de OpenJDK 17
FROM eclipse-temurin:17-alpine

#Crea un nuevo grupo con un uio y non root user llamado admin
RUN addgroup -g 1028 devopsc \ 
    && adduser -D -G devopsc admin
WORKDIR /product-app
VOLUME /product-app

# Copiamos el jar a la imagen
ARG JAR_FILE
ARG ARG DB_PASSWORD
COPY ${JAR_FILE} /product-app/app.jar

ENV DB_PASSWORD=$DB_PASSWORD

#Cambia el propietario de directorio /app para que use el admin
RUN chown -R admin:devopsc /product-app

# Indicamos que de aqui en adelante se usara este usuario para ejecutar 
USER admin

# Define el comando para ejecutar la aplicación
ENTRYPOINT ["java", "-jar", "/product-app/app.jar"]
