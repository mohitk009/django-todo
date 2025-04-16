---
title: "AWS Essentials"
datePublished: Sun Feb 05 2023 11:56:44 GMT+0000 (Coordinated Universal Time)
cuid: cldsrcso500060ame5nlg9ih6
slug: aws-essentials
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/jxhM5Ni46zw/upload/4c8c42880ec8f07889a343e93e1e2654.jpeg
tags: aws, vpc, subnet, ip-address

---

## Why AWS?

* Covers around 45% of the market share.
    
* It is one of the first cloud service providers and has cloud services in every field including AI and ML.
    
* It has flexible usage options, pay-as-you-go, savings plan, spot billing etc. which makes it economical to use.
    

## [AWS Global Infrastructure](https://aws.amazon.com/about-aws/global-infrastructure/)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675526798366/c25c3b78-751e-4e2d-ad83-9110b084415b.png align="center")

* AWS has more than 99 AZs which have physical servers installed at various locations across the world.
    

### Regions & AZs (Availability Zones)

* **A region is a** particular area where 2 or more availability zones are there.
    
* AZs (Availability Zone) is the actual location where physical servers are installed
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675527406668/918b9021-4ecf-4209-b9c1-696f9ab34f99.png align="center")
    
    Here, **Mumbai is a** region and it has 3 AZ which are shown above.
    

## AWS Pricing

* [AWS pricing calculator](https://calculator.aws/#/) is used to calculate estimated costs across various regions.
    

## VPC Basic Understanding & Rough Idea

* There are three levels of the network through which the internet reaches us. They are LAN (local), MAN (city) , WAN (Global)
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675528664638/237632ce-2f1f-4faa-b5f4-157543c441ad.png align="center")
    
* A network consists of various subnets which helps in managing IP addresses among the users.
    
    ![AZ](https://cdn.hashnode.com/res/hashnode/image/upload/v1675529558649/ef0b35f0-56c1-4ab5-bf94-e697bea7ff23.png align="center")
    
* In the above diagram, we design a web application where we want the first web app instance to be public and the other Database instance to be private.
    
* For that, we have created our custom VPC in AWS. With the help of security groups, web app instances can access private DB. Also, the world can access the web app through another inbound rule in the security group.
    
* All this configuration is done in our custom-designed Virtual Private Cloud.
    
* There can be other network devices involved like network gateway, routers, switches etc. which allow connection to the internet in this rough architecture.
    

# Basic Networking Concepts

## IPv4 addressing and CIDR Notation

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675679806819/e72cb922-f7ac-4adc-aa1f-fc2675050c57.png align="center")

* IPv4 addressing is of 32 bits. Only 2^32 ie. 4 billion IP addresses are possible at a given time.
    

In order to manage IP address we can use 3 techniques:

1. Private IP
    
2. Use IPv6 addressing
    
3. Use of Subnets
    

## Subnet

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675682923665/b130ed33-d442-4c5d-88e2-17aa45344829.png align="center")

* In the subnet, we create virtual networks using IP addresses.
    
* A subnet can be represented in CIDR notation (subnet address) as shown in given diagram.
    

### CIDR Notation

* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675684389951/e34b9f38-02de-46ae-8dea-da1797d95063.png align="center")
    
    IPv4 class C is represented in 4 bits using decimal representation.
    
* When we create a binary representation for the same IP it turns out to be 32 bits.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675684402600/e9f52508-9a43-4a7d-a612-83caab4d0d1f.png align="center")
    
    After converting the following IP to CIDR notation we get the following binary representation
    
* Using this information we can create subnets as explained in the following video [https://www.youtube.com/watch?v=NuVqcOq9YtY](https://www.youtube.com/watch?v=NuVqcOq9YtY)
    

## Virtual Private Cloud (VPC) in detail

* A virtual private cloud is a virtual network that stimulates data centre but it has scalable infrastructure (router, firewall, switches, etc.) of AWS.
    
* AWS keeps logical isolation among various virtual network through VPC
    

### How does VPC Work?

### Type of VPC

1. **Default VPC**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675531532352/5fda22bd-9fb8-4c5d-9caf-f79e61ed8379.png align="center")
    

* It is created by default when an AWS account is created
    
* It has default CIDR, Security group, NACL and route table
    
* It has an Internet Gateway by default which allows people to access the internet
    

1. **Custom VPC**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675531328926/eba10f9e-8da2-4a48-b15d-39879339c179.png align="center")

* It is created by the Admin and does not come by default
    
* Admin can define its CIDR
    
* It does not have an Internet Gateway by default one needs to be created when needed.b
    

### Public Vs Private Subnet

* If a subnet is routed through Internet Gateway it is known as a public subnet.
    
* If a subnet does not have a route to Internet Gateway it is known as a private subnet.
    

### Internet Gateway Vs NAT Gateway

* Internet Gateway (IG) is a virtual router that connects a VPC to the internet
    
* It is necessary to connect VPC to IG to gain access to the Internet
    
* Using **NAT Gateway** we can connect instances in private subnets to the internet or other AWS services.
    
* The internet cannot initiate a connection with our instances in VPC when connected with NAT Gateway.
    

## References

* [TrainWithShubham](https://www.trainwithshubham.com/) for AWS concept explanation
    
* [Technical Guftugu](https://www.youtube.com/@TechnicalGuftgu) for Subnet and VPC concept