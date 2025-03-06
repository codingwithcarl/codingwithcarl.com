+++ 
draft = false
date = 2021-12-07T18:17:33-05:00
title = "Dockerfiles"
description = "An introduction to Dockerfiles"
slug = ""
authors = []
tags = []
categories = []
externalLink = ""
series = []
+++
A text file that defines how to build a [Docker](https://www.codingwithcarl.com/posts/2021-11-30-docker/) container image.

Docker can build images automatically by reading the instructions from a **Dockerfile**. A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image. Using `docker build` command, users can create an automated build that executes several command-line instructions in succession.

```dockerfile
# we will inherit from  the Debian image on DockerHub
FROM debian

# set timezone so files' timestamps are correct
ENV TZ=America/New_York

# install apache and php 7.3
# we include procps and telnet so you can use these with shell.sh prompt
RUN apt-get update -qq >/dev/null && apt-get install -y -qq procps telnet apache2 php7.3 -qq >/dev/null

# add a user - this user will own the files in /home/app
RUN useradd --user-group --create-home --shell /bin/false app

# set up and copy files to /home/app
ENV HOME=/usr/app
WORKDIR /home/app
COPY . /home/app

# The PHP app is going to save its state in /data so we make a /data inside the container
RUN mkdir /data && chown -R app /data && chmod 777 /data

# we need custom php configuration file to enable userdirs
COPY php.conf /etc/apache2/mods-available/php7.3.conf

# enable userdir and php
RUN a2enmod userdir && a2enmod php7.3

# we run a script to stat the server; the array syntax makes it so ^C will work as we want
CMD  ["./entrypoint.sh"]
```

Components are installed within the container. Apache's config files are created on the host, then copied to the container. 

## A "good" Dockerfile

- fast to build

- fast to rebuild after a change

- small image

## Layer Caching

- each line in a Dockerfile creates a new layer

- a layer is only recreated  if something changes inside the layer

- for most docker instructions, this means that layer creation is skipped if the line in the dockerifle did not change

- `COPY` will copy files from your working directory into the container

- if a file that has been copied has changes, this will invalidate the layer cache from this line on

```dockerfile
FROM perl:5.30.2-buster
COPY . /usr/src/myapp
WORKDIR /usr/src/myapp
RUN cpanm -n --installdeps .
CMD ["perl", "-I/usr/src/myapp/lib", "/usr/src/myapp/bin/http2matrix.pl"]
```

- Time to initally build: 66s

- Time to rebuild: 70s

- Size: 885MB

If anything changes in "myapp" the `COPY .` invalidates the `RUN` line. We have to reinstall all dependencies every time we change something in our code.

***Never ever use COPY .*** (which copies an entire directory) as any change, including the Dockerfile itself and .git, will invalidate the following layers.

```dockerfile
FROM perl:5.30.2-buster
WORKDIR /usr/src/myapp
COPY cpanfile /usr/src/myapp/cpanfile
RUN cpanm -n --installdeps .
COPY bin /usr/src/myapp/bin
COPY lib /usr/src/myapp/lib
CMD ["perl", "-I/usr/src/myapp/lib", "/usr/src/myapp/bin/http2matrix.pl"]
```

Now, whenever something is changed in the app, you don't need to reinstall the dependencies (unless the dependencies are changed) which significantly reduces the time to rebuild. 

- Time to initially build: 66s

- Time to rebuild: 2s

- Size: 885MB

## Reducing Image Size

Prepackaged images are usually large. Buliding a custom image can reduce size.

```dockerfile
FROM debian:buster-slim #operating system
RUN apt-get update && apt-get install -y ... && apt-get clean && rm -rf /var/lib/apt/lists
WORKDIR /usr/src/myapp
COPY cpanfile /usr/src/myapp/cpanfile
RUN cpanm -n --installdeps .
COPY bin /usr/src/myapp/bin
COPY lib /usr/src/myapp/lib
CMD ["perl", "-I/usr/src/myapp/lib", "/usr/src/myapp/bin/http2matrix.pl"]
```

The first RUN statement is cached as one layer. It installs updates and whatever packages you need, then cleans up the cache in the image to reduce size. 

- Time to initially build: 131s

- Time to rebuild: 2s

- Size: 341MB

It's longer to initially build, however the image size is reduced which helps with storage costs. 

## Summary

- Never use `COPY .`

- Think about the ordering of your Dockerfile statements to optimize layer caching and build time

---

#### References

[Docker for Developers | Packt](https://www.packtpub.com/product/docker-for-developers/9781789536058) 

[domm - Writing a good Dockerfile for Perl apps - YouTube](https://youtu.be/ARpLPQWblAM)

[Docker development best practices | Docker Documentation](https://docs.docker.com/develop/dev-best-practices/) 

[Dockerfile reference | Docker Documentation](https://docs.docker.com/engine/reference/builder/)
