|
|
==What== ==How== ==Why==
==An AWS [Region](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/?p=ngi&loc=2) is a geographical area that consists of two or more Availability Zones.== ==By designing infrastructure that spans two or more Availability Zones, you are designing your network to withstand global disasters.== ==There is separation between Regions ensuring that each Region is fault tolerant.==  
==An [Availability Zone](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/?p=ngi&loc=2) is one or more interconnected data centers with redundant power, networking, connectivity, and so on.==  ==One Availability Zone is one or more data centers with isolated compute, storage, network, and so on. These data centers are housed in separate facilities and sit inside different Regions. AWS also has multiple data centers across the world. You can distribute your infrastructure across multiple Availability Zones in your Region for high availability.==  ==
If one Availability Zone fails, then the other Availability Zone should remain operational. The Availability Zones are isolated from each other, but connected with high-speed redundant networking.
==
==AWS [Local Zones](https://aws.amazon.com/about-aws/global-infrastructure/localzones/?p=ngi&loc=3) are about getting AWS services closer to end-users.== ==A Local Zone deploys compute, storage, databases, and other AWS services closer to large populations.== ==Each AWS Local Zone location is an extension of a Region where you can run your latency-sensitive applications using AWS services.==
==An [edge location](https://wa.aws.amazon.com/wellarchitected/2020-07-02T19-33-23/wat.concept.edge-location.en.html) is a global service and it is an endpoint for AWS that is used for caching content. The AWS content delivery network (CDN) is Amazon CloudFront.== ==When data is requested, CloudFront takes data and caches that data at the edge location. The next time another user requests that same information, that data is already available and delivered to the user much faster because CloudFront does not have to go all the way back to the database and search for that specific information. There are more edge locations than Regions.== ==The next time another user requests that same information, that data is already available and delivered to the user much faster because CloudFront does not have to go all the way back to the database and search for that specific information. There are more edge locations than Regions.==

A foundational networking service in AWS is the ==Amazon Virtual Private Cloud (Amazon VPC)====(opens in a new tab)==. An Amazon VPC is a software-defined virtual private network. It is a service that you use to create secure private networks in AWS to host your applications and data. Your private services will run from this Amazon VPC.

==Default Amazon VPCs(opens in a new tab)== ==are created by AWS when you create your AWS account and AWS sets up the configuration for you. Amazon VPCs operate resiliently by operating in multiple Availability Zones in a specific AWS Region.==
 
==Each default Amazon VPC comes with one== ==Amazon VPC Classless Inter-Domain Range (CIDR)(opens in a new tab)====, which is a given range of IP address, and this Amazon VPC CIDR defines the start and end range of the IP address that this default Amazon VPC can use.==
 ![Diagram showing default VPC. One Region. One Default VPC. Three Availability Zones (A, B, and C). Each with a Public Subnet connected to a Transit Gateway that connects the default VPC to the public internet. A table is included that shows the routes in the main route table for the default VPC. Destination 172.31.0.0/16 has a Target of Local. Destination 0.0.0.0/0 has a Target of internet_gateway_id.](Exported%20image%2020250315115745-0.png)

![Diagram showing AWS Cloud with one VPC. It contains two subnets, each with a security group and EC2 instances. The Subnets each connect to their own Network ACL and Route Table. Both Route Tables connect to the router and then either to the Internet Gateway or the Virtual Private Gateway. There are seven labels describing each part.](Exported%20image%2020250315115745-1.png)

==There are seven AWS Networking Gateways.==

1. **Internet gateway** ==is an Amazon VPC component that allows communication between your computer and the internet. Applications include, Elastic Load Balancers, Amazon EC2 instances, Amazon S3, AWS Lambda and so on.==
2. **Customer Gateway** ==is a physical or software appliance that you own or manage in your on premises network. Applications include manages routing to and from your environment.==
3. **VPN Gateway** ==is the gateway on the AWS side of site-to-site VPN connection. Applications include Amazon EC2 instances, Amazon S3, Amazon RDS< Amazon Lambda, and so on.==
4. **Direct Connect Gateway** ==establishes connectivity that spans Amazon VPCs spread across multiple AWS Regions. Applications include Amazon EC2 instances, Amazon RDS, AWS Lambda, and so on.==
5. **NAT Gateway** ==is a network address translation service that enables instances in a private subnet to connect to services outside your VPC. Applications include Amazon EC2 instances, Amazon RDS, AWS Lambda, and so on.==
6. **AWS Transit Gateway** ==connects Amazon VPCs, AWS accounts, and on premises networks to a single gateway. Applications include Amazon VPC connections, AWS VPN connection, AWS Direct Connect.==
7. **Virtual gateway** ==allows resources that are outside of your mesh network to communicate to resources that are inside. Applications include Amazon EC2, Amazon ECS, and Amazon EKS.==

**Additional resources**

- [Getting started with Amazon VPC](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-getting-started.html#create-vpc)
- [Best practices for configuring network interfaces](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/best-practices-for-configuring-network-interfaces.html)