FROM jenkins/inbound-agent:alpine as jnlp

FROM maven:3.6.3-jdk-11-slim

LABEL org.opencontainers.image.authors="xbeeant"
LABEL org.opencontainers.image.version="1.0"
LABEL org.opencontainers.image.description="Jenkins k8s Maven 环境"

RUN apt-get update && \
    apt-get install -y \
        git \
        curl \
        libfontconfig1 \
        libfreetype6

COPY --from=jnlp /usr/local/bin/jenkins-agent /usr/local/bin/jenkins-agent
COPY --from=jnlp /usr/share/jenkins/agent.jar /usr/share/jenkins/agent.jar

ENTRYPOINT ["/usr/local/bin/jenkins-agent"]