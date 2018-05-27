---
layout: post
title: Dockerizing containers
description: 
image: assets/images/pic11.jpg
nav-menu: true
permalink: projects/docker
---
    
### What was the problem?
COLAB builds many different websites. Many were on the same stack, but the devops between developers was different with some developers using MAMP and some using vvv. This made providing support and maintenance somewhat complicated.

### How does docker fit into the workflow?
Docker with docker-compose was chosen to streamline the developer environment and make it easier for support and maintenance to begin development. 

### What was my role in helping the team with docker?
While working with senior developers, I helped create new containers to solve this problem. I personally built the craft container, however, most of my expertise in this area was updating old MAMP and vvv environments to the new docker system. Internally this project is still being worked on and I have been tasked with taking over the internal docker-compose cli that is attempting to further streamline initial development setup.