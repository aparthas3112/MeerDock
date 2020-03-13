# MeerDock
Docker file for MeerTime TPA projects

First, clone this repository with the Dockerfile and download and install Docker (https://docs.docker.com/install/). 
## Building the image from the dockerfile.
Once Docker is running, build an image from the pulled Dockerfile by running,
`docker image build -t meerdock .` in the directory with the Dockerfile. 

## Launching a container from the image. 
Before actually running the docker image, i.e, starting a container, one can choose to mount a shared volume to the container. This is typically done if you'd like to access files/data not present in the container. 

A container can launched with a shared volume by running, 
`docker run --name meerdock -d -p 2222:22 -v <SharedVolume_path_localmachine>:/DockerShared meerdock`. 

a) This launches a container named `meerdock` with a shared volume, that is accessible within the container in the path `/DockerShared`. \
b) This command also launches the container in the background exposing it in the localhost port 2222:22. \
c) If you do not want to mount a shared volume, just run, `docker run --name meerdock -d -p 2222:22 meerdock` \

## Using the container. 
Once the container is running, you can login to it by, `ssh -XY psr@localhost -p 2222`, with the password: `psr`. 

Enjoy! 
