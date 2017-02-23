# development-environment
ATTX development environment

Running multiple compose files on the same network:
```
docker-compose -f build/docker-compose.yml -f attx-jenkins/build/docker-compose.yml -f pivy-repo/build up
```
