FROM openjdk:11-jre

ENV SPRING_PROFILES_ACTIVE=docker,mysql

COPY ./target/*.jar /app.jar

EXPOSE 9090

HEALTHCHECK --interval=30s --timeout=10s --start-period=30s --retries=3 \
  CMD curl --fail http://localhost:8888/actuator/health || exit 1

ENTRYPOINT ["java", "-Djava.security.egd=file:/dev/./urandom", "-jar", "/app.jar"]
