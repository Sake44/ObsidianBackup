At AWS, networking is managed at the subnet level, and subnets are first created  
as private subnets with no direct access to the outside world. Subnets that reside on your private networks at AWS are hosted in a virtual private cloud (VPC).  
Only by adding **gateway services** to a VPC and route tables entries are subnets able to be accessed from either the Internet or from external network location.
 
1. Each subnet’s ingress and egress traffic can be controlled by subnet firewalls

called network ACLs that define separate stateless rules for inbound and  
outbound packet flow.

1. Each EC2 instance hosted on a subnet is protected by a firewall called a security group, which defines what inbound traffic is allowed into the instancee and where outbound traffic is allowed to flow to.
2. VPCs can be further protected by deploying the AWS Network Firewall,

providing control over all network traffic, such as blocking outbound **Server**  
**Message Block (SMB)** requests, bad URLs, and specific domain names.

1. VPC flow logs can be enabled to capture network traffic for the entire VPC,

for a single subnet, or for a network interface.