# What is Docker?

Docker is a containerization platform whic packages your application & all its dependencies together in the form of **containers**, to ensure that you application works seamlessly in any environment be it *development/test/production*. </br>

## Benefits

* RAM consumed by containers is << RAM consumed by virtual machines.
* Are light-weight, can be easily sahred via Docker Hub.
* Easily run applications by packaging the into containers.
* Portability
* Sacalability
* Efficiency
* Consistency
* DevOps Enablement: it facilitates the adoption of DevOps practices by providing a standarized and reproducible deployment unit.

In summary, containarization technology refers to the practice of encapsulating an application and its dependencies into a self-contained unit called a container.

## Docker Architecture

* Docker Engine: At the core of Docker architecture is the Docker Engine. It is responisble for building, running, and managing containers.

* Docker Images: Are the building blocks of containers. An image is a read-only template that contains the necessary files, libraries, and dependencies required to run an application.

* Docker Containers: Containers are the running instances of Docker images.

* Docker Registry: It is a central repository for storing and distributing Docker images.

## Docker real-case uses

![Docker used](/section-01-theory/docker-uses.png "Places where Docker can be used")


## Basic Commandas

```docker
docker --version

# Creates and runs container from an image
docker run
docker run -d --name my-first-container 

# List running containers
docker ps

# Removes one or more containers
docker rm my-first-container

# Display the logs of a container
docker logs my-first-container

# Provides detailed information about a container
docker inspect my-container

# Copies files and folders between container and the host
docker cp
docker cp my-container:/path/to/file/host/path

# Displays real-time resource usage statistics of running containers
docker stats my-container
```

## Official Web Site to Install Docker

[Install Docker Engine](https://docs.docker.com/engine/install/)

## Dockerfile

A Dockerfile is a text file that contains a list of commands that the Docker client should execute to create an image. In simple words, it's a way to automate the image creation process.

```dockerfile
FROM python:3.8

# set a directory for the app
WORKDIR /USR/SRC/APP

# copy all the files to the container
COPY . . 

# install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# tell the port number the container should expose
EXPOSE 5000

# run the command
CMD ["python", "./app.py"]
```