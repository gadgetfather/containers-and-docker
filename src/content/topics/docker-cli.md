---
nextLink: dockerfile
previousLink: tags
---

# Docker CLI

Lets have look at some of the docker CLI commands

## pull / push

```
docker pull bcbcarl/hollywood

docker run --rm -it bcbcarl/hollywood

```

This will pull the container. The second line will execute this fun container. Lets have look !

`push` allows you to push the containers to whatever registry you are connected to (probably dockerhub or ECR or azure container registry)

## inspect

```
docker inspect my-alpine
```

It will dump out a lot of information about the container. Good check with whats going on with container.

## pause / unpause

As the name says it pauses / unpauses the processes in container.

```
docker run --detach -it bcbcarl/hollywood

docker ps

docker pause <ID or name>

docker unpause <ID or name>

docker ps

```

## exec

This allows you to execute a command against existing/running container. whereas `docker run` tries to create a new container.

```
docker run --detach -it bcbcarl/hollywood
docker ps
docker exec <ID or name > ps aux
```

If you haven't seen `ps aux` before, it's a really useful way to see what's running on your computer.

## import / export

allows you to dump out your container with tar file.

## history

this allow you to see how this Docker image's layer composition has changed over time and how recently.

```
docker history node-21
```

## info

Dumps a bunch of info about the host system. useful if you are logged into VM (like ec2 instance) and not sure about environment

```
docker info
```

## logs

Very useful to see the output of one of your running containers.

```
docker run -d node

docker logs <id>
```

## restart

Self explanatory

## Search

To check if container exists on dockerhub

```
docker search redis
```
