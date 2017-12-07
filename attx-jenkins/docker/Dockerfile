FROM jenkins

MAINTAINER João M. da Silva <joao.silva@helsinki.fi>

USER root

RUN apt-get update \
    && apt-get install -y apt-utils \
    && apt-get install -y sudo \
    && apt-get install -y libxml2-dev libxslt1-dev \
    && apt-get install -y python-setuptools python-dev \
    && apt-get install -y build-essential \
    && apt-get install -y zlib1g-dev \
    && apt-get install -y maven \
    && curl -sL https://deb.nodesource.com/setup_7.x | bash - \
    && apt-get install -y nodejs \
    && apt-get clean

RUN easy_install pip \
    && pip install ontospy

RUN git config --global user.email "attxproject@gmail.com" \
    && git config --global user.name "attx github"

RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers
