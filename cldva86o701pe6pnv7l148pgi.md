---
title: "Computer Networks"
datePublished: Wed Oct 16 2019 04:51:28 GMT+0000 (Coordinated Universal Time)
cuid: cldva86o701pe6pnv7l148pgi
slug: computer-networks-4626f179fe6d
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1675837242967/9487e96a-6676-4cf7-bf3e-6022bfad14b7.jpeg

---

Layers and Protocols (OSI and TCP/IP model Intro)

Have you ever thought why it’s so easy to run the internet? It’s because of abstraction. The Internet works in this way. There are certain layers on both client and server side.

> The Internet is collection of layers and protocols.

Yes, this is true. You can imagine internet as a collection of layers on each side, the client and the server. The layers can be imagined as a person and protocols as policeman. The layers communicate with each other with the help of protocols as policemen controls the traffic. For example HTTP is the protocol of application layer and on client side it talks directly to server without worrying about other layers. The layers provide abstraction and it assumes rest all will be handled by layers above or below it.

OSI model

Each layer starting from application, adds header and trailer to data generated in application layer. After it reaches to server from client, the server one by one opens the header and trailer to reach at top of server -side application layer.

The OSI(Open System Interconnect) model has seven layers. The bottom most layer called physical layer comprises of physical medium, it consist of optical fiber,coaxial or twisted pair cable or even WiFi. It only understands binary and more about systems and signal part.

The Data Link layer transfers data from one device to another connected in a LAN or from switch to devices. It uses CDMA/CA (collision avoidance) in order to stop collisions which generally happens in WiFi networks. It uses MAC address(printed on NIC) to establish connection.

While transferring data through data link layer, it may happen due to physical layer(transmission medium) data may get manipulated. In order to ensure quality of data certain mechanism such as access control, error detection and flow control are used.

![TCP/IP model along with protocols](https://cdn.hashnode.com/res/hashnode/image/upload/v1675837240738/0f79339f-c871-4055-8c93-5433ed2f371f.jpeg)

TCP/IP model along with protocols

There is one more model called TCP/IP which has only four layers Data Link, N/W Transport and Application layers. They work same as in OSI model but TCP/IP model is unreliable and connection less which means it does not guarantee delivery of data packets.

The Network layer establishes server connection from one computer to another using **IP** protocol. The **ARP** protocol is used to to map IP network addresses to the hardware addresses. **IGMP** is employed to form cluster of hosts, whereas **ICMP** is employed to send error messages and operational data indicating by hosts.

There are many ports which run different applications. The transport layer is used to establish connection among different apps using **TCP** or **UDP** Protocol. A simple example would be TCP/UDP protocols which are used to connect to various processes running at different ports.

Session layer is on top of Transport layer which ensures all the media such as images, videos or audio get transmitted as a stream of data.

Presentation layer ensures data compression and makes it easy to transfer data from client to server and vice versa.

The application layer is on top of the stack and here everything is abstracted. The client and server talk to each other using HTTP protocol.

In every layer from top to bottom a header and trailer is added to data. In application layer we assume only data and as we move down the stack headers and trailer are added. The data link layer converts data frame to packets and eventually it handles packets to physical layer.

In the next post we will discuss in detail about the data link layer.