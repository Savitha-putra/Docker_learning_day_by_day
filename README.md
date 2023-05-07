# Learning Docker and jenkins in local

in this repo, we will learn the docker and jenkins along with its working sections one by one.Plan is to learn docker and Jenkins thoroughly.
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
- [Bash examples](#Bash)


## Docker
<a target="_blank" href="/images/docker_image.png"><img border="1" alt="Blue whale image representing Docker for fun" src="/images/docker_image.png" width=1000></a>

 we will refer below links for explanation and understanding of terms we come across.
[docs.docker.com](https://docs.docker.com/)

Docker is a containerization platform that provides a simple way to build, deploy, and manage software containers. Docker containers are isolated from each other and from the host operating system.

List of all commands are here.[docs.docker.com/engine/reference/commandline/docker/](https://docs.docker.com/engine/reference/commandline/docker/)
Top 25 commands and examples here.[geekflare.com/docker-commands/](https://geekflare.com/docker-commands/)

```bash
# To check which all images in your system
docker images
REPOSITORY   TAG       IMAGE ID       CREATED         SIZE
centos       latest    5d0da3dc9764   19 months ago   231MB

# to name the docker container name with particular name use --name 
docker run -d --name jenkins_server centos
1437cafe4399aa7f36bb5183fe2f879fc5590769b8310ed7be63b467bebd7da4

#to check all running containers in your system
docker ps -a
CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS                     PORTS     NAMES
1437cafe4399   centos    "/bin/bash"   9 seconds ago   Exited (0) 7 seconds ago             jenkins_server

# to test Docker installed properly, best image to pull and run a container from it would be.
docker run docker/whalesay cowsay "Hey Team! Good morning"
Status: Downloaded newer image for docker/whalesay:latest
 __________________________
< Hey Team !, Good Morning >
 --------------------------
    \
     \
      \
                    ##        .
              ## ## ##       ==
           ## ## ## ##      ===
       /""""""""""""""""___/ ===
  ~~~ {~~ ~~~~ ~~~ ~~~~ ~~ ~ /  ===- ~~~
       \______ o          __/
        \    \        __/
          \____\______/


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
## Jenkins instalation in Docker
We are following the commands given in offical page here.(https://www.jenkins.io/doc/book/installing/docker/)

```bash
# To create a bridge network in Docker
docker network create jenkins
```
Bridges connects two or more different LANs that has a similar protocol and provides communication between the devices (nodes) in them. By joining multiple LANs, bridges help in multiplying the network capacity of a single LAN. Since they operate at data link layer, they transmit data as data frames.

## Bash
```bash
#to extract a tar.gz file, use the --extract (-x) option
tar -xf archive.tar.gz
#-v option will print the names of the files being extracted on the terminal.
tar -xvf archive.tar.gz
#to create a tar file from the given directory
tar -czvf file.tar.gz directory
#to create a tar from directories and files in same path
tar -czvf filename.tar.gz /path/to/dir1 dir2 file1 file2
#to list the contents of tar file use -t option
tar -ztvf projects.tar.gz
```
