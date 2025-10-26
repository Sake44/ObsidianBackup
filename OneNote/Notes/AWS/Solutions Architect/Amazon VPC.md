A virtual private cloud (VPC) is an isolated network that you create in the AWS Cloud, similar to a traditional network in a data center. When you create an Amazon VPC, you must choose three main factors:
 
• Name of the VPC  
• Region where the VPC will live – A VPC spans all the Availability Zones within the selected Region.  
• IP range for the VPC in CIDR notation – This determines the size of your network. Each VPC can have up to five CIDRs: one primary and four secondaries for IPv4. Each of these ranges can be between /28 (in CIDR notation) and /16 in size.
 ![When a VPC is created, you specify a CIDR block for the VPC. The VPC will span all the AZs within the selected Region.](Exported%20image%2020250315115724-0.png)

**Creating a subnet**  
After you create your VPC, you must create subnets inside the network. Think of subnets as smaller networks inside your base network, or virtual local area networks (VLANs) in a traditional, on-premises network. In an on-premises network, the typical use case for subnets is to isolate or optimize network traffic. In AWS, subnets are used to provide high availability and connectivity options for your resources. Use a public subnet for resources that must be connected to the internet and a private subnet for resources that won't be connected to the internet.
 
**High availability with a VPC**  
When you create your subnets, keep high availability in mind. To maintain redundancy and fault tolerance, create at least two subnets configured in two Availability Zones.
 
As you learned earlier, remember that “everything fails all of the time.” With the example network, if one of the Availability Zones fails, you will still have your resources available in another Availability Zone as backup.
 ![Provisioning resources in multiple AZ's provides high availability and a backup of your resources.](Exported%20image%2020250315115724-1.png)  

==When you create a subnet, you must specify the following:==

- **VPC** ==that you want your subnet to live in—in this case: VPC (10.0.0.0/16)==
- **Availability Zone** ==that you want your subnet to live in—in this case: Availability Zone 1==
- **IPv4 CIDR block for your subnet**==, which must be a subset of the VPC CIDR block—in this case: 10.0.0.0/24==

==When you launch an EC2 instance, you launch it inside a subnet, which will be located inside the Availability Zone that you choose.==

### VPC Components

#### Public Subnets
A public subnet is associated with a route table that has a route to an internet gateway. It lets you reach resources inside that subnet from the public internet by assigning public IP addresses.
Public subnets use the following:

- I**nternet gateways** allow communication between resources in your VPC and the internet.
- **Route tables** are set of rules that the VPC uses to route network traffic. In a public subnet, it includes a route to the internet gateway.
- **Public IP addresses** can be reached from the internet. 
- **Private IP addresses** are only reachable on the network.
![[Pasted image 20251026093605.png]]


#### Internet gateway
An internet gateway is a horizontally scaled, redundant, and highly available VPC component that permits communication between instances in your VPC and the internet.

An internet gateway serves two purposes: 

1. Provides a target in your route table for internet-routable traffic.
2. Protects IP addresses on your network by performing network address translation (NAT).

To activate internet connectivity for your VPC, you must create an internet gateway. Think of the gateway as similar to a modem. Just as a modem connects your computer to the internet, the internet gateway connects your VPC to the internet. Unlike your modem at home, which sometimes goes down or offline, an internet gateway is highly available and scalable. After you create an internet gateway, you attach it to your VPC.
An internet gateway performs network address translation (NAT) by mapping public and private IP addresses.
 ![[Pasted image 20251026094322.png]]

#### Route Tables

A route table contains a set of rules (routes) that are used to determine where network traffic is directed. When you create a VPC, it automatically has a main route table. Initially, the main route table (and every route table in a VPC) contains only a single route: This is a local route that permits communication for all the resources within the VPC.
![[Pasted image 20251026095856.png]]

You cannot delete the main route table.
- You cannot set a gateway route table as the main route table.
- You can replace the main route table with a custom subnet route table.
- You can add, remove, and modify routes in the main route table.
- You can explicitly associate a subnet with the main route table, even if it's already implicitly associated.
AWS assumes that when you create a new VPC with subnets, you want traffic to flow between them. Therefore, the default configuration of the main route table is to allow traffic between all subnets in the local network.

If you associate a subnet with a custom route table, the subnet will use it instead of the main route table. Each custom route table that you create will have the local route already inside it, allowing communication to flow between all resources and subnets inside the VPC. You can protect your VPC by explicitly associating each new subnet with a custom route table and leaving the main route table in its original default state.

![By associating subnets with a custom route table, the subnets will use the custom route table instead of the main route table.](Exported%20image%2020250315115729-5.png)
#### Private Subnets

Private subnets allow indirect access to the internet. Traffic stays within your private network. A private IP address assigned to an EC2 instance will never change unless you manually assign a new IP address on the network interface of the EC2 instance.
While you can put web-tier instances into a public subnet, we recommend that you put web-tier instances inside private subnets behind a load balancer placed in a public subnet.
![[Pasted image 20251026100805.png]]

#### Default VPC
Each AWS account comes with a default  VPC that is preconfigured for you to use immediately. You don't have to create and configure your own VPC. This diagram is a default VPC. The CIDR block for the default VPC is always a /16 subnet mask. In this example, the CIDR block of 172.31.0.0/16 means that this VPC can provide up to 65,536 IP addresses. It includes one public subnet in each Availability Zone in the Region. These subnets use a /20 subnet mask, providing 4,096 addresses per subnet. It also includes an internet gateway. The VPC uses a main route table to connect the subnets to the internet gateway.
![[Pasted image 20251026100858.png]]


#### Virtual private gateway

A virtual private gateway connects your VPC to another private network. When you create and attach a virtual private gateway to a VPC, the gateway acts as anchor on the AWS side of the connection. On the other side of the connection, you will need to connect a customer gateway to the other private network. A customer gateway device is a physical device or software application on your side of the connection. When you have both gateways, you can then establish an encrypted virtual private network (VPN) connection between the two sides.
 ![A virtual private gateway is the VPN endpoint on the Amazon side of your VPN connection that can be attached to a single VPC.](Exported%20image%2020250315115725-3.jpeg)  

### AWS Direct Connect
To establish a secure physical connection between your on-premises data center and your Amazon VPC, you can use AWS Direct Connect. With AWS Direct Connect, your internal network is linked to an AWS Direct Connect location over a standard Ethernet fiber-optic cable. This connection allows you to create virtual interfaces directly to public AWS services or to your VPC.
 ![With AWS Direct Connect, your network traffic remains on the AWS global network and never touches the public internet.](Exported%20image%2020250315115729-4.png)


 
### Network Access Control List (NACLs)

A network ACL is an optional layer of security for your VPC that acts as a firewall for controlling traffic in and out of one or more subnets.
Network ACLs are **stateless**, which means that responses to allowed inbound traffic are subject to the rules for outbound traffic (and the other way around).

#### Inbound and outbound IPv4 traffic
A network ACL contains a numbered list of rules.
Every VPC automatically comes with a modifiable default network ACL. By default, it allows all inbound and outbound IPv4 traffic. You can create a custom network ACL and associate it with a subnet.
![[Pasted image 20251026102041.png]]
#### Network ACL Rules
Each network ACL includes a rule whose rule number is an asterisk. This rule ensures that if a packet doesn't match any of the other numbered rules, it is denied.
Network ACLs are stateless, which means that responses to allowed inbound traffic are subject to the rules for outbound traffic (and vice versa).

#### Network ACL use case
![[Pasted image 20251026104102.png]]

### Security Groups
A security group acts as a virtual firewall for your instance to control inbound and outbound traffic. Security groups act at the network interface level, not the subnet level, and they support **Allow** rules only.
![[Pasted image 20251026103518.png]]
By default, a security group includes an outbound rule that allows all outbound traffic.
If your security group has no outbound rules, no outbound traffic originating from your instance is allowed.
![[Pasted image 20251026103732.png]]
With security group rules, you can filter traffic based on protocols and port numbers.


#### Secure EC2 instances with security groups
The next layer of security is for your EC2 instances. Here, you can create a virtual firewall called a security group. The default configuration of a security group blocks all inbound traffic and allows all outbound traffic.

![Exported image](Exported%20image%2020250315115729-6.jpeg)

You might be wondering, “Wouldn’t this block all EC2 instances from receiving the response of any customer requests?” Well, security groups are stateful. That means that they will remember if a connection is originally initiated by the EC2 instance or from the outside, and temporarily allow traffic to respond without modifying the inbound rules.
 
If you want your EC2 instance to accept traffic from the internet, you must open up inbound ports. If you have a web server, you might need to accept HTTP and HTTPS requests to allow that type of traffic into your security group. You can create an inbound rule that will allow port 80 (HTTP) and port 443 (HTTPS), as shown.


#### Comparing Security Groups and Network ACLs
A security group acts as a firewall for associated EC2 instances, controlling both inbound and outbound traffic at the instance level. Network ACLs act as a firewall for associated subnets, controlling both inbound and outbound traffic at the subnet level.

|**Security Group**|**Network ACL**|
|---|---|
|Security groups act as a firewall for associated EC2 instances, and are associated with elastic network interface implemented by a hypervisor|Network ACLs act as a firewall for associated subnets|
|Controls inbound and outbound traffic at instance level|Controls inbound and outbound traffic at subnet level|
|Supports Allow rules only|Supports both Allow and Deny rules|
|A stateful firewall|A stateless firewall|
|Needs to be manually assigned to instances|Automatically applied when instances are added to subnet|







**Resources**  
For more information, see the following resources.
 
- AWS user guide: [Configure Route Tables](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html)
- AWS user guide: [Example Routing Option](https://docs.aws.amazon.com/vpc/latest/userguide/route-table-options.html)
- AWS user guide: [Working with Route Tables](https://docs.aws.amazon.com/vpc/latest/userguide/WorkWithRouteTables.html)
- AWS user guide: [Control Traffic to Subnets Using Network ACLs](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html)
- AWS user guide: [Control Traffic to Resources Using Security Groups](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html)