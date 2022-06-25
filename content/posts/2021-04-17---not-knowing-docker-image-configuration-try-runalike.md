--- 
title: Not knowing Docker image configuration? Try runalike
date: "2021-04-17T19:34:54.000Z" 
template: "post" 
draft: false 
slug: "not-knowing-docker-image-configuration-try-runalike" 
category: "Technology" 
tags: 
  - "Technology" 
  - "Ops / DevOps" 
description: "The `docker inspect` will certainly come in handy, but the same one can little be unreadable - or it just requires the unreasonable rewriting of all values of the indicated result. Therefore, a simple image of assaflava / runlike was created which makes the work easier" 
socialImage: "media/server-10.jpg" 
---
There is a chance that after entering the server, we do not know with what command docker image was launched. The `docker inspect` will certainly come in handy, but the same one can little be unreadable - or it just requires the unreasonable rewriting of all values of the indicated result. Therefore, a simple image of assaflava / runlike was created which makes the work easier.
The approach to the painting is simple. It is required to connect the socket docker and indicate the image. The output will be a printed result presented as a complete docker run command including all switches
```shell
docker run --rm -v /var/run/docker.sock:/var/run/docker.sock \ 
    assaflavie/runlike YOUR-CONTAINER
```
If we use a given command often, we can additionally add it as an alias
```shell
alias runlike="docker run --rm -v/var/run/docker.sock:/var/run/docker.sock  
 assaflavie/runlike" 
runlike YOUR-CONTAINER
```
A simple option, and effective. It allowed me to save time and find a solution to overwrite the image environment variable when on the server I couldn't find the file that launched the original image.
