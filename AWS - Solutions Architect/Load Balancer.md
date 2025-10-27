## Availability 
The availability of a system is typically expressed as a percentage of uptime in a given year or as a number of nines. In the following table is a list of availability percentages based on the downtime per year and its notation in nines. 

| **Availability (%)**                            | **Downtime (per year)** |
| ----------------------------------------------- | ----------------------- |
| 90% (one nine of availability)                  | 36.53 days              |
| 99% (two nines of availability)                 | 3.65 days               |
| 99.9% (three nines of availability)             | 8.77 hours              |
| 99.95% (three and a half nines of availability) | 4.38 hours              |
| 99.99% (four nines of availability)             | 52.60 minutes           |
| 99.995% (four and a half nines of availability) | 26.30 minutes           |
| 99.999% (five nines of availability)            | 5.26 minutes            |
 
To increase availability, you need redundancy. This typically means more infrastructure—more data centers, more servers, more databases, and more replication of data. You can imagine that adding more of this infrastructure means a higher cost. Customers want the application to always be available, but you need to draw a line where adding redundancy is no longer viable in terms of revenue.

### Resources - Availability
For more information, see the following resources:

- AWS whitepaper: [High availability and scalability on AWS(opens in a new tab)](https://docs.aws.amazon.com/whitepapers/latest/real-time-communication-on-aws/high-availability-and-scalability-on-aws.html)
- AWS documentation: [Reliability Pillar – AWS Well-Architected Framework(opens in a new tab)](https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/welcome.html)
- AWS website: [Amazon EC2 Auto Scaling](https://aws.amazon.com/ec2/autoscaling/)

### Load Balancer
Load balancing refers to the process of distributing tasks across a set of resources. You can use a load balancer to distribute the requests across all the servers hosting the application.
 
To do this, the load balancer needs to take all the traffic and redirect it to the backend servers based on an algorithm. The most popular algorithm is **round robin**, which sends the traffic to each server one after the other.
![[Pasted image 20251027153048.png]]

### ELB features
The ELB service provides a major advantage over using your own solution to do load balancing. Mainly, you don’t need to manage or operate ELB. It can distribute incoming application traffic across EC2 instances, containers, IP addresses, and Lambda functions. Other key features include the following:
 
•**Hybrid mode –** Because ELB can load balance to IP addresses, it can work in a hybrid mode, which means it also load balances to on-premises servers.  
•**High availability –** ELB is highly available. The only option you must ensure is that the load balancer's targets are deployed across multiple Availability Zones.  
•**Scalability –** In terms of scalability, ELB automatically scales to meet the demand of the incoming traffic. It handles the incoming traffic and sends it to your backend application.

### Health checks
Monitoring is an important part of load balancers because they should route traffic to only healthy EC2 instances. That’s why ELB supports two types of health checks as follows:
 
•Establishing a connection to a backend EC2 instance using TCP and marking the instance as available if the connection is successful.  
•Making an HTTP or HTTPS request to a webpage that you specify and validating that an HTTP response code is returned.
 
After determining the availability of a new EC2 instance, the load balancer starts sending traffic to it. If ELB determines that an EC2 instance is no longer working, it stops sending traffic to it and informs Amazon EC2 Auto Scaling. It is the responsibility of Amazon EC2 Auto Scaling to remove that instance from the group and replace it with a new EC2 instance. Traffic is only sent to the new instance if it passes the health check.
![[Pasted image 20251027153109.png]]

### Application Load Balancer
An Application Load Balancer functions at Layer 7 of the Open Systems Interconnection (OSI) model. It is ideal for load balancing HTTP and HTTPS traffic. After the load balancer receives a request, it evaluates the listener rules in priority order to determine which rule to apply. It then routes traffic to targets based on the request content.

#### Routes based on request data
 An Application Load Balancer makes routing decisions based on the HTTP and HTTPS protocol.
#### Sends response to the client
An Application Load Balancer can reply directly to the client with a fixed response, such as a custom HTML page. It can also send a redirect to the client.
#### Uses TLS offloading
An Application Load Balancer understands HTTPS traffic. To pass HTTPS traffic through an Application Load Balancer, an SSL certificate is provided one of the following ways:
- Importing a certificate by way of IAM or ACM services
- Creating a certificate for free using ACM
#### Authenticates Users
An Application Load Balancer can authenticate users before they can pass through the load balancer. The Application Load Balancer uses the OpenID Connect (OIDC) protocol and integrates with other AWS services to support protocols, such as the following:

- SAML
- Lightweight Directory Access Protocol (LDAP)
- Microsoft Active Directory
- Others
#### Secures Traffic
To prevent traffic from reaching the load balancer, you configure a security group to specify the supported IP address ranges.
#### Sticky sessions
If requests must be sent to the same backend server because the application is stateful, use the sticky session feature. This feature uses an HTTP cookie to remember which server to send the traffic to across connections.
### Network Load Balancer
A Network Load Balancer is ideal for load balancing TCP and UDP traffic. It functions at Layer 4 of the OSI model, routing connections from a target in the target group based on IP protocol data.

Main features in Network Load Balancer (NLB): 
1. Sticky sessions: Routes requests from the same client to the same target.
2. Low Latency
3. Source IP address: Preserves the client-side source IP address.
4. Static IP Support
5. Elastic IP address support
6. DNS failover: Uses Amazon Route 53 to direct traffic to load balancer nodes in other zones.
 
### Gateway Load Balancer
A Gateway Load Balancer helps you to deploy, scale, and manage your third-party appliances, such as firewalls, intrusion detection and prevention systems, and deep packet inspection systems. It provides a gateway for distributing traffic across multiple virtual appliances while scaling them up and down based on demand.
![[Pasted image 20251027154319.png]]

### Resources
For more information, see the following resources:

- AWS website: [Elastic Load Balancing features](https://aws.amazon.com/elasticloadbalancing/features/#Product_comparisons)
- AWS website: [AWS Certificate Manage](https://aws.amazon.com/certificate-manager/)
- AWS documentation: [Authenticate users using an Application Load Balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/listener-authenticate-users.html)
- AWS developer guide: [How AWS WAF works](https://docs.aws.amazon.com/waf/latest/developerguide/how-aws-waf-works.html)
- AWS blog: [Introducing AWS Gateway Load Balancer](https://aws.amazon.com/blogs/aws/introducing-aws-gateway-load-balancer-easy-deployment-scalability-and-high-availability-for-partner-appliances/)