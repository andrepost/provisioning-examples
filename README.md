# Custom layered docker images for Spring Boot applications
This repository contains examples for layered docker images built from Eclipse Temurin JDK 17

## Slim builder image
Used to extract an application. Only contains 3 Modules: java.base, jdk.jartool and jdk.zipfs


## Base slim jre
Used as a Base image to run Spring Boot applications. Contains required modules to run a Spring Boot application

## Application
Sample application Dockerfile that uses both previous docker images to create a layered application docker image