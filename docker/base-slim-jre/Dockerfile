FROM eclipse-temurin:17-jdk-alpine as builder

WORKDIR /build

COPY modules.info ./

RUN jlink \
    --verbose \
    --compress 2 \
    --strip-java-debug-attributes \
    --no-header-files \
    --no-man-pages \
    --output jre \
    --add-modules $(cat modules.info)

FROM alpine:latest

WORKDIR /app

COPY --from=builder /build/jre/ ./jre

ENV JAVA_HOME /app/jre
ENV PATH $PATH:$JAVA_HOME/bin
