# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.202.5/containers/debian/.devcontainer/base.Dockerfile

# [Choice] Debian version (use bullseye or stretch on local arm64/Apple Silicon): bullseye, buster, stretch
ARG VARIANT="buster"
FROM openjdk:8-jdk-${VARIANT} AS openjdk-8
FROM openjdk:11-jdk-${VARIANT} AS openjdk-11
FROM openjdk:17-jdk-${VARIANT} AS openjdk-17
FROM mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

COPY --from=openjdk-8 /usr/local/openjdk-8 /usr/local/openjdk-8
COPY --from=openjdk-11 /usr/local/openjdk-11 /usr/local/openjdk-11
COPY --from=openjdk-17 /usr/local/openjdk-17 /usr/local/openjdk-17

ENV JAVA_8_HOME="/usr/local/openjdk-8"
ENV JAVA_11_HOME="/usr/local/openjdk-11"
ENV JAVA_17_HOME="/usr/local/openjdk-17"
ENV JAVA_HOME="${JAVA_17_HOME}"
ENV PATH="${JAVA_HOME}/bin:${PATH}"

RUN apt-get update \
 && apt-get -y install \
        maven
