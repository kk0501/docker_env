FROM ubuntu:16.04
MAINTAINER luke<461025755@qq.com>

ENV MY_TZ=Asia/Shanghai
ENV TERM=xterm

RUN buildDeps='software-properties-common apt-utils locales tzdata' \
    && apt-get update \
    && apt-get -qq upgrade  -y \
    && apt-get install -y --fix-missing $buildDeps

RUN cp /usr/share/zoneinfo/$MY_TZ  /etc/localtime \
    && dpkg-reconfigure -f noninteractive tzdata \
    && rm -rf /etc/timezone && echo $MY_TZ >> /etc/timezone \
    && locale-gen en_US.UTF-8 zh_CN.UTF-8 \
    && localedef -i en_US -f UTF-8 en_US.UTF-8

ENV LC_ALL=en_US.UTF-8 \
    LANGUAGE=en_US.UTF-8 \
    LANG=en_US.UTF-8 

RUN echo 'export LC_ALL=en_US.UTF-8' >> ~/.bashrc \
    && echo 'export LANG=en_US.UTF-8' >> ~/.bashrc

RUN buildDeps='build-essential ca-certificates curl git vim rsyslog' \
    && apt-get install -y --fix-missing $buildDeps

RUN apt-get autoclean \
    && apt-get autoremove \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*