FROM custom-slim-builder as  builder

WORKDIR /build

COPY app.jar ./

RUN java -Djarmode=layertools -jar app.jar extract

FROM  custom-slim-jre

WORKDIR /app

COPY --from=builder /build/dependencies/ ./
COPY --from=builder /build/snapshot-dependencies/ ./
COPY --from=builder /build/spring-boot-loader/ ./
COPY --from=builder /build/application/ ./

EXPOSE 8080

CMD ["java", "org.springframework.boot.loader.JarLauncher"]

RUN addgroup -S app && adduser -S -G app app

USER app