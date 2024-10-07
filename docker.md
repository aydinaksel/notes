# Introduction

Docker handles virtualisation. Open source software that uses containerization technology. Allows developers to package applications and their dependencies into lightweight, portable containers.


# What Is It?

- Docker is a platform that runs containers
- A container bundles an application's code and all its dependencies into one object
- Containers typically use less resources than virtual machines
- Docker containers can be run almost anywhere.
	- Docker must be installed on the host and the host is where the containers are being run which can be a server, virtual machine, desktop, etc. As long as the machine has Docker installed, then you can run Docker containers.

# Why Use It?

- Containers can be easily copied and deployed
	- Typically easier to deploy a container compared to a virtual machine
- Applications that run in containers are segregated from the rest of the host system
- Containers can often be cheaper to run than virtual machines
- Docker containers can be run on platforms such as AWS, Linode, Digital Ocean, etc.

# Weaknesses

- Not all apps are supported when run in containers
- Docker is awesome, but it is just one tool
	- It cannot be used for everything
- Performance can sometimes be inconsistent
	- You can install it on any machine, so running a docker container on Linux, Windows, etc. can yield different results.
	- Best to run Docker on Linux

# Starting Docker

```bash
# Start Docker
sudo systemctl start docker
```

# Stopping Docker

```bash
# Stop Docker
sudo systemctl stop docker

# Stop the socket which is prompted after stopping Docker
sudo systemctl stop docker.socket
```

# Images

```bash
# Search images with specified key word
docker search ubuntu

# Retrieve the specified image
docker pull ubuntu

# Show downloaded images
docker images
```

# Containers

These are the instances of the Docker Images that run on the Docker Engine. These can be quickly started, stopped, and restarted.

By default, containers do not save changes. So, Docker images are blueprints to create containers. If what you are trying to run is not in the image then it is not going to be inside the container. When you exit the container, the changes are lost.

```bash
# Create a container with the specified image
docker run hello-world

# List of all containers running on our system
docker ps

# List of all containers and ones that were running previously
docker ps -a

# Run a simple Ubunutu container and start a Bash shell. The `-it` flags allows
# you to open a terminal session inside the container, where you can run
# commands interactively in real time. The `-i` is for interactive and the `-t`
# is for 'tty' or terminal.
docker run -it ubuntu /bin/bash

# Run the container in a detached state, or daemon mode which sends the
# container in the background. So, the below runs the container in interactive
# mode and then sends it to the background.
docker run -it -d ubunutu /bin/bash

# To attach yourself to a container that is currently in the background
# use the attach command followed by the container ID.
docker attach 77c238efdb75

# Disconnects you from the server and keeps it running in the background.
^P^Q
```

# Accessing Containerized Apps

```bash
# Entrypoint command is a command in a container that is executed
# automatically. Since this command is executed automatically, the service
# is still running and it did not return us to the shell
docker run nginx

# Start the following container in interactive mode, daemon mode, and `-p`
# stands for 'port'. Nginx, or others, that provide a web server service
# typically run on port '80' by default. So, when the container starts, there
# is an nginx process listening on port 80 within the container. By default
# ports open inside a container are not accessibly outside the container.
# So, we need to create a way to access the port in the container. One way
# is to create a port mapping from a local port on the host system that is
# running docker to the port in the container that the application is
# listening on. So, the below maps the port 8080 on the local machine to the
# port 80 in the container.
docker run -it -d -p 8080:80 nginx

# Show IP address of local machine
ip addr show

# Then type in the IP address of the local machine followed by port 8080.
# This redirects to a webpage served by nginx in the Docker container
localhost:8080

# Stop a Docker container
docker stop b012001e58b2

# Run and restart unless specifically stopped
docker run -it -d --restart unless-stopped -p 8080:80 nginx
```

# Images

Lightweight, standalone, and executable packages. These are built by Docker Files which provide instructions for creating the Docker Images.

```bash
# Create a Docker image based on the running Docker container
docker commit b012001e58b2 aydin/fun-test:1.0.0

# Build an image from a Dockerfile. You must be in the directory of the
# Dockerfile. The `-t` is a tag. The `.` references the current working
# directory.
docker build -t aydin/fun-test:1.0.1 .

# The following command removes an image. However, you cannot remove an
# image that is used by an active or stopped container.
docker rmi b012001e58b2

# To remove containers from history.
docker rm b012001e58b2
```

# Resources

- [LLTV Docker Course](https://www.youtube.com/watch?v=WpwtzQq5Er4&list=PLT98CRl2KxKECHltRib03tG8pyKEzwf9t&pp=iAQB)