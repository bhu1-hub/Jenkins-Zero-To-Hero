# Jenkins build agent base: Maven + JDK 17 + Docker CLI
FROM maven:3.9.6-eclipse-temurin-17

USER root

# Install Docker CLI
RUN apt-get update && \
    apt-get install -y docker.io && \
    rm -rf /var/lib/apt/lists/*
