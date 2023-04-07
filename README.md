# Learning Docker in local

in this repo, we will learn the docker and its working sections one by one.Plan is to learn docker thoroughly.
Each section has screenshots and scripts learned along with description

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

- [Docker](#docker)
  - [How to migrate a Docker image without registry](#how-to-migrate-a-docker-image-without-registry)
  - [Clean up Docker before starting](#clean-up-docker-before-starting)
  - [Install Docker on Amazon Linux 2](#install-docker-on-amazon-linux-2)
  - [Install Docker on Linux](#install-docker-on-linux)
  - [Install Docker-Compose](#install-docker-compose)
  - [Dockerfile](#dockerfile)
- [Jenkins](#Jenkins)
  - [Initial Git configuration](#Jenkins-installed-in-docker)
    - [Generate SSH Keys](#generate-ssh-keys)
    - [Generate and auto-sign your commits with GPG](#generate-and-auto-sign-your-commits-with-gpg)


## Docker
<a target="_blank" href="/images/docker_image.png"><img border="1" alt="Blue whale image representing Docker for fun" src="/images/docker_image.png" width=1000></a>

 we will refer below links for explanation and understanding of terms we come across.
[docs.docker.com](https://docs.docker.com/)

Docker is a containerization platform that provides a simple way to build, deploy, and manage software containers. Docker containers are isolated from each other and from the host operating system.

```bash
# To start the docker daemon:
docker -d
# To start a container with an interactive shell:
docker run -ti <image-name> /bin/bash
# To "shell" into a running container (docker-1.3+):
docker exec -ti <container-name> bash
# To inspect a running container:
docker inspect <container-name> (or <container-id>)
# To get the process ID for a container:
docker inspect --format {{.State.Pid}} <container-name-or-id>
# To list (and pretty-print) the current mounted volumes for a container:
docker inspect --format='{{json .Volumes}}' <container-id> | python -mjson.tool
# To copy files/folders between a container and your host:
docker cp foo.txt mycontainer:/foo.txt
# To list currently running containers:
docker ps
# To list all containers:
docker ps -a
# To remove all stopped containers:
docker rm $(docker ps -qa)
# To list all images:
docker images
# To remove all untagged images:
docker rmi $(docker images | grep "^<none>" | awk "{print $3}")
# To remove all volumes not used by at least one container:
docker volume prune
```
## Jenkins

Followed the instructions on below link to get image and install jenkins
[hub.docker.com](https://hub.docker.com/r/h1kkan/jenkins-docker)

```bash
# To pull docker image into local
docker pull h1kkan/jenkins-docker
# To start contianer of docker image
docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home h1kkan/jenkins-docker:lts
```
Any issue faced while installing jenkins on top of Docker use[github.of.docker.above.image]
(https://github.com/jenkinsci/docker/blob/master/README.md)
## Jenkins installed in docker

```bash
docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home h1kkan/jenkins-docker:lts
```
