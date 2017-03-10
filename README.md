# development-environment
ATTX development environment

Latest version of docker-compose required (e.g. 1.11.2).

The default behaviour is to always pull the latest images and to remove them by doing the commad `gradle removeImages`.

Running with docker-compose:
* `gradle createComposeFile` in the root directory - this will create compose files for archiva, jenkins and pivy-repo
* `docker-compose -f build/docker-compose.yml -f attx-jenkins/build/docker-compose.yml -f pivy-repo/build up` - Running multiple compose files on the same network
* stop with `docker-compose -f build/docker-compose.yml -f attx-jenkins/build/docker-compose.yml -f pivy-repo/build stop`
* clean with `docker-compose -f build/docker-compose.yml -f attx-jenkins/build/docker-compose.yml -f pivy-repo/build rm`
* `gradle removeImages` in the root directory - to clean and remove the images

Running with gradle:
* `gradle startContainers` in the root directory - to start the network
* `gradle stopContainers` in the root directory - to stop the network
* `gradle removeImages` in the root directory - to clean and remove the images, this will also stop the network
