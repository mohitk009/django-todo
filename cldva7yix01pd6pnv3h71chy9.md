---
title: "The Data Link Layer"
datePublished: Fri Nov 22 2019 16:03:13 GMT+0000 (Coordinated Universal Time)
cuid: cldva7yix01pd6pnv3h71chy9
slug: the-data-link-layer-a4dd64df6ca8

---

Hi, We know that the bottom most layer in OSI/TCP IP protocol is data link layer. Let’s discuss more about it.

#### **Uses of data link layer**

1.  **Hop to Hop Delivery**

The data link layer is used for Hop to hop delivery of packets. Contrast data link layer with transport layer which is used for network to network delivery.

Data Link layer is responsible for transfer of packets from one router to another while transport layer is responsible for transfer of packets from one network to another.

**2\. Framing**

Data link layer adds header and trailer to packets. The headers consist of MAC, IP addresses etc. and trailers consist of error checking mechanism. Packets along with header and trailer is known as frame.

**3\. Flow and Error Control**

When packets travel from one router to another there is collection of packets or errors in packets which may cause traffic and congestion.To avoid this flow and error control mechanism is used.

a. Stop and Wait Protocol

b. Go Back N

c. Selective Repeat

**4\. Access Control**

While Transferring of packets, it may happen multiple devices access communication line simuntainously which may cause problem. To avoid this access control mechanism is used which is provided by data link layer.

We will discuss more about Flow and Error Control in next blogs.

Stay tuned!