---
title: "Always Be On AWS ‘Cloud’ Nine!"
datePublished: Sun Jan 17 2021 11:32:01 GMT+0000 (Coordinated Universal Time)
cuid: cldva72kq00r5vonv5hnag8vp
slug: always-be-on-aws-cloud-nine-5a6ef5d0d5e8
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/A9_IsUtjHm4/upload/87aa5b9755dd714b42be56b9b2c4c92b.jpeg

---

Back into past decade, companies used to buy space and infrastructure for arranging their own servers for hosting websites. It was a huge investment and mantainance headache for such businesses.

Fast forward 10 years, currently many startups and companies are using Cloud services. Most of the websites we use are hosted on cloud. What does this mean?

This means that a big company act as cloud provider. Let’s say “Amazon AWS” buys all the infrastructure and keep it at one place. Now any business requiring servers for their website would reach to AWS and ask for renting some of it’s computing power for setting up it’s servers. So does it mean anyone could access data of the company being hosted on same server provided by AWS?

No, There are three type of different models that cloud providers offer:

1.  **Public Cloud :** In this model, users don’t mind if others are sharing the same servers. This is used by users who don’t have private or confidential data in their websites.
2.  **Private Cloud:** Most of users are big businesses and for them security is major concern. They ask provider to give them a seperate set of servers that is not accessible by public users.
3.  **Hybrid Cloud:** This model is combination of both public and private cloud. In this model, some data which is confidential is kept in private while which is not so important is kept in public cloud.

That’s alright! I understood the cloud and different models. If tomorrow I open a startup and some developers make a website. Tell me how would I setup cloud? Will I get whole Operating System, a dashboard or software which I can offer directly to clients?

Okay, concern is valid! There are three popular services being provided by cloud providers depending on the use cases:

1.  **Infrastructure as a service:** Remember, what it looks like when we buy a new laptop? If you opt for this, the cloud provider would ask users (businesses) choice of Operating System and configurations. It then provides them with the infrastructure with installed OS. Generally used for website hosting.
2.  **Platform as a service:** This provides a dashboard kind of space which is like drag and drop mechanism. Examples include google app engine in which you just have to take care of development/code and operations/configuration part is taken care by cloud provider
3.  **Software as a service:** Ever used google docs for editing documents? This service provides software directly to users. In this you just expose whole software to be made use to other users. Examples include Gitpod and all IDE’s where whole software is made available online.

The first cloud provider, “Amazon AWS”, came into picture in 2006 and still rules the cloud market. It has 35 % shares followed by Google and Azure which were launched in 2012–13 and have just half ie. 12–13% shares.

Being in the market for around 15+ years AWS carries a lot of job oppurtunities and mature enough to use. It continues to add new services while improving on existing services. Some popular services are :

### Compute

1.  **Elastic Compute (EC2):** EC2 is a configurable infrastructure service which provides access to whole OS which can be accessed from any terminal using SSH. We can easily increase or decrease resources( RAM, Storage). We can easily host websites or databse on it.
2.  **Elastic BeanStalk:** It provides same services EC2 does but as a platform. Here we can directly find a dashboard where we have to drag and drop the code, rest is taken care by AWS.
3.  **Lambda:** It is used for backend of the application. It just provides the textual output and cannot host any application.
4.  **Load Balancing & Auto Scaling:** These are two seperate but inter dependent services. Load Balancer analyzes servers running and distribute traffic to healthy instances. Auto Scaling manages servers based on usage demand and scales up or down number of servers.
5.  **Elastic Container Registery(ECR) and Storage(ECS):** Based on dockers(lightweight virtual computers that use minimum resources). Docker have power to run application independently and ECS is storage for docker images.

### Storage

1.  **Storage S3:** Used for storage. Each file in S3 acts as object. It provides storage faciliity for objects. And also provides backup facility, generally it’s available all the time. The resources for hosting websites such as logos or images can be stored on S3
2.  **S3 Glaciar:** Provides backup services for storage S3 service. Since it’s a backup service it takes time to access files compared to S3.
3.  **Elastic File System (EFS):** It is also a storage service. We can attach it to our local drive. It can be mounted on Windows/Linux machine and used where common storage is required.

### Databases

1.  **Relational Database Service(RDS):** A database service used for setting up relational databases in AWS
2.  **Dynamo DB:** A database service for NoSQL or unstructured data
3.  **RedShift:** Connects multiple databases and provides output as required
4.  **ElastiCache:** Stores frequently accessed data so that it need not go again to access that data.

### Security

1.  **Identity Access Management (IAM):** Used by big companies to grant their multiple employees access their seperate AWS account. Also company can put restriction on any of the employee. Application account under IAM helps to access resources in AWS using security keys.
2.  **Key Management Service(KMS):** Used to create key pairs for security and authentication of services