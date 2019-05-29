FROM jenkinsci/jenkins:lts

MAINTAINER sshkim <sshkim88@gmail.com>

USER root

RUN set -ex \
    && curl -fsSL https://get.docker.com -o get-docker.sh \
    && sh get-docker.sh

RUN usermod -aG docker jenkins

USER jenkins
