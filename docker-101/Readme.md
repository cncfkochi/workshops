![101](src/images/docker-101-01.png)

### Introduction

Docker is an operating system container management tool that allows you to easily manage and deploy applications by making it easy to package them within operating system containers. Docker Containers has changed the way software is built and shipped.  

From a developer's point of view, it makes his life much easier to built and ship the software packages which will run anywhere. No longer need to worry about local and server environments.From the operation's point of view, we no longer need to worry about dependencies and system management. Run the containers anywhere without any hazards. From the business point of view, containers fastened the development and release of life-cycles. 


### History of containers

<details>
<summary>Evolution of Containers</summary>

- 1979: Unix V7 - chroot system calls
    
    During the development of Unix V7 in 1979, the chroot system call was introduced, changing the root directory of a process and its children to a new location in the filesystem. This advance was the beginning process isolation: segregating file access for each process. Chroot was added to BSD in 1982.

- 2000: FreeBSD Jails

    In 2000, a small shared hosting provider came up with FreeBSD jails to achieve clear-cut separation between its services and those of its customers for security and ease of administration. FreeBSD Jails allows administrators to partition a FreeBSD computer system into several independent, smaller systems – called “jails” – with the ability to assign an IP address for each system and configuration.


- 2001: Linux VServer

    Linux VServer is a jail mechanism that can partition resources (file systems, network addresses, memory) on a computer system.  This operating system virtualization is implemented by patching the Linux kernel.

- 2004: Solaris Containers

    In 2004, the first public beta of Solaris Containers was released that combines system resource controls and boundary separation provided by zones, which were able to leverage features like snapshots and cloning from ZFS.

- 2005 : Open VZ (Open Virtuzzo

    This is an operating system-level virtualization technology for Linux which uses a patched Linux kernel for virtualization, isolation, resource management and checkpointing. The code was not released as part of the official Linux kernel.


-  2006: Process Containers
    
    Process Containers (launched by Google in 2006) was designed for limiting, accounting and isolating resource usage (CPU, memory, disk I/O, network) of a collection of processes. It was renamed “Control Groups (cgroups)” a year later and eventually merged to Linux kernel 2.6.24.


- 2008: LXC

    LXC (LinuX Containers) was the first, most complete implementation of Linux container manager. It was implemented in 2008 using cgroups and Linux namespaces, and it works on a single Linux kernel without requiring any patches.


- 2011: Warden

    CloudFoundry started Warden in 2011, using LXC in the early stages and later replacing it with its own implementation. Warden can isolate environments on any operating system, running as a daemon and providing an API for container management. It developed a client-server model to manage a collection of containers across multiple hosts, and Warden includes a service to manage cgroups, namespaces and the process life cycle.

- 2013: LMCTFY
    
    Let Me Contain That For You (LMCTFY) kicked off in 2013 as an open-source version of Google's container stack, providing Linux application containers. Applications can be made “container aware,” creating and managing their own subcontainers. Active deployment in LMCTFY stopped in 2015 after Google started contributing core LMCTFY concepts to libcontainer, which is now part of the Open Container Foundation.

- 2013: Docker
    
    When Docker emerged in 2013, containers exploded in popularity. It’s no coincidence the growth of Docker and container use goes hand-in-hand. Docker also used LXC in its initial stages and later replaced that container manager with its own library, libcontainer. But there’s no doubt that Docker separated itself from the pack by offering an entire ecosystem for container management.


- 2017: Container Tools Become Mature
    
    Hundreds of tools have been developed to make container management easier. While these types of tools have been around for years, 2017 is the year that many of them earned their stripes. Just look at Kubernetes; since its adoption into the Cloud Native Computing Foundation (CNCF) in 2016.

</details> 


### A look back to the application deployment

In this mini workshop, we will walk you through the basic concepts of Docker



References

1. [A Brief History of Containers](https://blog.aquasec.com/a-brief-history-of-containers-from-1970s-chroot-to-docker-2016)