---
title: "Docker Basics and Hands On"
seoTitle: "docker basics"
seoDescription: "this blog is about docker basics and hands on. we would be running our first app with docker"
datePublished: Mon Jan 16 2023 18:28:13 GMT+0000 (Coordinated Universal Time)
cuid: cld0lauha000208k6eki3g1qi
slug: docker-basics-and-hands-on
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/SYTO3xs06fU/upload/e969f476d493c57e3c78761973998008.jpeg
tags: docker, aws, devops, containers, dockerhub

---

## What is Docker? What is Container?

Docker is a platform and technology for building, shipping, and running distributed applications. It uses containerization to create lightweight, portable, self-sufficient containers that can run on any infrastructure, making it easier to deploy and manage applications. Docker allows developers to package an application with all of its dependencies and ship it as a single container, making it easier to move the application between development, testing, and production environments.

## Docker Vs Virtual Machine

The operating system has 2 layers

| Docker | Virtual Machine |
| --- | --- |
| The Docker uses Kernel of its base Operating system | The Virtual machine has its own kernel |
| The size of docker image is smaller ranging from few MB's | The virtual machine images are larger in size ranging from few GB's |
| Docker are faster as they don't have to start kernel | VM takes time to load kernel and then applications. |
| Windows kernel might not be compatible with Linux so, linux docker can't run on windows machine. | VM's have seperate kernel |

## Docker Image Vs Docker Container

| Image | Container |
| --- | --- |
| Actual Package along with configuration and dependency | Actually start the application |
| Artifect -&gt; can be moved around | Container is running environment for image |
| Not in running state | In running state |

Container has a **seperate port** and **virtual filesystem** different from host machine.

## Docker Installation

1. Go to docker website and install according to your OS platform [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/)
    
2. Enable virtualization if not enabled. [https://stackoverflow.com/questions/27884846/virtualization-not-enabled-in-bios](https://stackoverflow.com/questions/27884846/virtualization-not-enabled-in-bios)
    
3. For EC2 installation from userdata refer this article.
    

## Basic Commands

| Docker command | Use case |
| --- | --- |
|  |  |
| `docker pull <image-name>` | pulls the docker image from docker hub |
| `docker run <image-name:tag>` |  |
| `<tag> is optional` | pulls image and runs the container |
| `docker ps` | shows all the running container with container-id, image name, ports, container name etc. |
| `docker run -d <container-name>` | shows the id and runs the container in background without disturbing the host machine shell |
| `docker stop <container-id>` | stops the docker container |
| `docker start <container-id>` | starts the docker container |
| `docker ps -a` | shows both running and stopped container |
| `docker run -p<host-port>:<container-port> <image-name:tag>` | port mapping host and docker |
| `docker images` | shows images present in docker |
| `docker rmi <image-id>` | deletes the docker image |
| `docker rm <container-id>` | deletes the docker container |
| `docker build -t <image-name:tag>` | create a new Docker image from a specified Dockerfile |
| `docker --help` | shows a list of docker commands |

## Debugging Commands

| Command | Use Case |
| --- | --- |
| `docker run -p<host-port>:<container-port> --name <container-name> <image-name:tag>` | alloctes container name instead of random name along with port mapping |
| `docker logs <container-id>` | shows the container logs |
| `docker exec -it <container-id> /bin/bash` | Enter into docker container with interactive terminal as a bash shell |

## Creating and pushing <mark>Docker Image </mark> to <mark>Dockerhub</mark>

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673977740525/4ae9666e-740a-4fb3-88b7-56b07f264850.png align="center")

After cloning the app from git repo we went into app and have created a Dockerfile

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673977844557/d0eabedd-ffbd-4536-aea8-54913f685cb7.png align="center")

After we created our Dockerfile, we have to build `todo-app` Docker image from the same location for all the items.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673978548597/701d7240-5722-4568-9251-31d29bba0b18.png align="center")

After that we have to login into docker hub using the above command and provide our credentials. If account do not exist we have to create from [Dockerhub](https://hub.docker.com) and then login.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673978123855/854f7bca-4a6a-4250-ae06-04739e45ab10.png align="center")

In this step, we rename our docker image using `docker tag` and view list of locally created docker images using `docker images`. After that using push command we send out newly created image to `Dockerhub`

## Pulling the <mark>Docker image</mark> from <mark>Docker hub</mark> and run the web application in browser

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673978240035/59d0fd7e-d7b2-4907-97d5-6413084492d5.png align="center")

In the first step we create a container out of docker image with `-p` as port 8001 on container and port 8001 on host machine are mapped together . `-d` option helps to run this container in background as a service. It is then followed by `image-name` : `tag` . First it checked if image was present on local volume, then it fetched whole image from docker hub.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673979700815/9cca8e9c-b15d-4e71-af1c-2f7b5e7ed55e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673979724882/9a9bc9f4-50f6-40f1-b500-1172fe277414.png align="center")

We check if container has been created by using `docker ps` . After that we open the port 8001 of host machine through `AWS security group` in `inbound rules` . When port is accessible, the web application is displayed through public ip of the host machine followed by mapped port number of the container.

## Why Docker container is not used in production?

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673980588164/fc7fd199-4992-4ac4-98c3-c42eacf6f61a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673980627881/b058a4b5-2d87-46f9-995b-bb7523d5751b.png align="center")

Docker containers can be kill easily if someone gets container id , therefore for security reasons it is not preferred in production environment. Other reasons can be

* **Lack of persistent storage**: By default, Docker containers are ephemeral, meaning that any data stored within them is lost when the container is stopped or deleted. This can make it difficult to use them in production environments where data needs to be retained.
    
* **Difficulty in scaling**: Docker containers can be challenging to scale horizontally, especially when compared to other container orchestration tools like Kubernetes.
    
* **Difficulty in monitoring**: Docker containers can be difficult to monitor and troubleshoot, especially when running multiple containers on the same host.
    
* **Security concerns**: Running untrusted or unknown images in production can pose a security risk.
    
* **Production requirements**: Some production environments might have specific requirements that are not met by containerization, such as GPU support or real-time processing
    
* **Legacy systems**: Some organizations might be running legacy systems that are not designed to be run in containers.
    

There are other Orchestration tools like **docker swarm** and **kubernetes** which are used to deploy the containers. We would be studying these in our upcoming article. Stay tuned!

## References

* [OpenAI Chat GPT](https://chat.openai.com/chat) for clearing my doubts though #90DaysOf devops community helped as well.
    
* [TrainWithShubham](https://www.trainwithshubham.com/) for the hands on examples
    
    Article written based on my own understanding, References helped me to reduce the time consumed in writing the article.