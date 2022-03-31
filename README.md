# Jenkins 101
## About Jenkins 101 Project
This is a guide for learning Jenkins.


## CICD and Jenkins
### What Is CICD


### Jenkins Is A Tool for Implementing CICD


## Install Jenkins
### Running Jenkins on Dokcer
[running jenkins on docker](https://www.jenkins.io/doc/book/installing/docker/)

``` shell
# 
docker run \
  --name jenkins-docker \
  --rm \
  --detach \
  --privileged \
  --network jenkins \
  --network-alias docker \
  --env DOCKER_TLS_CERTDIR=/certs \
  --volume jenkins-docker-certs:/certs/client \
  --volume jenkins-data:/var/jenkins_home \
  --publish 2376:2376 \
  docker:dind \
  --storage-driver overlay2

# build image
docker build -t myjenkins-blueocean:2.332.1-1 .

# run Jenkins
docker run --name jenkins-blueocean --rm --detach \
  --network jenkins --env DOCKER_HOST=tcp://docker:2376 \
  --env DOCKER_CERT_PATH=/certs/client --env DOCKER_TLS_VERIFY=1 \
  --publish 8080:8080 --publish 50000:50000 \
  --volume jenkins-data:/var/jenkins_home \
  --volume jenkins-docker-certs:/certs/client:ro \
  myjenkins-blueocean:2.332.1-1
```

### Intialize Jenkins

## References
