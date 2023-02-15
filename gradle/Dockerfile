FROM jenkins/inbound-agent:alpine as jnlp

FROM gradle:jdk11-alpine

LABEL org.opencontainers.image.authors="xbeeant"
LABEL org.opencontainers.image.version="1.0"
LABEL org.opencontainers.image.description="Jenkins k8s Gradle 环境"

RUN apk -U add \
        git \
        curl 

COPY --from=jnlp /usr/local/bin/jenkins-agent /usr/local/bin/jenkins-agent
COPY --from=jnlp /usr/share/jenkins/agent.jar /usr/share/jenkins/agent.jar

ENTRYPOINT ["/usr/local/bin/jenkins-agent"]