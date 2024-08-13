---
title : "Other concepts"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 1.3 </b> "
---

## Some concepts related

- **Docker client**: Is a tool help user contact with Docker host.
- **Docker daemon**: Is the Docker server for requests from the Docker API. It manages images, containers, networks and volumes. 
- **Docker Registry**: Is the private repository of Docker Images. Images are pushed to registry and client will pull images from registry. Users can use their own registry or a provider's registry such as: AWS, Google Cloud, Microsoft Azure.
- **Images**: Is a template for creating a container. An image will be built based on Dockerfile.
- **Dockerfile**: Is a file that includes code for building an image.
- **Volumns**: Is the data created when a container is run.

![Docker](/images/1-Introduce/dockerArchitecture.png)
