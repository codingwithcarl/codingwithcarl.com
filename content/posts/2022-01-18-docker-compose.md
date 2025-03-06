+++ 
draft = false
date = 2022-01-18T20:17:19-05:00
title = "Docker Compose"
description = "Quick introduction to Docker Compose"
slug = ""
authors = []
tags = []
categories = []
externalLink = ""
series = []
+++
A **composing system** for containers is a tool that allows us to describe the whole microservice architecture program in a config file, and then perform operations on the system.

- .yml files

- default is docker-compose.yml

```yml
services:
  redis:
    image: redis
    volumes:
      - /tmp/redis:/data
    ports:
      - 6379:6379
```

- services: containers that are to be built and run
  
  - redis service
    
    - pulling image from docker hub
    
    - mounting a volume for persistent storage
    
    - exposing port 6379, allowing the host and other containers to access the Redis server

## Commands

**up:** bring up all microservices in docker-compose.yml

**-d:** run in detached mode

**down:** stops all microservices

**depends_on:** controls startup order of the containers and controls dependency

```yml
version: '3'
services:

  redis:
    image: redis

  mongodb:
    image: mongo
    volumes:
      - /tmp/mongo:/data/db

  mosca:
    image: matteocollina/mosca
    volumes:
      - /tmp/mosca:/db

  publisher:
    build: publisher
    depends_on:
      - "mosca"
      - "subscriber"

  subscriber:
    build: subscriber
    depends_on:
      - "redis"
      - "mongodb"
      - "mosca"
```

---

#### References

[Docker for Developers | Packt](https://www.packtpub.com/product/docker-for-developers/9781789536058)

[Docker Compose Commands](https://docs.docker.com/compose/reference/)
