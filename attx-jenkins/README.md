## Build and Run

Build with gradle:
* build the image: `gradle buildJenkinsImage`
* push the image: `gradle pushJenkinsImage`

Running the docker image:
* without persistance: `docker run -p 49001:8080 -t attxproject/attx-jenkins`
* with persistance: `docker run -p 49001:8080 -v /data/jenkins:/var/jenkins_home -t attxproject/attx-jenkins`
