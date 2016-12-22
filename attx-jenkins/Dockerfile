FROM jenkins

MAINTAINER João M. da Silva <joao.silva@helsinki.fi>

USER root
RUN apt-get update \
      && apt-get install -y sudo \
      && apt-get install -y libxml2-dev libxslt1-dev python-dev \
      && apt-get install -y build-essential \
      && apt-get install -y zlib1g-dev \
      && rm -rf /var/lib/apt/lists/*

RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers
