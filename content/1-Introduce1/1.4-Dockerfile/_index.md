---
title : "Dockerfile"
date :  "`r Sys.Date()`" 
weight : 4 
chapter : false
pre : " <b> 1.4 </b> "
---

## What is Dockerfile

**Dockerfile** is a config file for Docker to build an image. Here are the configs:

- **FROM**: Specifies the original image: python, unbuntu, alpine...
- **LABEL**: Provide metadata for image. Can be used to add information maintainer. Command **docker inspect** to view all the label of images.
- **ENV**: Set an environment variable.
- **RUN**: Create a command to build image and install package into containers.
- **COPY**: Copy files and folders into container.
- **ADD**: Copy files and folders into container.
- **EXPOSE**: Declare port of image.
- **VOLUME**: Create a directory mount folder to access and store data.

## The process of a system using Docker

![Dockerfile](/images/1-Introduce/process.png)

A Docker system is implemented by three main steps:

- **Build** - **Push** - **Pull, Run**
