---
previousLink: docker
nextLink: nodejs-docker
---

# Docker images

Now lets try to run image

```
docker run -it alpine:3
```

This is 10X easier than handcrafting everything by yourself ! This will now drop you inside the container as the root user of that container. When you are done just `exit` or do CTRL + D. Notice that it will grab a image alpine:3 from dockerhub for you to run it. The `-it` part of the command says you want to be dropped in container interactively. By default container just runs and exits. Try `docker run alpine:3`. It will do nothing and just exit.

Now if you want to do something before exiting. Try this

```
docker run alpine:3 ls
```

The `ls` part at the end is what you pass to container to execute. So if you don't pass anything it will just execute `exit` by default.

To run container in background do

```
docker run --detach alpine:3
```

it will print a hash and keep running in background.

Now to see which containers are running you can do

```
docker ps
```

This will print out all the running containers that Docker is managing for you. You should see your container there. Now copy the ID or name and run

```
docker attach <ID or name>
```

This allows you attach a shell to running container and play with it. Useful if you want inspect something or see the realtime logs.

Now to kill the container, you can simply do

```
docker kill <ID or name>
```

to kill everything running

```
docker kill $(docker ps -q)
```

## --name and --rm

Let's make our lives simpler

```
docker run --detach --name my-alpine alpine
docker kill my-alpine
```

Now you can refer these containers by name. but now if you try it again to run it will say `my-alpine` exists. You can see that container still exists even if it is stopped by doing `docker ps`.

So you can use `--rm` flag. So whenever it exits it will automatically cleanup for you.

```
docker run --rm --detach --name my-alpine alpine
```
