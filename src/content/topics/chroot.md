---
previousLink: what-are-containers
nextLink: docker
---

# Chroot

Chroot (short for "change root") is a Unix system call that allows a process to change its root directory to a new location in the file system. This new location becomes the root directory for the process and its children, effectively isolating them from the rest of the system.

Chroot is commonly used in system administration and software development for various purposes, such as:

- Creating a sandbox environment for testing and debugging applications.
- Running potentially unsafe or untrusted programs with restricted access to the system.
- Building and testing software in a controlled environment.

To use chroot, you typically need root privileges. Here's an example of how to use chroot:

- this helps in separating two processes on the same server
- So lets get started

```
docker run -it --name docker-host --rm --privileged ubuntu:bionic

```

- This will download official ubuntu container from the docker hub and will pick the version with bionic tag.
- To see what version of ubuntu we are in you can run

```
cat /etc/issue/
```

Now lets attempt to chroot

1. lets make a folder <code >mkdir /my-new-root</code>
2. Inside the new folder , run `echo "GTA 6 trailer is out!" >> /my-new-root/secret.txt`
3. now try to run `chroot /my-new-root bash` and it will give you error.

it will say that shell is not able to find the bash. That's because bash is program and your new root does not have bash to run.(because it cannot reach outside of its new root). Lets fix it.

1. `mkdir /my-new-root/bin` (inside bin all the executable programs are kept)
2. `cp /bin/bash /bin/ls /my-new-root/bin/`
3. `chroot /my-new-root bash`

Still not working! Now the reason is that these commands rely on libraries to power them and we did not copy those. So lets also bring them. run `ldd /bin/bash. it will give output like this

```
linux-vdso.so.1 (0x0000ffffbc101000)
	libtinfo.so.5 => /lib/aarch64-linux-gnu/libtinfo.so.5 (0x0000ffffbbf82000)
	libdl.so.2 => /lib/aarch64-linux-gnu/libdl.so.2 (0x0000ffffbbf6d000)
	libc.so.6 => /lib/aarch64-linux-gnu/libc.so.6 (0x0000ffffbbe14000)
	/lib/ld-linux-aarch64.so.1 (0x0000ffffbc0d5000)
```

These are the libraries that bash needs. Let's bring them in as well.

1. Copy them to our environment

```
mkdir /my-new-root/lib /my-new-root/lib64
```

2. We need copy all those who have path.

```
cp /lib/aarch64-linux-gnu/libtinfo.so.5 /lib/aarch64-linux-gnu/libdl.so.2 /lib/aarch64-linux-gnu/libc.so.6 /lib/ld-linux-aarch64.so.1 /my-new-root/lib

cp /lib/aarch64-linux-gnu/libtinfo.so.5 /lib/aarch64-linux-gnu/libdl.so.2 /lib/aarch64-linux-gnu/libc.so.6 /lib/ld-linux-aarch64.so.1 /my-new-root/lib64
```

You can follow the same process to get the `ls` command working as well.

Now lets try to get `chroot` again and you should see that we are in `Bash`. if you do `pwd` to see working directory it will show `/`. That's it we just made a container. At any time to exit you can do `exit` or CTRL + C.

#### You can try for `cat` as well !

Congrats! you just made your first container :D
