FROM jenkins

MAINTAINER João M. da Silva <joao.silva@helsinki.fi>

USER root

RUN apt-get update \
    &&  apt-get install -y apt-utils \
    && apt-get install -y sudo \
    && apt-get install -y libxml2-dev libxslt1-dev python-dev \
    && apt-get install -y build-essential \
    && apt-get install -y zlib1g-dev \
    && apt-get install -y maven \
    && apt-get clean

RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers
