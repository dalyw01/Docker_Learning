# Docker-Learning
- Some notes I made while learning basic Docker functionality.

![Git](https://nickjanetakis.com/assets/blog/cards/differences-between-a-dockerfile-docker-image-and-docker-container-001320c81dd8d2989df10d0bec36341fd6a94b043f6f9de1c26ee79eaf16e566.jpg)

## Let's get started
- https://hub.docker.com/
- Download "Docker Desktop for Mac"
- Custom and official Docker IMAGES are on DockerHub, e.g - https://hub.docker.com/_/ubuntu/

## Some core lingo
- Docker IMAGES are used to create CONTAINERS
- A CONTAINER is an instance of an IMAGE
- A CONTAINER is a slimmed down version of an OS
- A DockerFile is basically a type of config file
- VOLUMES allow CONTAINERS to see files from the host machine

## Basic commands
```
docker images = lists all offline images on your machine
docker ps -a = display current running containers
```

## Juicy commands
- **-it** pops us into a container upon creating 
- **bash** commands are set
```
docker run ubuntu = creates an ubuntu container with random name (will download if image is not on machine already)
docker run --name LOL ubuntu = runs an ubuntu container with my custom name "LOL"
docker run -it ubuntu bash
```
## Juicier commands
- **-v** mounts a file or drive
- **--rm** deletes a container upon exiting it

```
docker rm $(docker ps -a -f status=exited -q) = delete all local containers
docker run -it --name my-linux-container --rm -v notes.txt ubuntu bash
docker run -it --name my-linux-container --rm -v /c/Users/:/my-data ubuntu bash 
```

## Creating a container from my own image file

This is the basic setup
```
MC-S104581:docker-tutorial dalyw01$ ls
Dockerfile	notes.txt
```
Build an IMAGE from the Dockerfile
- **.** indicates DockerFile is in same directory
```
docker build -t my-ubuntu-image . = build my local image, 
```
Now running the new IMAGE to create a CONTAINER
```
docker run -it my-ubuntu-image bash
```
Verifying Python is actually installed
```
root@29aacfd9b882:/# python3
Python 3.6.9 (default, Nov  7 2019, 10:44:02) 
```
