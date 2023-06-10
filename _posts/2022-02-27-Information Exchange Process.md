---
title: Information Exchange Process
date: 2022-02-27 09:10:50 +0600
categories: [Academics,Networking]
tags: [networking]     # TAG names should always be lowercase
author: Nazia Shehnaz Joynab
toc: true
pin: false
comments: true
---

Information flow:
 The flow of information is from the top layer (usually application layer) down to the physical layer at the information source node; and from the physical layer up to the application later at the destination node as illustrated in the figure below. The information exchange process occurs between peer OSI layers. Each layer in the source system adds control information to data and each layer in the destination system analyzes and removes the control information from that data.

<img src="https://user-images.githubusercontent.com/59027621/148686943-31194bb8-0224-4d39-8854-a620c07a1665.gif" width="300px" height="300px"><img src="https://user-images.githubusercontent.com/59027621/148686980-b9c8bc3b-8835-4abd-b954-29409bded698.gif" width="500px" height="300px">

from figure 2
> System A has data from a software application to send to System B.

> the data is passed to the application layer.

> The application layer in System A then adds any control information required by the peer layer in system B/ application layer in System B by prepending a header to the data.

> The resulting information unit (a header and the data) is passed to the presentation layer, which prepends its own header containing control information intended for the presentation layer in System B.

> The information unit grows in size as each layer prepends its own header (and in some cases a trailer) that contains control information to be used by its peer layer in System B.

> At the physical layer, the entire information unit is placed onto the network medium.

> The physical layer in System B receives the information unit and passes it to the data-link layer. The data link layer in System B then reads the control information contained in the header prepended by the data link layer in System A. The header is then removed, and the remainder of the information unit is passed to the network layer.

> Each layer performs the same actions:

- The layer reads the header from its peer layer
- strips it off
- passes the remaining information unit to the next highest layer.

> After the application layer performs these actions, the data is passed to the recipient software application in System B, in exactly the form in which it was transmitted by the application in System A.

| **Layer Name**                                               | **Work**                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **physical layer** (hop to hop delivery of individual bits (1’s and 0’s) (Protocol Data Unit)) | This layer represents the **physical medium** which is carrying the **traffic** between two nodes.<br/>In the case of **Ethernet**, bits are transferred in the form of **electric pulses**.<br />In the case of **Wifi**, bits are transferred in the form of **radio waves**. <br />In the case of **Fiber**, bits are transferred in the form of **pulses of light**. <br />Aside from the physical cable, **Repeaters and Hubs** also operate at this layer. |
| **Data Link Layer**(hop to hop delivery of frames (Protocol Data Unit))<br/>responsible to organize bits into frames and provide them from hop-to-hop. | ****Layer 2 will group together 1’s and 0’s sent from the **physical layer into chunks known as Frames**.<br/>The **Network Interface Card (NIC)** that you plug your **Ethernet wire** into **handles the Layer 2 functionality**. It receives **signals** from the wire, and **transmits** signals on to the wire.<br />Your **WiFi NIC** works the same way, **receiving and transmitting radio waves** which are then interpreted as a series of **1’s and 0’s**.<br />There is an **addressing system** that exists at **Layer 2** known as the **Media Access Control address**, or MAC address. The MAC address uniquely **identifies each individual NIC**. Each NIC is **pre-configured** with a MAC address by the **manufacturer**; in fact, it is sometimes referred to as the **Burned In Address (BIA)**.<br />A **Switch** also operates at this layer. A Switch’s primary responsibility is to facilitate communication **within** **Networks**.**** |
| **Network layer**(host to host/end to end delivery of packets (Protocol Data Unit))<br/>responsible for the delivery of individual packets from source to destination. | **addressing scheme used** - **Internet Protocol address, or the IP Address. logically** identifies **every node** connected to the Internet. <br />It is considered **logical** because an **IP address is not a permanent identification of a computer.** Unlike the MAC address which is considered a physical address, the IP address is not burned into any computer hardware by the manufacturer.<br />Routers are Network Devices that operate at Layer 3 of the OSI model. **A Router’s primary responsibility is to facilitate communication** **between** **Networks**. As such, a Router creates a boundary between two networks. In order to communicate with any device not directly in your network, a router must be used. |
| **transport layer**(process to process or service to service delivery of message/segments (Protocol Data Unit) and error recovery.) | The **Transport layer** of the OSI model is responsible for **distinguishing network streams.**At any given time on a user’s computer there might be an **Internet browser** open, while **music is being streamed**, while a **messenger or chat app is running.** Each of these applications are **sending and receiving data** from the Internet, and all that data is arriving in the form of **1’s and 0’s** on to that computer’s NIC.Something has to exist in order to distinguish which **1’s and 0’s** belong to the messenger or the browser or the streaming music. That “something” is Layer 4:<img src="https://lh3.googleusercontent.com/FQH5li3eUb-hDIISfW0RUFCoxDT4WKLePSng6H8o19v7dFnW4d3zP2JrbSsDcoCBgbJKYCD12zk77TWVzKk5fc27SnFvu8uNjLxyvtgOSJyxW49VuHcSbXa2Cd2mH9ktHf45AATW" width="500px" height="300px"><br />**Layer 4 accomplishes this by using an addressing scheme known as Port Numbers**.Specifically, two methods of distinguishing network streams exist. They are known as the Transmission Control Protocol (TCP), or the User Datagram Protocol (UDP). |
| Session layerResponsible for<br />> **Dialog control and synchronization**.<br /> > To **establish, manage, synchronize and terminate sessions** between **end-user application processes**. | The main functions of the session layer are as follows −<br />**1. Dialog Control<br />**The session layer behaves as a **dialog controller**.<br />It allows **two communication machines** to enter into a dialog.<br />It permits communication in either **half-duplex (one way at a time)** or **full-duplex (two ways at a time)** mode of communication.<br />**2. Synchronization<br />**This layer permits a **process to add checkpoints** which are referred to as **synchronization points** into the **stream of data**.<br />If a system is sending a file of **2500** pages, It is advisable to add **checkpoints after every 100** to ensure that a **100-page unit** is successfully **received and acknowledged** independently.<br />In this case, if a **crash happens during transmission of page number 824;** then retransmission begins on page **801**. There is no need to retransmit pages 1 to 800 pages.<br />**3. Token Management**<br />This layer is also responsible for managing tokens through which it prevents two users attempting the same critical operation. |
| **presentation layer**                                       | responsible for **translation, compression, and encryption**.<br/>The presentation layer is located at the sixth level of the OSI model, it is responsible for the **delivery and formatting of information to the application layer for further processing or display**. This type of service is needed because different computer architectures use different data representations. In contrast to providing transparent data transport at the fifth level, the presentation layer handles all issues related to **data presentation and transport,** including **translation, encryption, and compression**. |
| **application layer**<br />responsible for providing services to the user.Allows access to network resources to application users. | The Application Layer interface directly interacts with applications and provides common web application services. |

<img src="https://user-images.githubusercontent.com/59027621/148687562-9c3302cb-def9-4507-b2d4-acd71f2a6520.png" width="400px" height="300px"><img src="https://user-images.githubusercontent.com/59027621/148687565-eecd21ed-89d6-4796-a765-39120ee5ac7e.png" width="500px" height="300px">

| **OSI Model**                                                | **TCP/IP model**                                             |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| It is developed by ISO (International Standard Organization) | It is developed by ARPANET (Advanced Research Project Agency Network). |
| OSI model provides a clear distinction between interfaces, services, and protocols. | TCP/IP doesn’t have any clear distinguishing points between services, interfaces, and protocols. |
| OSI refers to Open Systems Interconnection.                  | TCP refers to Transmission Control Protocol.                 |
| OSI uses the network layer to define routing standards and protocols. | TCP/IP uses only the Internet layer.                         |
| OSI follows a vertical approach.                             | TCP/IP follows a horizontal approach.                        |
| OSI layers have seven layers.                                | TCP/IP has four layers.                                      |
| OSI model, the transport layer is only connection-oriented.  | A layer of the TCP/IP model is both connection-oriented and connectionless. |
| In the OSI model, the data link layer and physical are separate layers. | In TCP, physical and data link are both combined as a single host-to-network layer. |
| Session and presentation layers are not a part of the TCP model. | There is no session and presentation layer in TCP model.     |
| The minimum size of the OSI header is 5 bytes.               | Minimum header size is 20 bytes.                             |

![osi vs tcp2](https://user-images.githubusercontent.com/59027621/148687936-b96520f5-c5d1-4729-bb54-b5b3c619dfa1.png)

## ADDRESSING

| Four levels of addresses | employing the TCP/IP protocols                               |
| ------------------------ | ------------------------------------------------------------ |
| physical                 | Underlying physical networks in the physical +data link layer. |
| logical                  | Ip and other protocols under network layer                   |
| port                     | SCTP, TCP, UDP protocols under transport layer               |
| specific                 | Processes under application layer                            |

![hrllo](https://user-images.githubusercontent.com/59027621/148687707-0633dcac-0847-4a80-90b4-c90172055dc3.jpg)

> A part of an internet with \two routers connecting three LANs.
> Each device (computer or router) has a pair of addresses (logical and physical) for each connection.
> In this case, each computer is connected to only one link and therefore has only one pair of addresses.
> Each router, however, is connected to three networks (only two are shown in the figure). So each router has three pairs of addresses, one for each connection.

> The computer with logical address A and physical address 10 needs to send a packet to the computer with logical address P and physical address 95.

> The sender encapsulates its data in a packet at the network layer and adds two logical addresses (A and P). The network layer, however, needs to find the physical address of the next hop before the packet can be delivered.

> The network layer consults its routing table and finds the logical address of the next hop (router 1) to be F.

> Another protocol, Address Resolution Protocol (ARP) finds the physical address of router 1 (20) that corresponds to its logical address(F). Now the network layer passes this address to the data link layer, which in turn, encapsulates the packet with physical destination address 20 and physical source address 10.

> Router 1 decapsulates the packet from the frame to read the logical destination address P. Since the logical destination address(P) does not match the router’s logical address(F), the router knows that the packet needs to be forwarded.

> The router consults its routing table and ARP to find the physical destination address of the next hop (router 2), creates a new frame, encapsulates the packet, and sends it to router 2.

> Note the physical addresses in the frame. The source physical address changes from 10 to 99. The destination physical address changes from 20 (router 1 physical address) to 33 (router 2 physical address).

> The logical source and destination addresses must remain the same; otherwise the packet will be lost. At router 2 we have a similar scenario. The physical addresses are changed, and a new frame is sent to the destination computer.

> When the frame reaches the destination, the packet is decapsulated. The destination logical address P matches the logical address of the computer.

> The data are decapsulated from the packet and delivered to the upper layer. Note that although physical addresses will change from hop to hop, logical addresses remain the same from the source to destination.

![hrllo2](https://user-images.githubusercontent.com/59027621/148687740-748b8f06-7aa0-4351-b2d5-153939fb9289.jpg)

To show that data from process a needs to be delivered to process j, and not k, the transport layer encapsulates data from the application layer in a packet and adds two port addresses (a and j), source and destination. The packet from the transport layer is then encapsulated in another packet at the network layer with logical source and destination addresses (A and P). Finally, this packet is encapsulated in a frame with the physical source and destination addresses of the next hop. We have not shown the physical addresses because they change from hop to hop inside the cloud designated as the Internet. Note that although physical addresses change from hop to hop, logical and port addresses remain the same from the source to destination.

A port address is a 16-bit address represented by one decimal number as shown.753—A port address is a 16-bit address represented by one decimal number as shown.

Service primitives :
Lcrsd

![service primitives](https://user-images.githubusercontent.com/59027621/148687797-1bcb2115-adbc-4701-ab34-b218798591ee.jpg)
