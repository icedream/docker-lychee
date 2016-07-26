Lychee Dockerfile
=============

This repository contains Dockerfile of Lychee for Docker's automated build published to the public Docker Hub Registry.

# Base Docker Image
[kdelfour/supervisor-docker](https://registry.hub.docker.com/u/kdelfour/supervisor-docker/)

# Installation

## Install Docker.

Download automated build from public Docker Hub Registry: docker pull kdelfour/lychee-docker

(alternatively, you can build an image from Dockerfile: docker build -t="kdelfour/lychee-docker" github.com/kdelfour/lychee-docker)

## Usage

You can run this image with the following command, replace the volume host paths with whatever paths you store the Lychee data files in and replace the mysql link with the appropriate link to allow the container to connect to a MySQL server.

    docker run -it -d -p 80:80 \
    	-v /your-path/uploads/:/uploads/ \
    	-v /your-path/data/:/data/ \
    	--link mysql \
    	kdelfour/lychee-docker
    
## Build and run with custom config directory

Get the latest version from github

    git clone https://github.com/kdelfour/lychee-docker
    cd lychee-docker/

Build it

    sudo docker build --force-rm=true --tag="$USER/lychee-docker:latest" .
    
And run

    sudo docker run -d -p 80:80 -v /your-path/uploads/:/uploads/ -v /your-path/data/:/data/ -v /your-path/mysql/:/mysql/ $USER/lychee-docker:latest
    
Enjoy !!    