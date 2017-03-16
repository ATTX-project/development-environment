# README

Here you can find an example docker-compose.yml of our development environment implementation. We hope it makes it easier easier for sysdamins, testers, and developers to try it out how we have integrated Jenkins (https://jenkins.io/), Archiva (https://archiva.apache.org/index.cgi), and PiPy (https://pypi.python.org/pypi) into a CI system. 

## Prerequisites

Having Docker Compose installed, please check the instructions  ə https://docs.docker.com/compose/install/

## Deployment

Download the example docker-compose.yml and run

`docker-compose up -f docker-compose.yml`

You should then have three images running, for example:

```
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS              PORTS                                                             NAMES
49cacea98f82        attxproject/attx-jenkins:latest   "/bin/tini -- /usr..."   About an hour ago   Up About an hour    50000/tcp, 0.0.0.0:49001->8080/tcp                                attxdev_attx-jenkins_1
4641bb0a1281        attx-dev:5000/pypirepo:latest     "/bin/sh -c 'nginx..."   About an hour ago   Up About an hour    80/tcp, 0.0.0.0:5039->5039/tcp, 443/tcp, 0.0.0.0:5639->5639/tcp   attxdev_pypirepo_1
dcdf1ca95973        xetusoss/archiva:latest           "/run.bash"              About an hour ago   Up About an hour    8443/tcp, 0.0.0.0:8081->8080/tcp                                  attxdev_archiva_1
```

Jenkins webui can then be accessed at <127.0.0.1:49001>, PyPi at <127.0.0.1:5039> and <127.0.0.1:5639>, and Archiva at <127.0.0.1:8081>
