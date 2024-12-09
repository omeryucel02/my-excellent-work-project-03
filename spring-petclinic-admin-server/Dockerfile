FROM openjdk:11-jre

# Uygulamanın çalıştırma ortamı profillerini ayarla
ENV SPRING_PROFILES_ACTIVE=docker,mysql

# Jar dosyasını container'a kopyala
COPY ./target/*.jar /app.jar

# Container'ın expose edeceği port
EXPOSE 9090

# Uygulamanın sağlık kontrolünü yapacak HEALTHCHECK talimatı
HEALTHCHECK --interval=30s --timeout=10s --start-period=30s --retries=3 \
  CMD curl --fail http://localhost:9090/actuator/health || exit 1

# Uygulamayı başlat
ENTRYPOINT ["java", "-Djava.security.egd=file:/dev/./urandom", "-jar", "/app.jar"]