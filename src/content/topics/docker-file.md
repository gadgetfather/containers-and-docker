---
nextLink: nodejs-app
previousLink: docker-cli
---

# Dockerfile

Till now we have seen how to run containers and didn't really think about how to build them. Most of the time this is a job of DevOps person. but lets try to build it. Docker has a special file called a Dockerfile which allows you to outline how a container will be built. Each line is instruction. A big key with Docker container is that they're supposed to be disposable. You should be able to create them and throw them away as many times as necessary.

lets create most basic dockerfile ever.

```
FROM node:12-stretch

CMD ["node", "-e", "console.log('hello world')"]
```

The first thing on each line (FROM and CMD in this case) are called instructions. They don't technically have to be all caps but it's convention to do so so that the file is easier to read. Each one of these instruction incrementally changes the container from the state it was in previously, adding what we call a layer.

Lets go ahead and build it

```
docker build .
```

You should see it out put a bunch of stuff and it'll leave you with the hash of an image. After each instruction, you'll see a hash similar to the ones we've been using for the IDs for the containers. You know why that is? It's because each one of those layers is in-and-of themselves a valid container image

This container has two instructions in it. So it starts with `node:20-alpine` and then we add `CMD` instruction. There will be one of these in effect in dockerfile. if you have multiple it will take the last one.

To name our container we can do

```
docker build -t my-app .
```

if you don't pass the tag it will take `latest` implicitly.

You can give tag like this

```
docker build -t my-app:1 .

```
