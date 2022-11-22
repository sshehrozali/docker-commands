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