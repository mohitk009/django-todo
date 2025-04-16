---
title: "Running Web App from Docker Using EC2 Instance"
datePublished: Sat Jan 14 2023 13:17:16 GMT+0000 (Coordinated Universal Time)
cuid: clcvz3iw7000308l2b6ov4d3v
slug: running-web-app-from-docker-using-ec2-instance
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/jOqJbvo1P9g/upload/c3b0cb10aed49953d0416240513126bf.jpeg
tags: ec2, docker, aws, devops, dockerfile

---

1. **Launch EC2 Instance and Install Docker using EC2 template**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673677232090/3772ee3a-b2ef-49e5-8f44-02070618ec43.png align="center")
    
    Click on Launch Instance on EC2 Dashboard
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673677631813/bb7f0990-4400-44ce-987b-546e37d96b66.png align="center")
    
    Select **Ubuntu** from Quick start option
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673677256613/d78d78be-a732-4f6d-8904-afc42e97b535.png align="center")
    
    Don't forget to enable **HTTPS** and **HTTP** traffic from Internet to allow anyone to connect from our instance.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673677689354/9d4c4b93-d825-4e56-aa06-0dbdba9bdf8d.png align="center")
    
    Under Advanced details fill the [User Data](https://gist.githubusercontent.com/gonzaloplaza/ff79d0593085ed14b3a5c1ba2f8f7afa/raw/cbb578b9e0e0d843dca9a0ee4319248487e1dac8/aws_ec2_ubuntu_userdata_docker.sh) according to Ubuntu Operating system. This contains the commands which AWS executes before starting the operating system at launch time.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673681440751/be7d0510-9a51-4919-b61c-a42f7e527769.png align="center")
    
    When we connect to our instance in our shell `docker --version` gives the details about docker.
    
    1. **Copy project from github to our ec2 instance (local machine)**
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673684807474/6dfc5da1-0566-499f-95a1-d8c4578d34ee.png align="center")
        
        Using `git clone <repo-url>` we copy repository in our ec2 instance. All the files will be displayed.
        
        In this directory only we will create `Dockerfile`. This would be the home directory to our Docker container.
        
        The `Dockerfile` looks something like this
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673684058706/64173565-5fbb-49b5-9984-3d4ad9971165.png align="center")
        
        <mark>Dockerfile -&gt; </mark> [<mark>Docker Image</mark>](https://hub.docker.com/search?q=) <mark> -&gt; Docker Container</mark>
        
2. **Create a Dockerfile using the keywords and arguments**  
    **FROM** specifies name of docker image along with its tag. There is a `dockerhub` which contains all the docker images. We could have used `linux docker image` but we chose `node` as it is higher level base image than linux.  
    **WORKDIR** specifies working directory for the container. The image would be creating a container, this option specifies `app` folder would be created inside docker container which would contain application content
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673700366117/722ea476-3026-444a-b92f-ba3a49a1fe0d.png align="center")
    
    After executing `docker exec` to get inside container, we can see `/app` has been created inside it.  
    **COPY** would simply copy file from Docker root (same location as Dockerfile) to the created container. It runs on the host machine and copies to container OS.  
    **RUN** runs command with shell inside base linux layer in the container. We can have multiple RUN commands.  
    **EXPOSE** would simply allow the port to connect to outer world, here 8000 is HTTP port  
    **CMD** executes commands from shell/bash in the container to start the application. CMD is executed only one time when container is created from image.
    
    After creating the Dockerfile we have to save it with the exact name -&gt; `Dockerfile`
    
3. **Create an Docker Image from Dockerfile**
    
    After we create a Dockerfile we can build image out of it using the following command
    
    `docker build -t my-app:1.0 .`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673698677639/fe82f800-8649-4ba7-9f12-128fa564bf64.png align="center")
    
    This command basically creates a docker image `my-app` out of a Dockerfile. We can also view the created image using `docker images`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673698789858/55700d3f-8ce7-4039-b224-d6c17c8b0a54.png align="center")
    
    **Jenkins** actually creates an image from the Dockerfile.
    
4. **Run the container from Docker Image**
    
    Till the step 3 we have created a docker image, in the last step we would create a docker container and expose our IP and port to world so others can access our app using URL
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673701291640/ce8d5435-e17d-4ba7-b741-1c86724d59e7.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673701304053/270b977b-580a-4c2d-85f8-41da6afbaabe.png align="center")
    
    We look for our image details using `docker images` and then using `docker run -p` we did port mapping so that world could access our web application.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673701502438/e3b7bb75-e208-4dbe-93c8-4e8386f41265.png align="center")
    
    Also under `Security groups` -&gt; `inbound rules` we allow port 8000 in custom TCP so that world could access port 8000 of our host EC2 instance.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673701216615/ed396b0d-cea8-4be5-acf2-208baaf552c2.png align="center")
    
    We finally, go to our web browser type in &lt;public-ip&gt; followed by &lt;port&gt; and from any browser can access the web application.
    
    ## References
    
    1. [TechWorld with Nana](https://www.youtube.com/@TechWorldwithNana) for detailed Docker Tutorial
        
    2. [Train With Shubham](https://www.trainwithshubham.com/) for ZeroToHero
        
    3. [Hash13](https://www.hash13.com/) for AWS services & userdata