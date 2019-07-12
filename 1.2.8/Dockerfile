FROM openjdk:8-alpine

LABEL maintainer="Bogdan Snisar <bogdan.sns@gmail.com>"

ENV SBT_VERSION 1.2.8
ENV SBT_HOME /usr/local/sbt
ENV SBT_CACHE /usr/var/sbt-cache

ENV PATH ${PATH}:${SBT_HOME}/bin
ENV SBT_OPTS "-Dsbt.global.base=${SBT_CACHE}/.sbtboot -Dsbt.boot.directory=${SBT_CACHE}/.boot -Dsbt.ivy.home=${SBT_CACHE}/.ivy"


RUN apk update && \
    apk add --no-cache bash git openssh curl tar gzip && \
    curl -sL "https://piccolo.link/sbt-$SBT_VERSION.tgz" | gunzip | tar -x -C /usr/local && echo -ne "- with sbt $SBT_VERSION\n" >> /root/.built && \
    ln -s /usr/local/sbt-launcher-packaging-$SBT_VERSION/bin/sbt /usr/local/bin/sbt && \
    sbt sbtVersion
