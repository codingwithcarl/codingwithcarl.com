+++ 
draft = false
date = 2022-01-11T17:50:41-05:00
title = "Docker CLI"
description = "Cheat sheet for starting and stopping containers "
slug = ""
authors = []
tags = []
categories = []
externalLink = ""
series = []
+++
Another [CLI cheat sheet](https://www.codingwithcarl.com/posts/2021-10-23-cli/); this time for Docker. 

Whenever you edit the Dockerfile, the image needs to be rebuilt:

```bash
 docker build -t name .
```

List locally stored images:

```bash
docker image list
```

Run a container with a specified image:

```bash
docker run myImage
```

-d: detached. Run the container in the background. Don't overtake the terminal with output from the container.

--rm: remove the container when stopped. recommended to always include this in every docker run command

--hostname: assign a hostname to the container. useful for container networking. 

-p: map port 80 from the container to port 8086 on the host

-v: mounts volumes to the container. retains data (stored on the host) that is written to the filesystem by the container after a restart

Example run command:

```bash
docker run \
    -d \
    --rm \
    -p8086:80 \
    -v name:/data \
    --name="mycontainer" \
    mycontainer
```

Launch the container with shell (/bin/bash):

-it: For interactive processes (like a shell), you must use `-i -t` together to allocate a tty for the container process.

Full command to start a container, name it, and launch a bash prompt within it:

```docker
docker run -it --rm --name mycontainer myimage /bin/bash
```

View logs of a detached container:

```bash
docker logs mycontainer -f
```
List running containers:

```bash
docker ps
```

Stop the running container:

```bash
docker stop mycontainer
```

---

#### References

[Docker for Developers | Packt](https://www.packtpub.com/product/docker-for-developers/9781789536058)

[Docker Docs](https://docs.docker.com/)
