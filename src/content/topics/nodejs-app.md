---
nextLink: docker-compose
previousLink: docker-file
---

# Node.js App

Lets dig into some more advance things. lets start making nodejs server.

```
const http = require('http')
http.createServer((req,res)=>{
    console.log("New connection")
    res.end("Hello world")
}).listen(3000)
```

This is a very basic server that listens to traffic on port 3000. You can run it by doing `node index.js`

Now lets try to run it inside the docker now. First is we need to copy all stuff from local machine inside the container. We will use `COPY` for that.

```
FROM node:20-alpine

COPY index.js index.js

CMD ["node","index.js"]
```

This will copy index.js file into docker file system. Now we can run the container

```
docker build -t my-node-app .

docker run my-node-app
```

Now you can see that the server is running but you won't be able to access it. Thats because we have to tell docker to expose its port. CTRL+C also wont work since node.js doesn't handle SIGINT itself. so you need to kill the container `docker kill my-node-app`.

Now to make container work and accessible. `--init` flag will tell docker to handle linux signals.

```
docker run --init -p 3000:3000 my-node-app
```

This will make server accessible outside the container as well.
