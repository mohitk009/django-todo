---
title: "The webman of website — HTTP"
datePublished: Sun Jan 31 2021 10:44:16 GMT+0000 (Coordinated Universal Time)
cuid: cldva6xh800r4vonv2c529pm4
slug: the-webman-of-website-http-831e71105d74
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1675837184222/aec02b52-736d-43af-b82f-3ec0181f2e4b.png

---

Hyper Text Transfer Protocol (HTTP) is a protocol(set of rules) through which client and server can interact.

The client wants some information from the Internet and types in the URL of any website. The browser creates an HTTP request which is sent to server. The web browser of server reads the HTTP requests, the server side maps url to specific web document on it’s machine. The response which is HTML is displayed to client as a beautiful web page.

response from server under network tag in Inspect elements

The response sent by server can be viewed by “Inspect” in Google Chrome under the network tabs.

Usually GET, POST and PUT are used commonly. The request method like **POST** send the data in body instead of headers (**used to send/upload data to server**) while **GET method** sends data in headers itself (**used to just fetch data & doesn’t modifies it**). The **PUT method** just updates the data.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675837177103/3a600288-f28f-444e-a4cb-8e6e10597292.png)

google website has no image in preview tab

For Instance, take a look at html that was sent by server under response tab. We can find that despite having <img> tags, the server didn’t load images under preview tab. But on looking at other responses, we find out that there are some images in seperate response under Name under Network tab.

The above example just fetched the elements using GET request. Now if we encounter any form or password or we have to set status on social media, we generally have to send the data/ modify the document on the server. For that we use the POST request.

**HTTP is a stateless protocol.** It means that it can only fetch single resource at a time. Each request is treated as an individual request.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675837180057/875966eb-38e4-4cd3-9a40-bceb5f5a118c.png)

POST request displaying username password in header body

You might have noticed 200 status codes in responses. These codes have some meaning attached to it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675837181841/65d79b5b-5747-4bba-a920-f0c7e5f8700b.jpeg)

Error Codes Meaning

There are different codes that are recieved while accessing website. Most common are 404 page not found , 200 status ok , 500 internal server error.

If you try to look at network tab when you visit sites with **http protocol** instead of **https** you will notice you would be redirected with response code 3xx

Apart from this, there is a command line tool which is able to recieve and send http request/response for linux users. It’s known as **cURL**

**telnet 192.168.1.1 80** #connects to the ip of server ; 80 is HTTP port

after connection gets established, we can use GET, POST or any other method in order to request respone from server

**GET /index.html HTTP/1.0**

The response contains **status line & response header** along with **response body.**