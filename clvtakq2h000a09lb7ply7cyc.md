---
title: "Using Jenkins to build pipeline by triggering git webhook (Git SCM)"
seoTitle: "Jenkins Git Webhook Pipeline"
seoDescription: "Automate CI-CD pipeline with Jenkins and GitHub webhook integration for seamless project updates triggered by Git changes"
datePublished: Sun May 05 2024 08:49:40 GMT+0000 (Coordinated Universal Time)
cuid: clvtakq2h000a09lb7ply7cyc
slug: using-jenkins-to-build-pipeline-by-triggering-git-webhook-git-scm
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/wX2L8L-fGeA/upload/463eda72e9a733eac1dc32164562daf2.jpeg
tags: devops

---

Jenkins is a tool used to create CI-CD pipeline. Today we will make a project by integrating GitHub and Jenkins which will integrate changes automatically whenever a change is made in GitHub repo.

First, we will create a Pipeline in Jenkins dashboard. The pipeline is a set of plugins that make it possible to execute jobs in a file. There are mainly two types of pipelines.

1. Scripted Pipeline
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714883474842/8efcd38f-8b8d-4a1c-a82a-8a736e7924de.png align="center")
    
2. Declarative Pipeline
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714883520028/650758d0-2b5a-48e7-ac7e-89d95368e004.png align="center")

For our project we will be creating a declarative pipeline and then using github webhook, it would make a new build whenever any changes are being made in the repository.

Our developer has already a python flask app ready at [repository](https://github.com/codermandy/cicdbatch19.git) so we created the following pipeline. After forking the repo, we build a declarative pipeline and selected **Github trigger using GitSCM polling.** This option invokes git plugin whenever it receives changes from git repository.

The option **Build periodically** builds the Continuous Integration at specific intervals of time.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714896134255/6c0b7283-af9a-4062-9216-24785dc5aad7.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714883969207/818172c9-8fa0-4bc3-966c-c4c9d207215a.png align="center")

After creating this, we just made a [ngrok](https://dashboard.ngrok.com/get-started/setup/windows) web link so that our GitHub webhook can communicate with Jenkins in public.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714884105354/c785780c-792f-4a47-8b09-99366c3da3b9.png align="center")

We can see the local Jenkins is now being hosted public

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714884644924/0c764c58-030f-44df-b929-93866f70acab.png align="center")

Then we went to GitHub and created a webhook for our repo from settings. There we just pasted the Ngok public URL as given below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714896903049/58f381b7-dd8d-4745-8cc2-0573b91fe478.png align="center")

In webhook we also ensure that our git webhook is working. Only then it would communicate with jenkins git plugin to trigger the build. We can see below that it is working fine.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714896443750/9475ee3e-9b2b-4bb4-a7b6-e4f2457cd7b0.png align="center")

When we check the jenkins dashboard, we see that 3 commits have been made and it has been triggered without any manual intervention. We can also view the git logs.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714896760265/01cd3e50-e5c8-4c98-a1e2-6143676afdc5.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714896801163/c5ff2b61-b741-43eb-a42e-997beff12828.png align="center")

We can check that app is running on the IP along with specified port.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714898413462/6cfc29b3-b988-45c3-b41c-c842da79ede6.png align="center")

There are some of the popular build trigger apart from Git SCM that we will discuss in some other blog.

* Poll SCM
    
* Scheduled job
    
* Remote triggers
    
* Build After other project are build.
    

Sources:-

1. Jenkins Documentation
    
2. GFG Devops Planning to Production