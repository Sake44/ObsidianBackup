# What's Internet? 
There are a couple of ways to answer this question. First, we can describe the nuts and bolts of the Internet, that is, the basic hardware and software components that make up the Internet. Second, we can describe the Internet in terms of a networking infrastructure that provides services to distributed applications.

The Internet is a computer network that interconnects billions of computing devices
throughout the world. Indeed, the term computer network is beginning to sound a bit dated, given the many nontraditional devices that are being hooked up to the Internet. In Internet jargon, all of these devices are called #hosts or end systems.

End systems are connected together by a network of communication links and packet switches.
Different links can transmit data at different rates, with the transmission rate of a link measured in bits/second.
When one end system has data to send to another end system, the sending end system segments the data and adds header bytes to each segment. The resulting packages of information, known as packets in the jargon of computer networks, are then sent through the network to the destination end system, where they are reassembled into the original data.

A **packet switch** takes a packet arriving on one of its incoming communication links and forwards that packet on one of its outgoing communication links. The two most prominent types of switches are **routers** and **link-layer switches**. Both types of switches forward packets towards their ultimate destinations.
Link-layer switches are typically used in access networks, while routers are typically used in the network core. The sequence of communication links and packet switches traversed by a packet from the sending end system to the receiving end system is known as a **route** or **path** through
the network.

End systems access the Internet through Internet Service Providers (ISPs)
The Internet is all about connecting end systems to each other, so the #ISPs that provide access to end systems must also be interconnected.
End systems, packet switches, and other pieces of the Internet run **protocols** that control the sending and receiving of information within the Internet. **The Transmission Control Protocol (TCP) and the Internet Protocol (IP)** are two of the most important protocols in the Internet.
The Internet’s principal protocols are collectively known as #TCP/IP.
Given the importance of protocols to the Internet, it’s important that everyone agree on what each and every protocol does, so that people can create systems and products that interoperate. This is where standards come into play. Internet ­standards are developed by the Internet Engineering Task Force (**IETF**). The #IETF standards documents are called requests for comments (RFCs).

