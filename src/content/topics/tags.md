---
previousLink: nodejs-docker
nextLink: docker-cli
---

# Tags

Tags, these are very important. if you run `docker run -it node` this will automatically use the `latest` tag. it equivalent to running `docker run -it node:latest`. `:latest` is the tag. This allows to run different versions of the same container, just like we have React 16 or React 18. So lets say your React app few years old and uses React 16 with some packages that require Node 16 at that you can do

```
docker run -it node:16 bash
```

once inside the shell you can check the node version by doing `node -v`. This is helpful because now we can fix our Node.js version to the one our app expects.

Now back to the

```
docker run -it node:21-alpine cat /etc/issue
```

You have already seen that this is running Alpine Linux. This is very very tiny distribution of linux made for containers. Alpine containers are bare bones. If you want anything in them you are going to have do it yourself. This is exactly opposite to Ubuntu and Debian container as they ship entire village with them which convinent and much larger in size. Alpine images are about five megabytes whereas Ubuntu is close to two hundred megabytes. As you can see this can make difference in how fast you can deploy and can cost significantly less in terms of storage. It's also in general better to have less unnecessary things in your containers: less is more in terms of security. If an attacker tries to execute a Python exploit on your container but your container doesn't have Python then their attack won't work.

> PRO-TIP : have a development container which has all the logs, whistles, debugging tools, etc. that you need. Then have a production container that's minimalist as possibly can be.
