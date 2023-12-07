# docker compose and some advance stuff

Docker Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application's services, networks, and volumes. Then, with a single command, you create and start all the services defined in your configuration.You define your application's services, networks, and volumes in a docker-compose.yml file. This file describes which Docker images to use, how they interact.

It's especially useful in development environments, where it simplifies the process of setting up and managing complex applications that consist of several interdependent Docker containers.

## Bind mount

A bind mount in Docker is a type of volume that allows you to map a directory or file from the host machine into a container. This means you can take a directory on your host machine and make it accessible within the container. read more about it [here](https://docs.docker.com/storage/bind-mounts/)

## Multi Stage builds

Multi-stage builds in Docker are a feature that allows you to create more efficient and smaller Docker images by using multiple stages in a single Dockerfile. Each stage in a multi-stage build can use a different base image and contain its own instructions, like copying files, running commands, etc

A multi-stage build typically has at least two stages. The first stage is often used for compiling or building the application (e.g., using a larger image with all necessary build tools). The second stage is used for running the application, where a smaller, runtime image is used.

Links for some resources -

1. https://github.com/veggiemonk/awesome-docker
2. https://devopswithdocker.com/
