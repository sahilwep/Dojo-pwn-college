# Talking HTTP 

## www :
- `www`(world wide web) is collection of websites or web-pages stores in web servers and connected to local computers through internet.

## Static HTTP vs Dynamic HTTP :

* Static HTTP : Static HTTP mean once our browser request something it download into the the browser and display it.
* Dynamic HTTP : Dynamic HTTP mean The real time interaction with web, suppose we watch some videos then our browser will download & render it and show us in real time, or we fetch the time from internet and it increment at every second by real time interaction.  
  

```js
// static Request :
HTTP /cat.gif HTTP/1.0 
// static Response :
HTTP /1.0 200 OK
----------------------------------------
// Dynamic Request :
GET /time?tz=UTC HTTP/1.0
// Dynamic Response :
HTTP/1.0 200 OK
Content-Type: text/plain
Content-length: 19

2023-02-19 10:22:23 
```

## Internet :
* Internet is backbone for www, in order for the www work it need some sort of system or way of transmitting data from one system to another, and the way that work is internet.
* Internet is a way to transmitting data from one device to another, to possible this we need inter-connection between every devices and this will be possible with Internet.
* To Communicate b/w two devices we can use any wire or wireless device and connect both devices then we can send any message into the network. but what if we have to communicate b/w two devices without wires or wireless medium. Here Internet comes, Internet is Distributed system of machine, may be we are not directly connected with our destination device but we are connected with those device that connected with our destination device, then in this case we can use the another device as a way to send any message to our destination devices. 
* We can say internet is `Network of Networks`.

## Abstraction of Network :
* Network is an abstraction of layers.
> TCP/IP Flow
![Model flow ](model-flow.png)
 
* **link layer** : link layer is bottom layer or we can say the physical connected layer, every device that comes into internet is connected with some sort of wire or wireless medium that comes under the link layer.

* **Internet Layer** : This layer responsible for finding the right computer on the network. Consist of - IP, ICMP, ARP etc.   

* **Transport Layer** : This layer responsible for the rules and protocols that find the right program. consist of - TCP, UDP etc.

* **Application Layer** : This layer deals with how we are going to talk with our programs. consist of HTTP, SSH, FTP etc.

## RFC-1945 :
* RFC-1945 Request for comments that defines `HTTP : hyper text transfer protocol` .
* The Hypertext Transfer Protocol (HTTP) is an application-level    protocol with the lightness and speed necessary for distributed,    collaborative, hypermedia information systems. It is a generic,    stateless, object-oriented protocol which can be used for many tasks,    such as name servers and distributed object management systems,    through extension of its request methods (commands). A feature of    HTTP is the typing of data representation, allowing systems to be    built independently of the data being transferred.
* 