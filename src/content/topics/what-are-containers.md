---
previousLink: introduction
nextLink: chroot
---

# What are containers?

## Here is a ELI5 explanation !

Imagine you have a lot of toys and you want to keep them organized. You might use different boxes to put different types of toys in. One box for your cars, another for your dolls, and maybe a third one for your building blocks. Each box keeps one type of toy together so it's easy to find and play with.

In the world of computers, "containers" are like those toy boxes, but for computer programs. Just like you put cars in one box and dolls in another, in a container, you put all the things a computer program needs to run, like the instructions and tools it uses. This way, the program can be moved from one computer to another easily, just like moving your boxes of toys from your room to a friend's house. And because everything the program needs is in its own container, it doesn't get mixed up with other programs, just like your toys stay organized in their boxes.

#### So in technical language ...

_Containers are is just a few features of the Linux kernel duct-taped together. it's just using a few features of Linux together to achieve isolation. That's it._

> The kernel in a computer is responsible for managing how programs use the computer's resources and ensuring everything works together smoothly. It's in charge of tasks like memory management, process control, and handling input/output operations. So you can think of it as like the mayor of a city!

## Why Containers?

Containers offer several benefits that make them popular in software development and deployment:

### **Bare Metal**:

"Bare metal" refers to running a web server directly on the physical hardware. It's like having your code execute right on the processor, ideal for performance but demanding in management. Imagine needing a new server: you'd call Dell or IBM, wait for the shipment, and have a tech install it in your server farm, a process taking months. Once set up, the challenges continue. You need to keep the operating system updated, maintain hardware connections, and regularly upgrade or replace server components. On top of that, there are network issues, cable management, and concerns about power costs, physical security, and data center temperature. It's a complex task, almost like managing a small city, and typically requires a dedicated team to handle it efficiently.

"Bare metal" servers have several disadvantages, including high initial and maintenance costs, difficulties in scaling, space and energy demands, risk of downtime, security vulnerabilities, and the need for technical expertise. Their physical nature also leads to longer setup times, making them less agile

### **Virtual Machines**:

Virtual machines add a layer of abstraction to traditional servers, allowing multiple guest operating systems to run within a host system. This setup is beneficial because it enables one powerful server to create and manage multiple virtual servers as needed, offering greater flexibility. For instance, adding a new service simply involves spinning up a new virtual machine, provided there's sufficient capacity, which streamlines the process significantly.

Also you can separate two VMs from each other on the same server:

Imagine two soda companies, "Thumbsup" and "Mountain Dew," lease server space from a cloud provider to manage their production and store their secret recipes. If the provider places both companies on the same physical server without proper separation, one company could potentially access the other's confidential files. For instance, Thumbsup might SSH into the server and find Mountain Dew's secret recipe, posing a serious security risk. Additionally, if Thumbsup realizes they share the server with Mountain Dew, they could intentionally overload the server with a <a href="https://www.cyberciti.biz/faq/understanding-bash-fork-bomb/" target="_blank">Fork Bomb</a>, hogging resources and disrupting Mountain Dew's operations. Even less maliciously, any user on a shared server could accidentally crash it, affecting all tenants on that server.

So VMs are individual operating systems running on bare metal. The host machine offers VM certain amount of resources and if that VM runs out, they only run out and don't affect other VMs running on the server. All these things come at cost of bit of performance. Running an operating system within an operating system is very heavy!

### **Containers**

Containers are lightweight and share the host system's operating system kernel, reducing resource consumption and enabling efficient utilization of hardware resources. So these provide many of the security and resource management features of VM but without the cost of having to run a whole other operating system. It instead usings chroot, namespace, and cgroup to separate a group of processes from each other.
We will only cover chroot in this case. You can checkout about namespace and cgroup from <a href="https://www.nginx.com/blog/what-are-namespaces-cgroups-how-do-they-work/" target="_blank">here</a>.
