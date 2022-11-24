## Docker Commands
### Quick Start Guide

#### Container vs Image
A Docker Image is a file that contains the actual binaries such as PostgresSQL, Redis, etc. It's the same as installing it directly on the machine.

A Docker Container is actually a virtual environment which has all the configurations installed i.e. original image, setting up environment, required libraries, protocol/network configuration, and everything in order to make the Docker image executable.

#### Docker Network
A Docker Network is a virtually created network environment where you can run your Docker containers inside (like a isolated piece of containers running in a specified Docker network).

Example can be:
1. Creating a `mongo-network`
2. Pulling `mongodb` and `mongoexpress` Docker images
3. Running both images in their containers inside mongo-network (specifying by passing a flag arg)
4. `mongodb` and `mongoexpress` now running inside `mongo-network`

#### Port Binding
Docker port binding is a technique to allow multiple Docker images listen to their respective ports even if they both running on same ports. This is done via port binding command.

##### How it works?
We bind every Docker image port to listen to their respective HOST (each HOST cannot have some ports shared). 

You can think port binding like this:
`... -p PORT:HOST ...` where `PORT` is actual the port where your Docker image is listening to and `HOST` is your machine port bound with Docker image `PORT`.

This technique is very useful especially when you running two same Docker containers with different versions like PostgesSQL v14.XX and PostgresSQL < v14.XX because both PostgresSQL containers will listen to exact same port which you can't decide which container to connect. Under such scenarios port binding plays a very useful technique.

### Commands
* `docker pull [image]` - to pull image from Docker Hub
* `docker run [image]` - to start a Docker container
* `docker run [flags] [image]` - to start a Docker container with flags
* `docker start [container_id]` - to restart a Docker container
* `docker stop [container_id]` - to stop a Docker container
* `docker build -t [container_name]:[version]` - to build an image with a Dockerfile
* `docker rm [container_id]` - to remove a container
* `docker images` - to list all Docker images
* `docker ps -a` - to get history of all ended/up containers
* `docker ps -a | grep [container_name]` - to see history of a specific container
* `docker ps` - to list all running containers
* `docker logs [container_id] or [container_name]`- to display logs of running container
* `docker exec -it [container_id] /bin/bash` - to get access as a root user for Linux terminal

#### Example use-case for starting mongodb container
`docker run -d \
--name mongodb \
-p 27017:27017 \
-e MONGO-INITDB_ROOT_USERNAME=admin \
MONGO-INITDB_ROOT_PASSWORD=password \
--net mongo-network \
mongo`

Flags:
* d: Start in detach mode
* name: Name of the container
* p: Port binding
* e: Environment variables
* net: Specifying which network to run in
