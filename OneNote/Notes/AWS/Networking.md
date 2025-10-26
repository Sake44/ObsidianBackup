**Networking defined**  
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
