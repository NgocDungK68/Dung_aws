---
title : "Commands"
date :  "`r Sys.Date()`" 
weight : 5 
chapter : false
pre : " <b> 1.5 </b> "
---

## Some basic commands in Docker

- List image / container:
   ```
   docker image/container ls
   ```
- Delete image / container:
   ```
   docker image/container rm <image/container's name>
   ```
- Delete all images:
   ```
   docker image rm $(docker images –a –q)
   ```
- List all images:
   ```
   docker ps –a
   ```
- Stop a specific container:
   ```
   docker stop <container's name>
   ```
- Run a container from image and change container's name:
   ```
   docker run –name <container's name> <image's name>
   ```
- Stop all container:
   ```
   docker stop $(docker ps –a –q)
   ```
- Delete all containers:
   ```
   docker rm $(docker ps –a –q)
   ```
- Show log of a container:
   ```
   docker logs <container's name>
   ```
- Build an image from container:
   ```
   docker build -t <container's name>
   ```
- Run a container:
   ```
   docker run -d <image's name>
   ```
- Pull an image from Docker Hub:
   ```
   docker pull <image's name>
   ```
- Start a container:
   ```
   docker start <container's name>
   ```