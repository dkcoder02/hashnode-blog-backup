---
title: "An Introductory Guide to the Docker Foundation"
seoTitle: "Docker Basics: A Beginner's Guide"
seoDescription: "Discover the basics of Docker containers and virtual machines. Learn how Docker works, key concepts, and essential CLI commands for developers"
datePublished: Mon Mar 24 2025 05:00:55 GMT+0000 (Coordinated Universal Time)
cuid: cm8mlmpek000009l46t8d8amj
slug: an-introductory-guide-to-the-docker-foundation
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1742792140379/eca0f54e-56cf-4d6b-a91e-32a9d6316cf2.png
tags: docker, kubernetes, devops, containers, ai-tools

---

## Foundation of containers

**Container** is a lightweight, standalone and executable software package that includes everything necessary to run a piece of software, such as the application code, runtime, system tools, libraries and settings. This encapsulation ensures that the application operates *consistently across various computing environments, from development and testing to production*

![How to work containers](https://cdn.hashnode.com/res/hashnode/image/upload/v1742787043973/99edaf59-024a-4344-a439-991cd86ec9e0.png align="center")

* A **Hypervisor** also known as a ***virtual machine* (VM)**, is a software or hardware layer that allows multiple virtual machines (VMs) to run on a single Physical Machine. It manages system resources like CPU, memory and storage, ensuring that VMs operate independently and efficiently.
    
* **Docker** is a powerful engine, Docker is an **open-source platform** that allows developers to ***build, package and deploy applications*** *using* ***containers***. Containers are lightweight, portable, and ensure that applications run consistently across different environments.
    

---

## Container vs Virtual Machine (**Hypervisor)**

​Docker containers and virtual machines (VMs) are both technologies that enable the deployment of applications within **isolated environments**, but they differ significantly in their architecture and resource utilization.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1742788854593/3d14cf0b-8eba-4eb1-85be-641784d0abe3.png align="center")

* **Virtual Machines:** VMs operate by virtualizing physical hardware, allowing multiple operating systems to run concurrently on a single physical machine. Each VM includes a full guest OS, along with virtualized hardware, running a top a hypervisor that manages these VMs.
    
* **Docker Containers:** Containers, in contrast, leverage the host operating system kernel to run isolated user-space instances. They package applications with their dependencies but share the host OS kernel, making them more lightweight and efficient. This approach reduces the need for separate OS instances, leading to faster startup times and lower resource usage.
    

Docker is much more optimized, up to 100 times faster than VMs and enhances load balancing.

---

## Why Developers should use containers ?

​*Containers offer developers several key benefits :*​

* **Portability:** Containers package applications with their dependencies, ensuring they perform consistently across different environments. ​
    
* **Efficiency:** By sharing the host OS kernel, containers use fewer resources than traditional virtual machines, allowing for more applications to run on the same hardware. ​
    
* **Agility:** Containers support agile and DevOps practices by enabling quick development, testing, and deployment cycles. ​
    
* **Scalability:** Containers can be easily scaled horizontally to manage increased workloads.
    

---

## Behind the Scenes: How It Works When You Run Your First Container

​When you execute the `docker run` command, Docker performs several key actions to set up and run your containerized application

1. **Image Retrieval:** Docker checks if the specified image is available locally. If not, it pulls the image from a Docker Hub. ​
    
2. **Container Creation:** Using the image, Docker creates a new container. This involves *setting up isolated environments using namespaces and control groups* to ensure the container operates independently.
    
3. **File system Setup :** Docker mounts a writable layer on top of the image’s read-only file system, allowing the container to modify files during its execution without altering the original image. ​
    
4. **Network Configuration:** Docker assigns the container a unique IP address and *sets up networking rules, enabling communication with other containers and external systems* as defined.
    
5. **Application Execution:** Finally, Docker runs the specified application or command within this isolated environment, ensuring consistent behavior regardless of the host system's configuration.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1742790005419/5e259777-da2c-4140-9eb4-69bc828d11cb.png align="center")

---

## Key Docker Concepts : Images, Containers, Docker files

1. **Docker Images** : A Docker image is a lightweight, standalone, and executable package that includes everything needed to run a piece of software: code, runtime, libraries, environment variables, and configuration files
    
2. **Docker Containers :** A container is a runtime instance of a Docker image. It is a lightweight, standalone, and executable package that includes everything needed to run a piece of software
    
3. Docker Files : A **Dockerfile** is a script containing a series of *instructions* that *define how to build a Docker image*. It automates the creation of containers by specifying the base image, dependencies, configurations and commands needed to run an application.
    

---

## Basic Docker CLI commands

````markdown
## 1. Running Containers

```sh
# Run a container from an image
docker run <image>

# Run a container in detached mode (background)
docker run -d <image>

# Run a container with a custom name
docker run --name my-container <image>

# Run a container and map port 8080 on host to 80 in container
docker run -p 8080:80 <image>

# Mount a volume from the current directory to /app in the container
docker run -v $(pwd):/app <image>

# Run a container interactively with a shell
docker run -it <image> sh
```

## 2. Managing Running Containers

```sh
# List running containers
docker ps

# List all containers (including stopped ones)
docker ps -a

# Show logs of a specific container
docker logs <container>

# Attach to a running container's terminal
docker attach <container>

# Stop a running container
docker stop <container>

# Kill a container (force stop)
docker kill <container>

# Stop all running containers
docker stop $(docker ps -q)
```

## 3. Removing Containers

```sh
# Remove a specific container
docker rm <container>

# Force remove a container
docker rm -f <container>

# Remove all stopped containers
docker container prune
```

## 4. Copying Files to and from Containers

```sh
# Copy a file from a container to the host
docker cp <container>:/path/to/file ./
```
````

---

## Conclusion

In conclusion, Docker is a powerful tool for developers, offering portability, efficiency, and scalability in application deployment.

If you found this blog post helpful, please consider sharing it with others who might benefit. You can also follow me for more content on JavaScript, React.js, Next.js, and other web Development , Devops topics.

For *Paid collaboration*, *Web Development freelancing* *work*, mail me at: [**krishdesai044@gmail.com**](mailto:krishdesai044@gmail.com)

Connect with me on [**Twitter**](https://x.com/DKB972), [**LinkedIn**](https://www.linkedin.com/in/krishdesai117/), and [**GitHub**](https://github.com/dkcoder02).

Thank you for Reading

Happy Coding