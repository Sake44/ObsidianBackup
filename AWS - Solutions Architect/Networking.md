## Networking defined
Networking is how you connect computers around the world and allow them to communicate with one another. In this course, you’ve already seen a few examples of networking. One is the AWS Global Infrastructure. AWS has built a network of resources using data centers, Availability Zones, and Regions. 

### CIDR notation
192.168.1.30 is a single IP address. If you want to express IP addresses between the range of 192.168.1.0 and 192.168.1.255, how can you do that?
 
One way is to use CIDR notation. CIDR notation is a compressed way of representing a range of IP addresses. Specifying a range determines how many IP addresses are available to you.

![The last number '24' specifies that the first 24 bits of the IP address are fixed, and the last 8 bits are flexible.](Exported%20image%2020250315115722-0.png)   
It begins with a starting IP address and is separated by a forward slash (the _/_ character) followed by a number. The number at the end specifies how many of the bits of the IP address are fixed. In this example, the first 24 bits of the IP address are fixed. The rest (the last 8 bits) are flexible.
 
The higher the number after the /, the smaller the number of IP addresses in your network. For example, a range of 192.168.1.0/24 is smaller than 192.168.1.0/16.

- You can assign block sizes between /28 (16 IP addresses) and /16 (65,536 IP addresses). Amazon VPC supports IPv4 and IPv6 addressing and it has different CIDR block size limits for each.
- By default, all VPCs and subnets must have IPv4 CIDR blocks—you can't change this behavior. You can optionally associate an IPv6 CIDR block with your VPC.
- AWS IPv6 subnets always have a fixed size of /64.

There's a linux utility tool to calculate gatewaty, broadcast, first IP available, etc.. (ipcalc)

### Subnet mask
A subnet mask is a 32-bit number used for determining if a host is on a local subnet. It is created by setting host bits to all zeroes and setting network bits to all ones.

In a 32-bit IPv4 address, the subnet mask defines which bits of the address represent the network and subnet identifiers.

In networking, there are three main types of network protocols:

- Network management protocols
- Network communication protocols
- Network security protocols

### Network Communications Protocol
 
Communication protocols determine the formats and rules used to transfer data over the network. This applies to both hardware and software. Communication protocols also handle authentication and error detection as well as the syntax, synchronization, and semantics that both analogue and digital communications must abide by to function.

- HTTP: Hypertext transfer protocol (HTTP)(opens in a new tab) is an application layer protocol that allows the browser and server to communicate.
- TCP – Transmission Control Protocol (TCP)(opens in a new tab) separates data into packets that can be shared over a network. These packets can then be sent by devices like switches and routers to the designated targets.
- UDP – User Datagram Protocol (UDP)(opens in a new tab) works in a similar way to TCP, sending packets of data over the network. The key difference between the two is that TCP ensures that a connection is made between the application and server, but UDP does not.
- IRC – Internet Relay Chat (IRC)(opens in a new tab) is a text-based communication protocol. Software clients are used to communicate with servers and send messages to other clients. This protocol works well on networks with a large number of distributed machines.

#### Network Management Protocols
 
Network management protocols define the policies and procedures used to monitor, manage, and maintain your network. This ensures stable communication and optimal performance for your network, and these protocols can be applied to all devices on your network (computers, switches, routers and servers).
 
Management protocols help to:

- Troubleshoot connections between host and client devices.
- Provide connection status, availability, packet or data loss, and so on related to the health of your network connection.

Common network management protocols:

- SNMP – Simple Network Management Protocol (SNMP)(opens in a new tab) is used to monitor and manage network devices. This TCP-based protocol adds visibility and the ability to modify endpoints which alter behaviour of devices across the network. SNMP relies on the use of agents to collect and send data to an overarching SNMP manager, which in turn queries agents and gets their responses.
- ICMP – Internet Control Message Protocol (ICMP)(opens in a new tab) is primarily used for diagnostic purposes. Managed devices on the network can use this protocol to send error messages, providing information regarding network connectivity issues between devices.

#### Network Security Protocol
 
Network security protocols ensure that data traffic on your network is secure. These protocols define how the network secures data from malicious attempts. This protects the data from unauthorized users, services, or devices that access your network data.
 
Network security protocols rely on encryption and cryptography to secure data.
 
Common security protocols:

- SSL – A Secure Sockets Layer (SSL)(opens in a new tab) is a network security protocol primarily used for ensuring secure internet connections and protecting sensitive data. This protocol can allow for server/client communication as well as server/server communication. Data transferred with SSL is encrypted to prevent it from being readable.==
- SFTP – Secure File Transfer Protocol (SFTP)(opens in a new tab), as its name might suggest, is used to securely transfer files across a network. Data is encrypted and the client and server are authenticated.
- HTTPS – Secure Hypertext Transfer Protocol(opens in a new tab) is the secure version of HTTP. Data sent between the browser and server are encrypted to ensure protection.

**IPv4**
 
IPv4 addresses are a 32-bit number and are represented by dotted decimal notation that consists of four numbers from 0 to 255. The numbers are separated by a period, and the bit between the period is called an octate. IPv4 starts with 0.0.0.0 and ends with 255.255.255.255, providing a little over 4.2 billion IP addresses.

Public
 
==The IPv4 range is split using classful addressing into smaller ranges.==

1. ==The first range, Class A starts at 0.0.0.0 and ends at 127.255.255.255, providing over 2.1 billion IP address.==
2. ==Then second range, Class B starts at 128.0.0.0 and ends at 191.255.255.255, providing a little over 1 billion IP address.==
3. ==The third range, Class C, starts at 192.0.0.0 and ends at 223.255.255.255, providing a little over 2 million IP address.==
4. ==There are also Class D and Class E IP ranges.==
 
==Private==
 
==There were also ranges created for private networks. These IP addresses cannot communicate over the internet and they are private. The private IPv4 addresses were also broken down into ranges.==

1. ==Class A is 10.0.0.0 - 10.255.255.255 providing one single Class A IP addresses.==
2. ==Class B is 172.16.0.0 - 172.31.255.255 providing 16 Class B IP addresses.==
3. ==Class C is 192.168.0.0 - 192.168.255.255  providing 256 Class C IP addresses.==

**Useful links**  
Refer to the following links to learn more about the topics covered in the course. 

- [AWS re:Post](https://repost.aws/)
- [Networking foundations](https://aws.amazon.com/products/networking/networking-foundations/?nc=sn&loc=2&dn=4)
- [Hybrid connectivity](https://aws.amazon.com/products/networking/hybrid-connectivity/?nc=sn&loc=2&dn=3)
- [Edge networking](https://aws.amazon.com/products/networking/edge-networking/?nc=sn&loc=2&dn=2)
- [Application networking](https://aws.amazon.com/products/networking/application-networking/?nc=sn&loc=2&dn=1)
- [Internet Assigned Numbers Authority (IANA)](https://www.iana.org/numbers)
- [Address blocks](https://en.wikipedia.org/wiki/List_of_assigned_/8_IPv4_address_blocks)
- [Private Addresses RFC1918](https://tools.ietf.org/html/rfc1918)
- [Understanding IP addressing and CIDR charts](https://www.ripe.net/about-us/press-centre/understanding-ip-addressing)
- [Stanford: Introduction to Computer Networking(opens in a new tab)](https://web.stanford.edu/class/cs101/network-1-introduction.html)
- [How Amazon VPC Works(opens in a new tab)](https://docs.aws.amazon.com/vpc/latest/userguide/how-it-works.html)
- [Wikipedia: Classless Inter-Domain Routing(opens in a new tab)](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)
- [CIDR.xyz: An interactive IP Address and CIDR Range Visualizer](https://cidr.xyz/)
