---
title: "Hands on with Jenkins"
datePublished: Sat Jan 21 2023 11:11:48 GMT+0000 (Coordinated Universal Time)
cuid: cld5up4io00000al17sdr906d
slug: hands-on-with-jenkins
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/ujx_KIIujRg/upload/a17e5d0d7fd923b3d0e06b68ebfa839e.jpeg
tags: docker, yaml, jenkins, pipeline, docker-compose

---

1. We would be checking the options when to rebuild our project using `Build Triggers` We can either set up a build
    
    * through scripts or after some other project
        
    * after a specific time
        
    * through commits in a particular branch
        
    * when a pull request is made
        
    * through GitHub hooks (on w In `Build Steps` we would also type certain commands so that docker-compose run creates and runs a container through `YAML` file
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1674296176802/eff4c2a0-e5d3-44e1-a548-f0aea6bedcef.png align="center")
        
2. If we want to receive mail for failed builds we can also set up notifications.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1674296225238/7623babe-33a7-475f-b25d-c769fbeb4852.png align="center")
    
3. We can also check the `Build history` in the left sidebar to see the console output for debugging.
    
    Also for commits, we can Click on `#Build number` to check the status of our build and for debugging purposes.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1674296399988/b1fe721b-f02c-4bc1-95a4-2446c12b8039.png align="center")
    

On port 8001 mentioned in `yaml` file our web application would be built.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1674297031630/12d7c076-7917-495d-8a44-e7adcee300ed.png align="center")

## Building the project in jenkin through pipeline

1. In the pipeline, we would be defining `stages` (Code, Build, Test, Deploy) and `steps` in pipeline script once we have created the project. The `config` menu would be having this option
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1674297551061/f916152a-62ee-4322-aa0e-7c5af56af45f.png align="center")
    
    * `pipeline` is always written at top of the pipeline script file
        
    * `agent` defines on which Operating system this code would be executed.
        
    * `stages` defines SDLC stages and `script` are the commands that get executed on the host machine
        
2. Then through `Full Stage View` we can see all the stages
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1674297752588/2cde3903-b2c1-4f28-a20c-f679d2ed0316.png align="center")
    
3. Our app would be built using the Jenkins pipeline and would be accessible according to the port defined in `Dockerfile` or `YAML` file.
    

## References

1. [Train with Shubham](https://www.trainwithshubham.com/) Zero To Hero DevOps Bootcamp