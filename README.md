# Simple Docker Guide

![4. They unplug the root machine but the thousands of leaf VMs scatter in the wind and start spinning up new instances wherever they land](https://imgs.xkcd.com/comics/xkcde.png)

Required: [Docker](https://www.docker.com/get-docker)


## What is Docker?

Basically docker can run and manage applications in isolated containers, providing consistent environments for each application.


## Image

Images are templates which docker uses to create a container. You can create and use your own images or pull others' images from online repositories like [Docker Hub](https://hub.docker.com/explore/).

Pulling an image from Docker Hub:

```sh
$ docker pull hello-world
```

`hello-world` is the name of the [image found on Docker Hub](https://hub.docker.com/_/hello-world/).

To create your own image, a `Dockerfile` is required. A `Dockerfile` is a text file containing instructions telling Docker how to correctly build the image. For more information, refer to the [official guide](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/).

Building an image:

```sh
$ cd /directory/containing/required/files/
$ docker build --tag image-name . 
```

`.` specifies the path where Docker has access to during the build process (AKA the "context" of the build). The directory should contain at least the `Dockerfile` itself.

Listing all images:

```sh
$ docker images
```

Removing an image:

```sh
$ docker image rm image-name
```

Removing all unused images:

```sh
$ docker image prune
```


## Container

Containers are instances of images which provide consistent environments for applications running inside them. They are similar to virtual machines, but a lot more lightweight.

Creating and running a container:

```sh
$ docker run --name container-name image-name
```

`image-name` specifies the image used to create the container.

Supplying `--detach` will run the container in background. (`docker run --name container-name --detach image-name`)

Stopping a container:

```sh
$ docker stop container-name
```

Listing all active containers:

```sh
$ docker ps
```

Supplying `--all` will include stopped containers in the result. (`docker ps --all`)

Removing a container:

```sh
$ docker container rm container-name
```

Removing all stopped containers:

```sh
$ docker container prune
```

Executing commands inside a container:

```sh
$ docker exec --interactive --tty container-name /bin/sh
```

`/bin/sh` is the command to be executed.
Supplying `--interactive` and `--tty` gives you the ability to send/recieve input/output through the shell.


## Volume

Volumes are managed storage spaces utilized by Docker to persist data across sessions or multiple containers. They are automatically created alongside containers e.g. when you execute `docker run`.

Listing all volumes:

```sh
$ docker volume ls
```

Removing unused volumes:

```sh
$ docker volume prune
```


## The Next Step

For further information, refer to the official guides and documentations:
* https://docs.docker.com/
* http://lmgtfy.com/?q=docker

## Other (GUI) Tools

* [Portainer](https://portainer.io/) is an opensource management UI for Docker.
* [Kitematic](https://kitematic.com/) is a GUI for Docker currently included in the official installer, [Docker Toolbox](https://www.docker.com/products/docker-toolbox).
