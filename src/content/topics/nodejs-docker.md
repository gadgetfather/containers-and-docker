---
previousLink: docker-images
nextLink: tags
---

# Node.js on Docker containers

Now what if you want run container with node in it? The alpine container we were playing does not come with Node.js installed. lets see on dockerhub

```
docker run -it node:21-alpine
```

The version that we are using here is 21 and alpine refers to distribution of linux. (By default it uses lts version of debian)

Notice that this will drop us into the Node.js REPL which you may not want. What if we wanted to drop into the bash of that container?

```
docker run -it node:21-alpine bash
```

in this case node image by default executes the `node` command (in alpine it was executing the exit command).

Now if you still want to confirm what linux distribution is being used you can check with

```
docker run -it node:21-alpine cat /etc/issue
```
