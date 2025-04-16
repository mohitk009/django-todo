---
title: "Computer Networks"
datePublished: Wed Oct 16 2019 17:16:32 GMT+0000 (Coordinated Universal Time)
cuid: cldva8emh01pj6pnv2be11qr1
slug: computer-networks-4370681d1b26
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1675837252686/3d648c9b-53aa-42d2-b5a2-24ce1af9edb2.png

---

Type of Delays

There are 4 main types of delays while transferring data

1.  Transmission Delay

Transmission Delay

This delay refers to time taken to put a packet onto the link. In other words, it is simply time required to put data bits on the wire/communication medium. It depends on length of packet and bandwidth of network

Transmission Delay = Data size / bandwidth = (L/B) second

2\. Propagation Delay

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675837250409/effe3f13-0945-4421-8d67-f43496fb89fe.png)

Propagation Delay

Time taken by the first bit to travel from sender to receiver end of the link. In other words, it is simply the time required for bits to reach the destination from the start point. Factors on which Propagation delay depends are Distance and propagation speed.

Propagation delay = distance/transmission speed = d/s

3\. Queuing Delay

It is simply the time taken by data packets to get into queue of the switch or the switch. It depends on congestion or the no of packets in switch

4\. Processing Delay

It is simply the time taken by routers ts to process the packet header. It helps in detecting bit level errors.

> **Total time** \= Transmission delay + Propagation delay + Queuing delay + Processing delay