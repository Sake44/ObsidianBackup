---
---
To be ready for this certification we need few things:

1\. Use the AWS Well-Architected Tool: https://www.wellarchitectedlabs.com/well-architectedtool/
2\. Complete AWS security workshops: https://awssecworkshops.com/
3\. Simulating test: [Simulate testing](https://d1.awsstatic.com/training-and-certification/docs-sa-assoc/AWS-Certified-Solutions-Architect-Associate_Sample-Questions.pdf)
4\. Browse the AWS Architecture Center: \_The AWS Architecture Center\_([Architecture Center](https://aws.amazon.com/architecture/)) has many examples of how to deploy reference architecture for analytics, compute and HPC deployments, and databases, to name just a few.

## History

If you haven’t heard of the National Institute of Standards and Technology (NIST), a
branch of the U.S. government, you’re not alone. Around 2010, NIST began documenting
the emerging public cloud. After consulting the major cloud vendors, it released
an initial report in June 2011, Special Publication 800-145, “The NIST Definition of
Cloud Computing”

Below the essential NIST's characteristics

1. **On-demand Self-Service:** _At AWS, a virtual server can be ordered and operational in under 5 minutes._
2. **Broad Network Access:** At AWS, applications and services can be made publicly available, or they can remain completely private. Virtual private network (VPN) connections from your place of work to AWS are commonplace. Customers can also order an AWS Direct Connect connection, a private fiber connection to AWS resources running at speeds up to 100 Gbps. Depending on the type of application you’re hosting in the AWS cloud, high-speed network access may be essential.
3. **Resource Pooling:** Without a massive pool of compute resources, AWS would not be able to allow customers to dynamically allocate compute resources to match their performance requirements workloads.
4. **Rapid Elasticity:** At AWS, compute and storage resources are defined as elastic. Workloads running in the AWS cloud for Amazon EC2 instances or Amazon Elastic Container Service (Amazon ECS) deployments have the capability to automatically scale using a scaling policy to dynamically resize an Auto Scaling group of web or application servers using several scaling policies, including
5. **Measured Service:** You pay for what you use. The management of cost is one of the most important task to understand and control.

### Cloud Provider Responsibilities

![[image.170.png]]

AWS has published service-level-agreements (SLAs) for most AWS cloud services.
Current details on the SLAs offered by AWS can be viewed at
[SLAs](https://aws.amazon.com/legal/service-level-agreements). AWS defines its commitments in each SLA about security, compliance, and overall operations. The challenge is to live up to these agreements when all services fail from time to time. Each cloud service SLA contains details about the acceptable outage times and the responsibilityof the cloud provider when outages occur. Each SLA also contains statements about
their level of responsibility for events outside the cloud provider’s control. SLAs commonly use terms such as “best effort” and “commercially reasonable effort.”

**AWS is responsible for overall service operation and deployment, service orchestration and overall management of their cloud services, the security of the cloud components,and maintenance of each customer’s privacy**

### **Security at AWS**

As you move to AWS cloud, you need to consider some security factors:

1. **Data Security:** the reality is that your data are more secured in cloud than on-premises physical servers. All storage mediums at AWS are encrypted with the **Advanced Encryption Standard** (AES). Amazon **S3 buckets** are encrypted with keys provided by the S3 service or the Key Management Service (KMS). Data **durability** provides additional security as all data stored in AWS is stored on multiple physical locations. **Amazon S3 objects** are replicated across at least **three** separate availability zones within the selected AWS region, producing a very high level of durability.
2. **Data Privacy:** Amazon ensures that each AWS account's stored data records remain isolated from other AWS customers. Each s3 bucket is can be shared publicly but first all data records are created as a private resources.
3. **Data Control:** Customers are fully responsible for storing and retrieving their data records stored at AWS. it's customer responsibility to define the security and accessibility of all data records stored in AWS.
4. **Security Controls:** AWS Identity and Access Management (IAM) permissions policy can be defined at a very granular level to control access to all resources.

### Network Security at AWS

At AWS, networking is managed at the subnet level, and subnets are first created
as private subnets with no direct access to the outside world. Subnets that reside on your private networks at AWS are hosted in a virtual private cloud (VPC).
Only by adding **gateway services** to a VPC and route tables entries are subnets able to be accessed from either the Internet or from external network location.

1. Each subnet’s ingress and egress traffic can be controlled by subnet firewalls

		called network ACLs that define separate stateless rules for inbound and
		outbound packet flow.

2. Each EC2 instance hosted on a subnet is protected by a firewall called a security group, which defines what inbound traffic is allowed into the instancee and where outbound traffic is allowed to flow to.
3. VPCs can be further protected by deploying the AWS Network Firewall,

		providing control over all network traffic, such as blocking outbound **Server**
		**Message Block (SMB)** requests, bad URLs, and specific domain names.

4. VPC flow logs can be enabled to capture network traffic for the entire VPC,

		for a single subnet, or for a network interface.
		

### Application Security at AWS

Both web and servers application hosted at AWS are usually located on a private subnets, which are not directly accessible from the internet. Customers requesting access to the application will be directly by DNS services (Route 53) to the DNS name of the load balancer.

To have just an example we could take in consideration a tier-three web application designed to using many encryption/decryption points, like:

1. **AWS Web Application Farewell (WAF):** custom traffic filter that can be associated with an Application Load Balancer to protect against malicious traffic requests.
2. **Application Load Balancer:** An application load balancer can accept encrypted HTTPS traffic on port 443
3. **EC2 instance hosting web application:** EBS boot and data volumes can be encrypted using the AWS KMS service
4. **EC2 instance hosting server application:** EBS boot and data volumes can be encrypted using the AWS KMS service
5. **RDS DB server:** All boot and data can be encrypted using **KMS.**

![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.png]]

### Migrating Applications

When we decide to move an Application on Cloud, several decisions need to be made. There are several way to move application to AWS depending on various factors.

1. **Define a value proposition:** Start off with a defined value proposition that can be validated quickly. For developing applications you can consider to use **Cloud9,** a cloud-hosted integration environment. Starting new at AWS enables you to try out new methods to host applications, such as serverless computing, creating a mobile application using stateless components, or using DynamoDB as a NoSQL deployment instead of a SQL database.

## The AWS Well-Architected Framework

AWS introduces the Well-Architected Framework to provide guidance to help cloud architects build secure, resilient and well-performing infrastructure to host their applications.

The documentation for the Well-Architected Framework (see [Well-architected framework](http://docs.aws.amazon.com/wellarchitected/latest/framework)) also presents many key questions customers should review. It is useful to discuss these questions with the other technical team members in your company to make key decisions about your infrastructure and workloads to be hosted at AWS. Each workload to be deployed at AWS should be viewed through the lens of the Well-Architected Framework following these six pillars.

# IAM (Identity Access Management)

IAM it's a global service. When we first create the account that user is called **Root User** (has all the privileges). The root user shouldn't be use or shared.
**User** are people within your organization, and can be grouped
User permissions:
User and groups can be assigned JSON documents called policies. These policies define the **permissions** of the users.
In AWS you apply the least privilege principle: don’t give more permissions than a user needs.
![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.1.png]]

### IAM Roles for Services

Some AWS services will need to perform actions on your behalf. To do so we will assign permissions to AWS services with **IAM roles.**
A role is an identity you can create in IAM that has specific permissions. A role is similar to a user, as it is an AWS identity with permission policies that determine what identity can and cannot do in AWS. A role is intended to be assumable by anyone who needs it so it's not associated with one person.
As security tools IAM provide a Credential Report (account-level) and Access Advisor (user-level).
The reason why we use roles instead of credentials is that if our web server get hacked they can access to our credentials stored in a file. In this way they can read our Access Key and Private Access Key and able to log in our s3 account. Using roles is so much more secure cause you not store credentials in your ec2 instance.

![[Screenshot from 2024-11-16 18-11-50.png]]

## AWS IAM Guidelines &  Best Practices

1. Don't use root account except for AWS account setup
2. One physical user = One AWS User
3. Assign user to groups and assign permission to group
4. Create a strong password policy
5. Use an enforce the use of MFA
6. Create and use Roles for giving permissions to AWS Services
7. Use Access Keys for Programmatic Access (CLI/SDK)
8. Audit permissions of your account using IAM Credentials Report & IAM Access Advisor
9. NEVER share IAM users & Access Keys

### IAM Section - Summary

![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.2.png]]

# EC2 (Elastic Compute Cloud)

Is one of the most popular service AWS's offering. It's an IaaS and constists in the capability of:

1. Renting virtual machines (EC2)
2. Storing data on virtual drives (EBS)
3. Distributing load across machines  (ELB)
4. Scaling the services using an auto scaling group (ASG)

EC2 require differente configurations like:

1. Operating system
2. CPU
3. RAM
4. Storage space
5. Network, IP address
6. Firewall rules
7. Bootstrap script (launching command when a machine starts)

![[image.77.png]]

### On-demand Instances

* Pay for what you use:
	* Linux and Windows - billing per second, after the first minute
	* All other OS - billing per hour
* Has the highest cost but no upfront payment
* No long-term commitment

On-demand instances are often used to grant flexibility without any upfront payment or long-term commitment.
Are really useful for **short-term, spiky or unpredictable** workloads that cannot be interrupted. Last but not least the Applications are developed on Amazon Ec2 for the first time.

### Reserved Instances

Up to 72% discount compared to On-demand
• You reserve a specific instance attributes (Instance Type, Region, Tenancy, OS)
• Reservation Period – 1 year (+discount) or 3 years (+++discount)
• Payment Options – No Upfront (+), Partial Upfront (++), All Upfront (+++)
• Reserved Instance’s Scope – Regional or Zonal (reserve capacity in an AZ)
• Recommended for steady-state usage applications (think database)
• You can buy and sell in the Reserved Instance Marketplace
We can choose Reserved Instances if our Applications are with a steady state or predictable usage or if our Applications that require reserved capacity.
We can choose to make an upfront payments to reduce the total computing costs even further.
Within Reserved Instances we have the option to use **Standard RIs** which allow us to have a discount up to 72% off the on-demand price.
Another option are **Convertible RIs** have a discount up to 52% but allow us to change to a different RI type of equal or greater value.
One last option is to use **Scheduled RIs** to launch within the time window you define.
Reserved instances operates at region level.

### EC2 Savings Plans

Get a discount based on long-term usage (up to 72% - same as RIs)
		• Commit to a certain type of usage ($10/hour for 1 or 3 years)
		• Usage beyond EC2 Savings Plans is billed at the On-Demand price
		• Locked to a specific instance family & AWS region (e.g., M5 in us-east-1)
		• Flexible across:
		• Instance Size (e.g., m5.xlarge, m5.2xlarge)
		• OS (e.g., Linux, Windows)
		• Tenancy (Host, Dedicated, Default)

### Spot Instances

Can get a discount of up to 90% compared to On-demand
		• Instances that you can “lose” at any point of time if your max price is less than the
		current spot price
		• The MOST cost-efficient instances in AWS
		• Useful for workloads that are resilient to failure
		• Batch jobs
		• Data analysis
		• Image processing
		• Any distributed workloads
		• Workloads with a flexible start and end time
		• Not suitable for critical jobs or databases

### Spot Fleets

![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.16.png]]
		

### EC2 Spot Instance Requests

Can get a discount of up to 90% compared to On-demand
		• Define **max spot price** and get the instance while current **spot price < max**
		• The hourly spot price varies based on **offer and capacity**
		• If the current spot price > your max price you can choose to stop or terminate your instance
				with a 2 minutes grace period. 
				If we stop our instance, when our **max price** will be again **less** than spot price we can restart our instance from where we left it off.
• Other strategy: **Spot Block (No longer supported)**
		• “block” spot instance during a specified time frame (1 to 6 hours) **without interruptions**
		• In rare situations, the instance may be reclaimed
		• Used for batch jobs, data analysis, or workloads that are resilient to failures.
		• Not great for critical jobs or databases
Spot block are no longer available to new AWS Customers since July 1st 2021.

### Timing Workloads with Spot Instances and Spot Fleets

A typical use case for Spot Instances is for stateless, fault-tolerant or flexible applications. Applications such as big data, containerized workloads, CI-CD, high performance computing or test and development workloads.

### How to terminate a Spot Instances

![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.15.png]]
We can have two different types of Spot Instances's Requests:

* **One time request**: This request is valid just one time. When the instances are launched then the Spot request expire.
* **Persistent request**: This request is **persistent.** We need to remember, before to terminate/stop an instances, to cancel the Spot Request. Otherwise, spot request will be smart enough to relaunch our instances.

![[image.78.png]]

### 

### Dedicated Hosts

• A physical server with EC2 instance capacity fully dedicated to your use
• Allows you address compliance requirements and use your existing serverbound
software licenses (per-socket, per-core, pe—VM software licenses)
![[image.86.png]]

**• Purchasing Options:**
		• On-demand – pay per second for active Dedicated Host
		• Reserved - 1 or 3 years (No Upfront, Partial Upfront, All Upfront)
• Useful for software that have complicated licensing model (BYOL – Bring Your Own License) or for       companies that have strong regulatory or compliance needs
![[image.79.png]]

### EC2 Dedicated Instances

• Instances run on hardware that’s dedicated to you
• May share hardware with other instances in same account
• No control over instance placement (can move hardware after Stop / Start)
![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.13.png]]

### EC2 Instances types ([link](https://aws.amazon.com/ec2/instance-types/))

![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.3.png]]![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.4.png]]![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.5.png]]![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.6.png]]![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.6.png]]

### Security Groups

Security groups are the fundamental of network security in AWS. They control how traffic is allowed into or out of our EC2 Instances. Security Groups are **virtual firewall for your ec2 instance.** By default everything is blocked. A security groups only contain **allow** rules.
![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.7.png]]
Security groups are acting like **Firewall** on EC2 instances.
They regulate:

* Access to **Ports**
* Authorised IP ranges - IPv4 and IPv6
* Control of inbound network (from other to the instance)
* Control of outbound network (from the instance to other)

![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.8.png]]![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.9.png]]![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.10.png]]![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.11.png]]
SSH is one of the most important function. It allows you to control a remote machine, all using the command line.

### SSH Troubleshooting

If there's a **connection timeout** 90% is a security groups issue. Any timeout (not just for SSH) is related to security groups or firewall. Ensure your security group looks like this and correctly assigned to your EC2 instance.
If there's **connection refused** it means the instance is reachable, but no SSH utility is running on the instance. Try to:

* Restart your instance
* If it doesn't work , terminate the instance and create a new one. Make sure you're using **Amazon Linux 2.**

To connect to our ec2 Instance we have different ways. Since I'm using Windows 11, run this command. (Remember to be in the folder where your .pem file is saved)
```
ssh -i (.pem file name) ec2-user@(public IP Address)


```

### Ec2 Purchasing Options

![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.12.png]]

### 

### 

![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.14.png]]

### 

### Private an Public IP

Networking has two sorts of IPs. IPv4 and IPv6:
		• IPv4: 1.160.10.240
		• IPv6: 3ffe:1900:4545:3:200:f8ff:fe21:67cf
Fundamental differences between Public and Private IP Address:
Public IP:

* Means the machine can be identified on the internet.
* Must be unique across all web
* Can be geo-located easily.

Private IP:

* Private IP means the machine can be only identified on a private network  only
* The IP must be unique across a private network
* Two different private network can have the same IP address.
* Machines connect to WWW using a NAT + internet gateway (proxy)
* Only a specified range of IPs can be used as private IP

By default, your EC2 machine comes with:
		• A private IP for the internal AWS Network
		• A public IP, for the WWW.
When we are doing SSH into our EC2 machines:
		• We can’t use a private IP, because we are not in the same network
		• We can only use the public IP.
Each we stop our instance the public IP assign to the instance, when the instance will be reboot, will change. To make it not change we can have a Elastic IP and the attach it to our EC2 Instance. Always remember to terminate EC2 instance and release your Elastic IP if you don't use it. AWS will charge you also if you don't have an EC2 instance running but with a public IP address assignee. 
Overall, try to avoid using Elastic IP:
		• They often reflect poor architectural decisions
		• Instead, use a random public IP and register a DNS name to it
		• Or, as we’ll see later, use a Load Balancer and don’t use a public IP

### EC2 Placement Groups

Sometimes we want control over the ec2 instances placement strategies. We can define this strategy through placement groups.
There are three different types of Placement groups:
• Cluster—clusters instances into a low-latency group in a single Availability Zone
• Spread—spreads instances across underlying hardware (max 7 instances per
group per AZ)
• Partition—spreads instances across many different partitions (which rely on
different sets of racks) within an AZ. Scales to 100s of EC2 instances per group
(Hadoop, Cassandra, Kafka)
![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.18.png]]

![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.17.png]]![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.19.png]]

### Ec2 Networking

You can attach three different types of **virtual networking cards** on your ec2 instance:
![[image.80.png]]
**An ENI is a simple virtual network that allows:**
![[image.81.png]]

### 

Elastic Network Interfaces (ENIs) are virtual network components that are crucial to Amazon's Elastic Compute Cloud (EC2) service. They function as virtual network adapters, enabling EC2 instances to connect to a Virtual Private Cloud (VPC) securely and communicate with other resources within the AWS environment.

Think of an ENI as an adapter that connects your computer to the internet. But instead of connecting to the public internet, ENIs connect your EC2 instances to your private VPC. This provides greater control over network security and traffic.

Here are some of the key features of an ENI:

* **Private and public IP addresses:** Each ENI has a unique private IP address within the VPC. You can also associate an Elastic IP with it to provide a static public IP address to your instance.
* **Security:** You can assign security groups to ENIs to control their inbound and outbound traffic. This allows you to define what types of network traffic are allowed to the instance.
* **Flexibility:** ENIs can be attached and detached from EC2 instances as needed. This makes it easy to scale your instances and migrate workloads between different instances.
* **Independent lifetime:** Unlike attached EBS volumes, ENIs have an independent lifetime. This means that you can continue to use an ENI even after you terminate the EC2 instance that it was previously attached to.

In summary, ENIs provide a scalable and secure way to connect EC2 instances to your VPC in AWS. They offer flexibility, security, and network traffic control, making them an essential component for network configuration in AWS architectures.

Here are some additional points to note:

* ENIs can have one primary private IPv4 address, and zero or more secondary private IPv4 addresses.
* ENIs can have one Elastic IP address per private IP address.
* ENIs can have one public IPv4 address.
* ENIs can have one or more IPv6 addresses.
* ENIs can be associated with one or more security groups.
* ENIs have a MAC address.
* ENIs have a source/destination check flag.
* ENIs can have a delete on termination flag.

**ENI use cases:**

1. Use network and security appliances in your VPC.
2. Create a low budget, high-availability solution.
3. **Create a management network**

What is Enhanced Networking?
![[image.82.png]]
Depending on your instance type, enhanced networking can be enabled using:
![[image.83.png]]
What is an EFA? (Elastic Fabric Adapter)
![[image.84.png]]
EFA can use OS-Bypass

Exam tips:
![[image.85.png]]![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.20.png]]

### Use cases (in italiano)

Ecco alcuni esempi concreti di come gli ENI possono essere utilizzati in un ambiente AWS:

**Scenario 1: Scalabilità rapida di un'applicazione web durante i periodi di picco di traffico**

Immagina di gestire un sito web di e-commerce che subisce un picco di traffico durante i periodi di vacanza. Per gestire questo aumento improvviso della domanda, è necessario scalare rapidamente le tue istanze EC2 per soddisfare la richiesta.

In questo scenario, gli ENI possono essere utilizzati per collegare rapidamente nuove istanze EC2 alla tua VPC. Ciò consente di aggiungere rapidamente capacità di calcolo senza dover configurare manualmente le impostazioni di rete per ogni nuova istanza. Una volta terminato il periodo di picco, puoi semplicemente scollegare le istanze EC2 non necessarie per liberare risorse.

**Scenario 2: Migrazione di un database da un ambiente di sviluppo a uno di produzione**

Supponiamo di aver sviluppato un nuovo database in un ambiente di sviluppo AWS e di volerlo migrare nell'ambiente di produzione. Gli ENI possono semplificare questo processo consentendo di migrare il database senza dover modificare le impostazioni di rete dell'istanza.

Per eseguire la migrazione, puoi semplicemente scollegare l'ENI dal database nell'ambiente di sviluppo e collegarlo al database nell'ambiente di produzione. Ciò garantisce che il database mantenga lo stesso indirizzo IP privato e che le applicazioni che vi fanno riferimento non debbano essere aggiornate con nuovi indirizzi IP.

**Scenario 3: Creazione di una rete ad alte prestazioni per un'applicazione di calcolo scientifico**

Se stai eseguendo un'applicazione di calcolo scientifico che richiede una bassa latenza e un throughput elevato, puoi utilizzare gli ENI per creare una rete ad alte prestazioni. Ciò può essere realizzato utilizzando funzionalità come il supporto per SRIOV e la tecnologia Intel AWS Nitro.

Queste funzionalità consentono di ridurre la latenza e migliorare il throughput della rete, rendendo gli ENI una scelta ideale per applicazioni ad alte prestazioni che richiedono una comunicazione efficiente tra le istanze EC2.

**Scenario 4: Implementazione di una soluzione di disaster recovery per un'applicazione critica**

Per garantire la disponibilità aziendale, è fondamentale disporre di un piano di disaster recovery per le applicazioni critiche. Gli ENI possono essere utilizzati per facilitare la failover in un sito di backup in caso di un'interruzione del sito primario.

In questo scenario, puoi configurare gli ENI in entrambi i siti primario e di backup con gli stessi indirizzi IP privati. Ciò consente alle applicazioni di continuare a funzionare senza interruzioni anche se si verifica un'interruzione nel sito primario.

### EC2 Hibernate

**If we stop an instance the data on disk (EBS) is kept intact until the next start. If we terminate it any EBS volumes (root) also set-up to be destroyed is lost.**
Otherwise, when we start an instance, the following happens:

* First start: OS boots & the EC2 User Data script is run
* Following starts: the OS boots up

Then application start, caches get warmed up, and can take time!
Thanks to Hibernate the in-memory (RAM) state is preserved. So our instance boot will be so much faster. Everything is RAM will be stored in an encrypted file in the root EBS volume.
![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.21.png]]
**Use cases:**
		• Long-running processing
		• Saving the RAM state
		• Services that take time to initialize
		

Good to know - Hibernate
• Supported Instance Families – C3, C4, C5, I3, M3, M4, R3, R4, T2, T3, …
• Instance RAM Size – must be less than 150 GB.
• Instance Size – not supported for bare metal instances.
• AMI – Amazon Linux 2, Linux AMI, Ubuntu, RHEL, CentOS & Windows…
• Root Volume – must be EBS, encrypted, not instance store, and large
• Available for On-Demand, Reserved and Spot Instances
• An instance can NOT be hibernated more than 60 days

### AWS Outposts

Outposts brings the AWS data center directly to you, on-premises. Outposts allow you to have the large variety of AWS services in your data center
![[image.87.png]]
Family members:
![[image.88.png]]

## 

### Ec2 Instance Storage

An EBS (Elastic Block Store) Volume is a network drive you can attach to your instances while they run.

* It allows your instances to persist data, even after their termination
* **Can be mounted to one instance at a time**
* They are bound to a **specific availability zone**
* It’s a network drive (i.e. not a physical drive)
* It uses the network to communicate the instance, which means there might be a bit of latency
* It can be detached from an EC2 instance and attached to another one quickly
* **An EBS Volume in us-east-1a cannot be attached to us-east-1b**
* To move a volume across, you first need to **snapshot it**
* Have a provisioned capacity (size in GBs, and IOPS)
* You get billed for all the provisioned capacity
* You can increase the capacity of the drive over time

We can also choose to create an EBS volume and leave it unattached.
![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.22.png]]

### EBS Instance Store

EBS volumes are **network drives** with good but "limited" performance. If you need a high-performance hardware disk, use **EC2 Instance Store.**
• Better I/O performance
• EC2 Instance Store lose their storage if they’re stopped (ephemeral)
• Good for buffer / cache / scratch data / temporary content
• Risk of data loss if hardware fails
• Backups and Replication are your responsibility

# Elastic Block Storage

EBS is a storage volume you can attach to your ec2 instances. We can use EBS the same way you would use any system desk:

1. Create a file system.
2. Run a database
3. Run an operating system
4. Store data
5. Install applications.

EBS is designed for mission critical workloads and is highly available and scalable (dynamically increase capacity and change the volume type with no downtime or performance impact to your live systems.

EBS Volumes come in different types
		• gp2 (SSD): General purpose SSD volume that balances price and performance for
		a wide variety of workloads. Good for boot volumes or development and test applications that are not latency sensitive.

* gp3 (SSD): Ideal for applications that require high performance at a low cost such as MySQL, Cassandra, virtual desktops, and Handoop analytics.

		• io1 / io2 Block Express (SSD): Highest-performance SSD volume for mission-critical
		low-latency or high-throughput workloads
		• Throughput Optimized HDD (st1): Low cost HDD volume designed for frequently accessed
		workloads
		• sc1 (Cold HDD): Lowest cost HDD volume designed for less frequently accessed workloads
		EBS volume are characterized in Size, Throughput, IOPS (I/O Ops Per Sec)
		Only **gp2/gp3** and **io I/io2 Block Express can be used as boot volumes**
		

### General Purpose SSD

* Cost effective, low-latency
* System boot volumes, virtual desktop, Development and test environments
* 1 GiB - 16 TiB
* **gp3:**
	* Baseline of 3.000 IOPS and throughput of 125 MiB/s
	* Can increase IOPS up to 16.000 and throughput up to 1000 MiB/s indipendently
	* max performance of gp3 is 4 times faster than max performance than gp2
* **gp2:**
	* Small gp2 volumes can burst IOPS up to 3.000
	* Size of the volume and IOPS are linked, max IOPS is 16.000
	* 3 IOPS per GB, means at 5,334 GB we are at the max IOPS

### Provisioned IOPS (PIOPS) SSD

• Critical business applications with sustained IOPS performance
• Or applications that need more than 16,000 IOPS
• **Great for databases workloads** (sensitive to storage perf and consistency)
• io1 (4 GiB - 16 TiB):
		• Max PIOPS: 64,000 for Nitro EC2 instances & 32,000 for other
		• Can increase PIOPS independently from storage size
• io2 Block Express (4 GiB – 64 TiB):
![[image.89.png]]

### 

### Throughput Optimized HDD (st1)

**Cannot be a boot volume.** 125 GiB to 16 TiB
• Throughput Optimized HDD (st1)
![[image.91.png]]

### Cold HDD (sc1)

![[image.92.png]]

### IOPS vs Throughput

![[image.93.png]]

### 

### EBS Volumes & Snapshots

Volumes are simply virtual hard disks. You need a minimum of 1 volume per Ec2 instance. **This is called the root device volume.**

EBS volumes will always be in the same AZ as Ec2 which is attached to. It's possible also to resize and switch volume types. You don't need to stop or restart the instance.
Snapshots exist on S3 not on EBS.
![[image.94.png]]
Tips for Snapshots:

1. Snapshots only capture data that has been written to your Amazon EBS volume, which might exclude any data that has been locally cached by your application or OS. For a consistent snapshot, it is recommended you stop the instance and take the snap
2. If you take a snapshot of an encrypted EBS volume, the snapshot will be encypted automatically.
3. You can share snapshots, but only in the region in which they were created. To share to other regions, you will need to copy them to the destination region first.

![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.23.png]]

### EBS Multi-attach - io I/io2 family

With EBS Multi-Attach we can attach the same EBS volume to multiple EC2 instances in the **same AZ**. Each instance has full read & write permissions to the high-performance volume
Use case:
		• Achieve higher application availability in clustered Linux applications (ex: Teradata)
		• Applications must manage concurrent write operations
		• Up to 16 EC2 Instances at a time
		• Must use a file system that’s cluster-aware (not XFS, EXT4, etc…)
		

### EBS Encryption

When you create an encrypted EBS volume, you get the following:

* Data at rest is encrypted inside the volume
* All the data in flight moving between the instance and the volume is encrypted
* All snapshots are encrypted

Encryption is something that we should use cause a low impact on latency, is transparently (you don't have nothing to do). EBS Encryption leverages keys from KMS (AES-256). Copying a snapshot unencrypted allows encryption. Snapshots coming from an encrypted volume are encrypted by default.
Amazon EBS encryption uses AWS Key Management Service (AWS KMS) customer master keys (CMK) when creating encrypted volumes and snapshots.
![[image.95.png]]

![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.24.png]]

# Elastic file system - EFS

![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.25.png]]
EFS is a managed NSF (Network File System) that can be mounted on many EC2 instances. EC2 instances attached to EFS can be stored in multi-AZ
Use cases:

* Content management
* Web serving
* Data sharing
* WordPress

EFS use **NFSv4** protocol. To control access to EFS we can use Security Group. EFS is only compatible with **Linux based AMI (not Windows).** Encryption at rest using KMS. File system scales automatically, pay-per-use, no capacity planning.
![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.26.png]]![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.27.png]]

# FSx for Windows

Amazon FSx for Windows File Server provides a fully managed native Microsoft Windows file system so you can easily move your Windows-based applications that require file storage to AWS.
![[image.96.png]]

### Exam tips (FSx, FSx for Windows, FSx for Lustre)

![[image.97.png]]

## Amazon Machine Image: EBS vs Instance store

An Amazon Machine Image (AMI) provided the information required to launch an instance
![[image.98.png]]![[image.99.png]]

### AWS Backup

Backup allows you to consolidate your backups across multiple AWS services, such as EC2, EBS, EFS, Amazon FSx for Lustre. It can include also other services, such as DB technologies like RDS and DynamoDB.

AWS Backup is really good to manage also multiple AWS Accounts within your Organizations.
Several benefits like:

1. Central management: use a single, central backup console, allowing you to centralize your backups across multiple AWS services and multiple AWS accounts.
2. Automation: you can create automated backup schedules and retention policy. You can also create lifecycle policies, allowing you to expire unnecessary backups after a period of time.
3. Improved Compliance: backup policies can be enforced while backups can be encrypted both at rest and in transit.
4. 

# High Availability & Scalability

### Scalability

There are two types of scalability:

* Vertical: let's say we have our application running on **t2.micro.** Scaling this application vertically means to upgrade to **t2.large.** Is common for non distributed systems, like database. Usually there's a limit to how much you can scale.
* Horizontal: means increasing the number of instances of your application. Horizontal scalability is related to distributed systems. Very common for web applications.

### Availability

High availability usually goes hand in hand with horizontal scaling. It means running your application/system in at least 2 data centers( == AZs). The main goal is to survive to a data center loss.

# Elastic Load Balancer (ELB)

ELB automatically distributes incoming application traffic across multiple targets, such as Amazon EC2 instances. This can be done across multiple AZs.
![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.28.png]]

## Why use a load balancer?

* Spread load across multiple downstream instances.
* Expose a single endpoint (DNS) to access to your application
* Seamlessly handle failures of downstream instances
* Provide SSL termination (HTTPS) for your websites
* Enforce stickiness with cookies
* High availability across zones
* Separate public traffic from private traffic

## Why use an Elastic Load Balancer?

• **An Elastic Load Balancer is a managed load balancer**
		• AWS guarantees that it will be working
		• AWS takes care of upgrades, maintenance, high availability
		• AWS provides only a few configuration knobs
• It costs less to setup your own load balancer but it will be a lot more effort on your end.
• It is integrated with many AWS offerings / services

* ECS, EC2 Auto Scaling Groups, Amazon ECS
* AWS Certificate Manager (ACM), CloudWatch
* Route 53, AWS WAF, AWS Global Accelerator

All AWS load balancers can be configured with health checks periodically send requests to load balancers' registered instances to test their status.
The status of any instances that are unhealthy at the time of the health check is **OutOfService**. The load balancer performs health checks on all registered instances, whether the instance is in a healthy state or unhealthy state.
The load balancer routes requests to only to the healthy instances
![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.29.png]]![[image.147.png]]

## Layer 7 Load Balancing

An Application Load Balancer functions at the Application Layer (seventh layer of the OSI model). After a load balancer receives a request, it evaluates the listener rules in priority order to determine which rule to apply.
A listener checks for connection requests from clients, using the protocol and port you configure.
Rules allows us to enable some actions when conditions are met. You must define a default rule for each listener, and you can **optionally define additional rules.**
Then we have **target groups,** which routes requests to one or more registered targets, such as Ec2 instances.
![[image.148.png]]

## Load Balancer Security Groups

![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.30.png]]
Use case:
A user can access from anywhere to load balancer. Ec2 Instance can accept only traffic coming from load balancer. So in **Source** of EC2 Instance instead to have a IP range will have the security group of load balancer.

### Application Load Balancer (ALB)

• Application load balancers is Layer 7 (HTTP)
• Load balancing to multiple HTTP applications across machines (target groups)
• Load balancing to multiple applications on the same machine (ex: containers)
• Support for HTTP/2 and WebSocket
• Support redirects (from HTTP to HTTPS for example)

With ALB we can route based on different target groups:

* Routing based on path in URL (example.com/users & example.com/posts)
* Routing based on hostname in URL (one.example.com & other.example.com)
* Routing based on query, String, Headers (example.com/users?id=123&order=false)

ALB is a great fit for microservices, container-based applications.

### Application Load Balancer - Target groups

A target group can be attach to multiple things:

* EC2 Instance (can be managed by an Auto Scaling Group) - HTTP
* ECS tasks (managed by ECS itself) - HTTP
* Lamba functions - HTTP request is translated into a JSON event
* IP Addresses - Must be private IPs.
* ALB can route to multiple target groups
* Health checks are at the target group level

![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.31.png]]

### Network Load Balancer (NLB v2)

Network load balancer (Layer 4) allow to:

* **Forward TCP & UDP traffic to your instances**
* Handle million of request per second
* Less latency 100ms (vs 400 ALB)

NLB has one static IP for AZ, and supports assigning Elastic IP. It's used for extreme performance, **TCP or UDP Traffic.**

* **Not included in AWS Free tier.**

![[Evernote/My Notes/_resources/AWS_Solutions_Architect_-_Associate.resources/image.32.png]]

### Gateway Load Balancer (Newest)

![[image.33.png]]![[image.34.png]]

## Sticky Sessions

It's possible to implement sticky sessions, when we want to redirect the same client to the same instance behind load balancer. It works for **Classic Load Balancer (CLB), Application Load Balancer (ALB), Network Load Balancer (NLB, works without cookies).** For the first two, the "cookie" used for stickiness has an expiration date you control.
![[image.35.png]]
To enable encryption "in-flight" we can attach SSL (Secure Socket Layer)/TLS (Transport Layer Security) certificate to our load balancer. SSL Certificate has an expiration date (you set) and must be renewed.
![[image.36.png]]

![[image.37.png]]
Elastic Load Balancers – SSL Certificates
• **Classic Load Balancer (v1)**
		• Support only one SSL certificate
		• Must use multiple CLB for multiple hostname with multiple SSL certificates
• **Application Load Balancer (v2)**
		• Supports multiple listeners with multiple SSL certificates
		• Uses Server Name Indication (SNI) to make it work
• **Network Load Balancer (v2)**
		• Supports multiple listeners with multiple SSL certificates
		• Uses Server Name Indication (SNI) to make it work
		

## Deregistration Delay

Allows Load Balancers to keep existing connections open if the Ec2 instances are de-registered or become unhealthy.
We can disable deregistration delay if you want to immediately close connections to the instances that are de-registering or have become unhealthy.
![[image.38.png]]

## Auto scales group

In the cloud, we can create or get rid of servers very quickly. The goal of Auto Scaling Group is to:

* Scale out (add instances) to match an increased load
* Scale in (remove instances) to match a decreased load.
* Ensure we have a minimum and maximum number of EC2 instances running

![[image.39.png]]![[image.40.png]]
It's possible to scale an ASG based on CloudWatch alarms. An alarm monitors a metric (CPU Usage, custom metric). Based on the alarm we can scale out (add instances) or scale in (remove instances).

## Scaling Policies

There are two different types of scaling:

* **Dynamic Scaling**
	* **Target Tracking Scaling**
		* Simple set up
		* **Example**: I want the avg CPU to stay around 40%
	* **Simple / Step Scaling**
		* When a CloudWatch alarm is triggered (example CPU > 70%), then add 2 units
		* When a CloudWatch alarm is triggered (example CPU < 30%), then remove 1 unit
* **Scheduled Scaling**
	* Anticipate a scaling based on known usage patterns
	* **Example**: increase the min capacity to 10 at 5 pm on Fridays

![[image.41.png]]![[image.42.png]]

# Relation Database Service (RDS)

This service is a managed DB and use SQL as query language. It allows you to create databases in the cloud that are managed by AWS:
		• Postgres
		• MySQL
		• MariaDB
		• Oracle
		• Microsoft SQL Server
		• Aurora (AWS Proprietary database)
RDS is generally used for **online transaction processing (OLTP)** workloads.
![[image.110.png]]
RDS is not suitable for analyzing large amounts of data. Use a data warehouse like Redshift, which is optimize for OLAP.
Since RDS is a managed service has many advantages instead of deploying a DB on EC2 instances. Like below:
		• Automated provisioning, OS patching
		• Continuous backups and restore to specific timestamp (Point in Time Restore)!
		• Monitoring dashboards
		• Read replicas for improved read performance
		• Multi AZ setup for DR (Disaster Recovery)
		• Maintenance windows for upgrades
		• Scaling capability (vertical and horizontal)
		• Storage backed by EBS (gp2 or io1)
We can't access from SSH to our RDS instances. Cause this is a managed services it totally managed by AWS, so we don't need to worry about what is under the hood.

### RDS  - Storage Auto Scaling

Key feature for RDS is auto-scaling. Helps to increase storage on your RDS DB instance dynamically. When RDS detect you are running out of free DB storage, it scales automatically.
![[image.43.png]]

## 

### RDS Read Replicas

We can use Read Replicas to improve performance with RDS. A Read Replicas is a read-only copy of your primary DB.
![[image.44.png]]

### Use Cases

![[image.45.png]]

### Network Cost

![[image.46.png]]

### RDS Multi-AZ (Disaster Recovery)

To increase **availability** we can create, from master DB, another DB with sync replication in another AZ. So if AZ failed, loss of network or storage failure, automatically, will be a failover switching RDS Instance without manual intervention. Not used for scaling.
AWS handles the replication for you. When you write to your production DB, this write will be automatically synchronize to the standby DB.
Note: The read replicas need to be setup as Multi-AZ for Disaster Recovery (DR)
![[image.47.png]]![[image.48.png]]![[image.49.png]]

### Operating Mongo-DB-Compatible DB in Amazon DocumentDB

MongoDB is a document DB that allows for scalability and flexibility with your data as well as robust querying and indexing features.
Amazon DocumentDB allows you to run MongoDB on the AWS Cloud. It's managed DB service that scales with your workloads and safely and durably store your database information.

### 

## Amazon Aurora

Aurora is a proprietary technology of AWS (not open source)
Postgres and MySQL are both supported as Aurora DB. Aurora is a "AWS Cloud optimized" and claims 5x performance improvement over MySQL on RDS, over 3x performance of Postgres on RDS.
Aurora storage automatically grows in increments of 10GB, up to 128TB. Aurora can have up to 15 read replicas and the replication process is faster than MySQL. Since Aurora is HA (High Availability) native, failover in Aurora is instantaneous. Aurora costs more than RDS (20% more) but is more efficient.

Aurora storage is **self-healing.** Data blocks and disks a re continuously scanned for errors and repaired automatically. Aurora has automated backups turned on by default. You can also take snapshots with Aurora
![[image.50.png]]![[image.51.png]]

## 

### Features of Aurora

		• Automatic fail-over
		• Backup and Recovery
		• Isolation and security
		• Industry compliance
		• Push-button scaling
		• Automated Patching with Zero Downtime
		• Advanced Monitoring
		• Routine Maintenance
		• Backtrack: restore data at any point of time without using backups
		

### Amazon Aurora Advanced

		

![[image.52.png]]![[image.53.png]]![[image.54.png]]![[image.55.png]]![[image.56.png]]

## DynamoDB

Amazon DynamoDB is a fast and flexible NoSQL database for all applications that nee consistent, single-digit millisecond latency at any scale. It is fully managed database and supports both document and key-value data models.
Your data in DynamoDB are stored in SSD storage and spread across 3 geographically distinct data centers.
![[image.111.png]]

### DynamoDB Accelerator (DAX)

DAX is a fully managed, highly available, in-memory cache service for DynamoDB. it actually gives you up to 10 times the performance improvement than just using DynamoDB on its own.
And it reduces request times from milliseconds to microseconds even under load.

### DynamoDB Transactions

![[image.112.png]]
DynamoDB Transactions provide developers, atomicity, consistency, isolation and durability across 1 or more tables within a single account AWS and region. ACID basically means ALL or NOTHING.
![[image.113.png]]

### DynamoDB Streams and Global Tables

![[image.114.png]]
Global Tables allow you to manage multi-master, multi-region replication of you DynamoDB tables.
And this is great for globally distributed applications. So if you've got an application that's spread all across the world and you want to have consistent DynamoDB tables in each region,
then you can have global tables.

## RDS Backups

RDS automatically daily full backup the database (during the backup window). Transaction logs are backed up by RDS every 5 minutes. So the earliest DB version is max 5 minutes old.
• => ability to restore to any point in time (from oldest backup to 5 minutes ago)
• 1 to 35 days of retention, set 0 to disable automated backups

### Manual Backups

• Manually triggered by the user
• Retention of backup for as long as you want

**Trick**: in a stopped RDS database, you will still pay for storage. If you plan on
stopping it for a long time, you should snapshot & restore instead

![[image.57.png]]![[image.58.png]]

### Aurora Database Cloning

Create a new Aurora DB Cluster from an existing one.  It's faster than get a snapshot and restore it and also is cost-effective.
• Uses copy-on-write protocol
		•     Initially, the new DB cluster uses the same data volume as the original DB cluster (fast and efficient – no                  copying is needed)
		•     When updates are made to the new DB cluster data, then additional storage is allocated and data is                           copied to be separated
Useful to create a **"staging"** DB from the production one, without affecting the production db.

### RDS & Aurora Security

1. RDS and Aurora can encrypt **at-rest. This means the encryption is in the volume.**
	* DB master and replicas encryption using KMS (Key Management System) - must be defined at lunch time
	* If the master is not encrypted, the read replicas cannot be encrypted
	* To encrypt an unencrypted DB, we can get a snapshot and restore it as encrypted.
2. Can also encrypt **In-flight. Means between the client and DB.** Every DB is TLS-ready by default. Use the AWS TLS root certificates client-side.
3. **IAM Authentication:** we can use IAM roles to connect to your DB.
4. **Security groups:** Control network access to your RDS/Aurora DB.
5. No SSH available except on RDS custom

We can enable and send to CloudWatch Logs for longer retention

### Amazon RDS Proxy

![[image.59.png]]

# Caching

![[image.165.png]]

## CloudFront

CloudFront is a fast content delivery network (CDN) service that securely delivers data, video, applications and APIs to customer globally. It helps reduce latency and provide higher transfer speeds using AWS edge location.
![[image.166.png]]

## ElastiCache

The same way RDS is to get managed Relation Databases, ElastiCache is to get managed Redis or Memcached. Neither of these tools are specific to AWS, but by using ElastiCache you avoid a lot of common issues you might encounter. Caches are **in-memory databases** with really high performance and low latency.
Help a lot reduce load off of databases for read intensive workload and helps make your application stateless.
As for RDS, AWS take care of OS maintenance / patching, optimizations, setup, configuration, monitoring  failure recovery and backups.
**Using ElastiCache involves heavy application code changes.**

![[image.167.png]]

## DynamoDB Accelerator (DAX)

DynamoDB Accelerator is a fully managed, highly available caching service built for Amazon DynamoDB. DAX delivers up to 10 times performance improvement even at millions of requests per second.
![[image.168.png]]

## Global Accelerator

Global Accelerator is a networking service that sends your users traffic through AWS's global network infrastructure via accelerators. Global Accelerator is meant for TCP or UDP traffic. So is well suited for applications that require low latency and high availability.
![[image.169.png]]

### Solution Architecture

![[image.60.png]]![[image.61.png]]

### ElastiCache Security

• **ElastiCache supports IAM Authentication for Redis**
		•  IAM policies on ElastiCache are only used for AWS API-level security
• **Redis AUTH**
		• You can set a “password/token” when you create a Redis cluster
		• This is an extra level of security for your cache (on top of security groups)
		• Support SSL in flight encryption
• **Memcached**
		• Supports SASL-based authentication (advanced)
![[image.62.png]]![[image.63.png]]

# Route 53

Route53 is Amazon's DNS service. It allows you to register domain names, create hosted zones, and manage and create DNS records.
Domain Name System is responsible to translate the human friendly hostnames into the machine IP address.
IP addresses are used by computers to identify each other on the network.
Since all domain names must be unique, there needs to be a way to organize this all so that domain names aren't duplicated. This is where **domain registrars** come in.
A registrar is an authority that can assign domain names directly under one or more top-level domains. These domains are registered with InterNIC, a service of ICANN, which enforces uniqueness of domain names across the internet.

![[image.64.png]]![[image.65.png]]
Route 53 is high available, scalable, fully managed and Authoritative DNS. It's **authoritative** cause the customer can update can update the DNS records. Route 53 is also a Domain Registrar and can check the health of your resources.
Route 53 is the only AWS service with a 100% SLA.
![[image.66.png]]

### Common DNS Record Types

1. **SOA Records: "**Start of Authority" record stores important information about a domain.
2. **CNAME Records:** forwards one domain or subdomain to another domain.
3. **NS Records:** stores the name server for a DNS entry.
4. **A record:** the record that holds the IP address of a domain.

### Hosted Zones

Hosted zones are container that define how to route traffic to a domain or its subdomains.
There are two different Hosted Zones:

### Public Hosted Zones

contains records that specify how to route traffic on the Internet (public domain names)
**application1.mypublicdomain.com**

### Private Hosted Zones

contain records that specify how you route traffic within one or more VPCs (private domain names)
**[application1.company.internal](http://application1.company.internal)**
**User pay 0.50$ / month per hosted zone**
![[Screenshot from 2024-06-07 10-43-55.png]]

### CNAME vs Alias

CNAME points hostname to any other hostname. **Works only for NOT ROOT DOMAIN.**
Alias points hostname to AWS Resource. **It works for ROOT DOMAIN and NOT ROOT DOMAIN.** In addition Alias is free of charge and is natively health check.
![[Screenshot from 2024-06-07 10-50-24.png]]
Alias Record Target:

* Elastic Load Balancer
* CloudFront Distributions
* API Gateway
* Elastic Beanstalk env
* S3 Websites
* VPC Interface Endpoints
* Global Accelerator
* Route 53 record in the same hosted zone

### 

## Routing Policies

Routing policies define how Route53 responds to DNS queries. Don't be confused by the word **routing.** It's not like Load Balancer.
There different types of Routing Policies:
		• Simple
		• Weighted
		• Failover
		• Latency based
		• Geolocation
		• Multi-Value Answer
		• Geoproximity (using Route 53 Traffic Flow feature)
		

### Simple

If you choose the simple routing policy, you can only have **one record with multiple IP addresses.**
If you specify multiple values in a record, Route53 returns all values to the use in a random order. 
Simple routing policies can't be associated with Health Checks.

### Weighted

Control the % of the requests that go to each specific resource.
Assign to each record a relative weight.
**Traffic ( % ) is = to Weight for a specific resource / sum of all the weights for all records**
**Weight don't need to sum to 100**
**DNS** record must have the same name and type. Weighted routing policies can be associated with Health Checks.
**Use cases:**

* Load balancing between regions
* Testing new application versions

To stop sending request to a resource just set weight to 0. 

### Latency

Redirect to the resource that has the least latency close to us. It's really useful when latency is a priority for user. It also can be associated to health check

### Health Checks

Are a way to check the health on many PUBLIC resources.
![[image.67.png]]

It's possible to combine different Health Checks using OR, AND or NOT creating a parent. It's possible to group together 256 child health checks
Health checks are just to check PUBLIC resources so it would be difficult to check for something in a VPC. To do so, we can create a **Cloud Watch Metric** and associate to it a **Cloud Watch Alarm** then create an Health check that checks the alarm it self. Remember, the health check will be always outside something is private.

### Failover (Active-Passive)

Failover routing policies are used when you want to create an active/passive set up.
![[image.68.png]]

### Geolocation

It's different from Latency routing policies. This policy is based on user location. We can specify location by Continent, Country or by State. In case there's no match on the specified location, best practice to have a default value. It can also be associated it health checks.

### Geoproximity

You can use Route53 traffic flow to build a routing system that uses a combination of:

1. Geographic location
2. latency
3. and availability to route traffic

from your users to your cloud or on-premises endpoint.
![[image.69.png]]

### Ip-based Routing

Routing is based on client's IP Addresses. We can provide a list of CIDR's for our clients and the corresponding endpoints/locations

### Multi-value

Useful when routing traffic to multiple resources. Route 53 return multiple values/resources

## 

# Amazon S3

Amazon S3 is one of the main building blocks of AWS. It has a lot of use cases:
![[Screenshot from 2024-06-11 09-03-46.png]]
Amazon S3 stores files in bucket (directories) and what is in the bucket (need to have a unique name across all AWS regions and accounts) is an object.
Buckets are define at region level.
Objects stored in S3 bucket have a key. Key is the FULL path of the object.
The key is is composed of **prefix + object name.**
Object values are content of the body. We can store object with **max size** of 5000GB (5TB). If we are going to upload something is **greater** than 5GB (but recommended for file over 100mb) we need to use **multi-part upload** which increases efficiency. It's also possible to parallelize downloads by specifying byte ranges. So if there's a failure in the download, it's only for a specific byte range.

Files in your s3 bucket are spread across multiple devices an facilities to ensure **availability** and **durability**.
![[image.100.png]]

### Object ACLs vs Bucket Policies

Access control list work on an individual object level. Instead, bucket policies must be applied at bucket level, in this way we can make fully public or fully private our bucket.

When we create an s3 bucket, **it is private by default** (including all objects within it). You have to allow public access on both the bucket and its object in order to make a bucket public.

### Amazon S3 Security

We have multiple kind of security settings for S3 bucket.

**User based:**

* IAM Policies: which API call should be allowed for a specific user from IAM

**Resource-Based:**

* **Bucket Policies:** bucket wide rules from the S3 console - allow cross account
* **Object Access Control List (ACL) -** finer grain (can be disabled)
* **Bucket Access Control List (ACL) -** less common (can be disabled)

### Bucket Policies

![[Screenshot from 2024-06-11 09-34-17.png]]
S3 can host also static websites and have them accessible on the internet

### Versioning

You can enable versioning in s3 so you can have **multiple versions of an object on s3.**
![[image.101.png]]
Versioning it's enabled at a **bucket level.** It's best practice to version your bucket so you can protect against unintended deletes (ability to restore a version) and easily roll back to previous version.
Since we enable versioning on s3 bucket, when we delete a file is not actually deleted but just disappear from our UI.

### S3 Replication (CRR & SRR)

![[image.109.png]]
• Use cases:
		• CRR – compliance, lower latency access, replication across
		accounts
		• SRR – log aggregation, live replication between production and test
		accounts
![[Screenshot from 2024-06-11 10-00-47.png]]

### S3 Durability and Availability

• **Durability**:
		• High durability (99.999999999%, 11 9’s) of objects across multiple AZ
		• If you store 10,000,000 objects with Amazon S3, you can on average expect to
		incur a loss of a single object once every 10,000 years
		• Same for all storage classes
• **Availability**:
		• Measures how readily available a service is
		• Varies depending on storage class
		• Example: S3 standard has 99.99% availability = not available 53 minutes a year
		

### Storage Classes

![[Screenshot from 2024-06-11 10-15-47.png]]![[Screenshot from 2024-06-11 10-16-01.png]]![[image.102.png]]

![[image.70.png]]![[image.103.png]]

### Exam tips - Storage classes

![[image.104.png]]

### Lifecycle management

Lifecycle management automates moving your objects between the different storage tiers, thereby maximizing cost effectiveness. Lifecycle can be used to move different versions of objects to different storage tiers.
We can set lifecycle rules to configure object to transition to another storage class. Like after 60 days since the creation of the object, is moved to another storage class. (**transition actions**)
We can also set **expiration actions,** in this way we can configure objects to expire after some time
• Rules can be created for a certain prefix (example: s3://mybucket/mp3/\*)
• Rules can be created for certain objects Tags (example: Department: Finance)

![[Screenshot from 2024-06-13 07-47-05.png]]![[Screenshot from 2024-06-13 07-53-13.png]]
We can define some events that are triggered when something happen in our buckets. This event notification can be sent to SQS, SNS or Lamba function.
• S3 event notifications typically deliver events in seconds but can sometimes take a minute or longer

The bucket to be able to send notifications to our service (SQS, SNS) we need to attach Resource (Access) policy (IAM permissions, JSON file).
![[Screenshot from 2024-06-13 08-02-20.png]]![[Screenshot from 2024-06-13 08-12-07.png]]![[Screenshot from 2024-06-13 08-14-01.png]]

### S3 Object Lock

You can use S3 object lock to store objects using a **write once, read many (WORM) model.** It can help prevent objects from being deleted or modified for a fixed amount of time or indefinitely.
There's two types of Object Lock mode:
![[image.105.png]]![[image.106.png]]
A retention period **protects an object version for a fixed amount of time.** When you place a retention period on an object version, Amazon S3 stores a timestamp in the object version's metadata to indicate when the retention period expires. After the retention period is expired, the object version can be **overwritten or deleted** unless you also placed a **legal hold** on the object version.
A legal hold **prevents an object version from being overwritten or deleted,** like retention period. The difference is that legal hold doesn't have an associated retention period and remains in effect until removed.

### Glacier Vault Lock

Allows you to easily deploy and enforce compliance controls for individual S3 Glacier Vaults with a vault lock policy.
Essentially, Glacier Vault Lock is a way of applying a WORM model to Glacier.

### Select & Glacier Select

We can filter using SQL by performing server-side filtering. Can filter by rows & columns. With this we can achieve less network transfer, less cpu cost client-side.

### S3 Batch Operations

• Perform bulk operations on existing S3 objects with a single request, example:
		• Modify object metadata & properties
		• Copy objects between S3 buckets
		• Encrypt un-encrypted objects
		• Modify ACLs, tags
		• Restore objects from S3 Glacier
		• Invoke Lambda function to perform custom action on
		each object
• A job consists of a list of objects, the action to perform, and optional parameters
• S3 Batch Operations manages retries, tracks progress, sends completion notifications, generate           reports …
• You can use S3 Inventory to get object list and use S3 Select to filter your objects

### Storage Lens

We can understand, analyze and optimize storage across entire AWS Organization. We can take all data from Organization, specific account, regions, buckets or prefixes aggregate them together in a report and optimize several aspect of our configuration.
Storage Lens provide a default dashboard 

## Amazon S3 - Encrypting Objects

We can encrypt objects in four methods:

* **Server side encryption (SSE)**
	* **Server-Side Encryption with Amazon S3-Managed Keys.** Enable by default. **(SSE-S3)**
		* Encrypts S3 objects using keys handled, managed, and owned by AWS
	* **Server-Side Encryption with KMS Keys stored in AWS KMS (SSE-KMS)**
		* Leverage AWS Key Management Service (AWS KMS) to manage encryption keys
	* **Server-Side Encryption with Customer-Provided Keys(SSE-C)**
		* When you want to manage your own encryption keys.
* **Client-Side Encryption**

![[image.107.png]]
**Tips:** it's possible to create a bucket policy that denies any S3 PUT request that doesn't include the **x-amz-server-side-encryption** parameter in the request header.

### Optimizing S3 Performance

S3 has extremely low latency. You can get the first byte out of S3 within 100-200 milliseconds.
![[image.108.png]]

If we are using KMS to encrypt our S3 bucket, please notice some limitations.
When you upload a file, you will call **GenerateDataKey** in the KMS API.

# Virtual Private Cloud (VPC) Networking

We can think to a VPC as a virtual data center in the cloud. Every region has a default VPC.
Logically isolate part of AWS Clous where you can define your own network.

Complete control o virtual network, including your own IP address range, subnets, route tables and network gateways.
1 subnet is always in 1 Availability Zone.

Every region has a default VPC. When AWS create the default VPC it create also:

* Create a VPC with a size `/16` IPv4 CIDR block ([172.31.0.0/16](http://172.31.0.0/16)). This provides up to 65,536 private IPv4 addresses.
* Create a size `/20` default subnet in each Availability Zone. This provides up to 4,096 addresses per subnet, a few of which are reserved for our use.
* Create an [internet gateway](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html) and connect it to your default VPC.
* Add a route to the main route table that points all traffic ([0.0.0.0/0](http://0.0.0.0/0)) to the internet gateway.
* Create a default security group and associate it with your default VPC.
* Create a default network access control list (ACL) and associate it with your default VPC.
* Associate the default DHCP options set for your AWS account with your default VPC.

![[image.74.png]]

### Demo: Provisioning VPC

![[image.72.png]]
Below the step to follow:

1. Create a VPC.
2. Choose a name and a CIDR block of IPv4. CIDR for AWS must be between **/16 and /28.**
3. Now, you can create subnets. Obviously subnet's IP range must be lower than the maximum IP available in the CIDR block. By default the subnets created by you have **"Auto-assign public IPv4 address"** set to NO. We can make turn it on YES by editing the subnet's setting (Action > Edit subnet Settings).
4. To make it effectively a public subnet we need an **internet gateway.** Create one.
5. After the creation, internet gateway is not attached to nothing. We need to associate it to a VPC.
6. Now, we need a route out to the internet. When we create a VPC, a route table is created by default an associated to our VPC. We don't want to edit the existing route table but to create a new one.![[Screenshot from 2024-10-23 19-46-10.png]]
7. When it's created and associated with our VPC we need to add a Routes that basically allow us to route out to the internet.
8. Now, we want to associate our **public subnet** to this route just created.![[Screenshot from 2024-10-23 19-48-54.png]]
	Now our **public subnet is no longer** without explicit associations but it's explicitly associated to our route table with internet access.
	
9. Now, we can launch two ec2 instances. One instance will be our Webapp and the other one will be our "DB". Webapp will live in our public subnet with access to internet. DB will live in our private subnet. To able connection between this ec2 instances we need to create a route table for our instance that lives in our private subnet and create an **inbound rule** which allow incoming traffic fromn a custom source which is our **security group** previously created. Our DB instance can't communicate with internet and this can be an issue (update OS, SQL, etc...). we can fix it.
10. We can create a NAT gateway in our public subnet.
11. Now, we have to edit routes of our main route table.

## What we can do with VPC?

![[image.73.png]]
We can choose between two types of VPC: Default and Custom.

## Protecting Your Resources with SG

Computer communicates each other through protocol, which is dedicated to a particular port. When someone is trying to connect to our instances, the request pass before through Route Table than NACL (Network Access Control List) and then through SG (Security Group). So we can consider SG as the last line of defense. So if, for example we have a internet issue connection, the first thing to check should be Route table than NACL and at the end SG.

Security Groups are **virtual firewalls for an EC2 Instance.** By default, everything is blocked. **In order to communicate to your EC2 instances via SSH, HTTP, RDP we have to open up the correct ports.**

**Security groups are stateful.** If you send a request from your instance, the response traffic for that request is allowed to flow regardless of inbound security group rules.
Always remember that our NACLs are our first line of defense.

* **Default Network ACLs:** VPC automatically comes with a default network ACL, and by default it allows all outbound and inbound traffic.
* **Custom Network ACLs:** You can create custom network ACLs. By default, each custom network ACL denies all inbound and outbound traffic until you add rules.
* **Subnet Associations:** Each subnet in your VPC must be associated with a network ACL. If we don't explicitly associate a subnet with a network ACL, the subnet is automatically associated with the default network ACL.
* **Block IP Addresses:** Block IP addresses using network ACLs, not security groups.

## Network ACLs

You can associate a network ACL with multiple subnets; however, a **subnet** can be associated with **only 1 network ACL at a time.**
Network ACLs contain a numbered list of rules that are evaluated in order, starting with the lowest value.
Network ACLs have separate inbound and outbound rules, and each rule can either allow or deny traffic.
Network ACLs are **stateless**; responses that allowed inbound traffic are subject to the rules for outbound traffic (and vice versa).ok spass

## NAT Gateways

We can use NAT gateway to **enable instances in a private subnet** to connect to the internet or other AWS services while preventing the internet from initiating a connection with those instances. bPrivate Communication Using VPC Endpoints
A VPC Endpoints enables you to privately connect your VPC to supported AWS services and VPC endpoint services powered by PrivateLink without requiring an internet gateway, NAT device, VPN connection etc.
![[Screenshot from 2024-11-08 09-06-13.png]]

## VPC Peering

Allow you to connect to one VPC with another via a direct network route using private IP addresses.
![[Screenshot from 2024-11-08 09-13-15.png]]

## Securing your network with VPN ClouHub

VPN Cloudhub is really useful if you have multiple sites, each with its own VPN connection and you can use AWS VPN cloudhub to connect those sites together. So it works on a hub and spoke model. It's low cost and very easy to manage and it operates over the public internet. But all traffic between the customer gateway and the AWS VPN Cloudhub is encrypted.
![[Screenshot from 2024-11-08 09-23-56.png]]

## Connecting on-prem with Direct Connect

**Direct Connect** is a cloud service solution that makes it easy to establish a dedicated network connection from your premises to AWS. It has a lot of advantages like: reduce your network costs, increase bandwidth throughput and provide a more consistent network experience than internete-based connections.
There are two types of Direct Connect connections.

1. Dedicated Connection: a physical Ethernet connection associated with a single customer.
2. Hosted Connection: A physical Ethernet connection that an AWS Direct Connect Partner provisions on behalf of a customer.

![[image.75.png]]

### Simplifying Networks with Transit Gateway

AWS Transit Gateway connects VPCs and on-premises networks through a central hub. This simplifies your network and puts an end to complex peering relationships. It acts like a cloud router - each new connection is only made once.
![[image.76.png]]

## 

# Big Data

The 3 Vs of Big Data refer to three primary characteristics that are often used to describe and differentiate Big Data from traditional data.
![[image.115.png]]

## 

## Amazon Redshift

Redshift is a fully managed, petabyte-scale data warehouse service in the cloud. It's a very large relational database traditionally used in big data applications.
Redshift is incredibly big, it can hold up to 16 PB of data. It's a relational database. You use your standard SQL and business intelligence (BI) tools to interact with it.
Redshift offer up to 10x the performance of other data warehouses offered in the cloud.
Redshift is not meant to be a replacement for standard RDS DB. 
Storage data is column-based instead of row-based.
![[image.117.png]]![[image.118.png]]

### 

## Processing Data with EMR (Elastic MapReduce)

ETL (Extract, Transform and Load) are processes that a critical components of data management and analysis. Systematic extraction of data from various sources systems, then are transformed to match business requirements and then load into warehouses.
To complete this process there's a service called Amazon EMR. It's a managed big data platform that allows you to process vast amounts of data using open-source tools, such as Spark, Hive, Presto etc.
![[image.119.png]]
**Clusters** are groups of Ec2 Instances within Amazon EMR. Each instance is a **node.**
![[image.120.png]]

### EMR Architecture

![[image.121.png]]

## Streaming Data with Kinesis

Kinesis allows you to ingest, process, and analyze real-time streaming data.
![[image.122.png]]
We can use Kinesis Data Analytics paired with Firehose or Data streams to process our information using standard SQL.
![[image.124.png]]

### Kinesis Architecture

![[image.123.png]]

### Kinesis Exam tips

![[image.125.png]]

## Amazon Athena and AWS Glue

Amazon Athena is an interactive query service that makes it easy to analyze data in S3 using SQL. This allows you to directly query data in your s3 bucket without loading it into a database.

Amazon Glue is a **serverless data integration** service that makes it easy to discover, prepare and combine data. It allows you to perform **ETL** workloads without managing underlying servers.

## Visualizing Data with Quicksight

Quicksight is a fully managed, serverless business intelligence (BI) data visualization service.
It allows you to easily create dashboards and share them with specific users and groups.
![[image.126.png]]
Users can be created for accessing Quicksight and Enterprise version allow you to create groups. Users and groups only exist in Quicksight (they are not IAM users and groups).
Dashboards are essential for stored configurations and filtering. Dashboards and analysis results can be shared with users and groups.

### Architecture Example

![[image.127.png]]

## Moving and Transform Data using Data Pipeline

AWS Data Pipeline is a managed ETL service for automating movement and transformation of your data.
![[image.128.png]]![[image.129.png]]
Popular use cases are:

1. Processing data in EMR using Hadoop streaming
2. Importing and exporting DynamoDB data
3. Copying CSV files or data between S3 buckets
4. Exporting RDS data to S3
5. Copying data to Redshift

![[image.131.png]]

## Implementing Amazon Managed Streaming for Apache Kafka (AWS MSK)

Amazon MSK is a streaming service use for Apache Kafka. Fully managed service to run data streaming applications that use Kafka.
**MSK provides** control-plane operations such as creates, deletes and updates clusters as required and leverage Kafka data-plane operations for producing and consuming streaming data.
![[image.132.png]]
Amazon MSK automatically detect and recover from common failure scenarios. If a broker failure is detected it result in mitigation or replacement of unhealthy nodes. During failures we can try to reuse storage from older brokers to reduce data needing replication.
After successful recovery, producers and consumer apps continue to communicate with the same broker IP as before.
![[image.133.png]]
Amazon MSK will always encrypt your data at rest. MSK is integrated with Amazon KMS for SSE requirements.
We can deliver broker logs to Amazon CloudWatch, Amazon S3, and Amazon Kinesis Data Firehose

## OpenSearch service

OpenSearch is a managed service allowing you to run search and analytics engines for various use cases. (successor to Amazon Elasticsearch).
![[image.134.png]]![[image.135.png]]

# Monitoring

## AWS CloudWatch

CloudWatch is a monitoring and observability platform that was designed to give us insight into our AWS architecture. It allows us to monitor multiple levels of our applications and identify potential issues.
![[image.149.png]]

### CloudWatch Logs

CloudWatch logs is a tool that allows you to monitor, store, and access logs files from a variety of different sources. It gives you the ability to query your logs to look for potential issues or data that is relevant for you.
For custom logs , you use Amazon CloudWatch Agent. The agent enables user to collect and monitor system and application metrics on their AWS instances and on-premises servers.
![[image.150.png]]

### CloudWatch Logs Feature

1. **Filter Patterns:** you can look for specific terms in your logs. Think 400 errors in your web server logs.
2. **CloudWatch Logs Insights:** This allows you to query all your logs using a SQL-like interactive solution.
3. **Alarms:** Once you've identified your trends or patterns it's time to set up alerts for them.

![[image.151.png]]

## Amazon Managed Service for Prometheus and Grafana

Amazon Managed **Grafana** is a fully managed AWS service allowing secure data visualizations for instantly **querying, correlating and visualizing your operational metrics, logs, and traces** from different sources.
![[image.152.png]]
Amazon Managed Prometheus is a serverless, Prometheus-compatible service used for securely monitoring container metrics at scale.
![[image.153.png]]

### Exam Tips Grafana & Prometheus

![[image.154.png]]

# High Availability and Scaling

A launch template specifies all the needed **settings** that go into building out an EC2 instance. It is a collection of settings you can configure so you don't have to walk through the Ec2 wizard over and over.
![[image.155.png]]

## Scaling Ec2 Instances (ONLY Ec2)

An Auto Scaling group contains a collection of EC2 instances that are treated as a collective group for purposes of **scaling and management.**
![[image.156.png]]

### Auto Scaling Restrictions

Using properly auto scaling group allows us to set a minimum, maximum or desired requirement/state. A minimum requirement is the lowest number of Ec2 instances you'll ever have online. You won't dip below this.
A maximum requirement is the highest number of Ec2 instances you'll ever prevision. You won't go above this.
A desired requirement is the amount of instances we want right now.

### Auto Scaling policies

Thanks to Step Scaling we can create and manage the CloudWatch alarms that invoke the scaling process. When an alarm is breached, Amazon Ec2 Auto Scaling initiates the scaling policy associated with that alarm.
![[image.157.png]]

![[image.158.png]]

## Scaling Relational Databases

There are four different types of Scaling if we talk about relational DBs.

1. **Vertical Scaling:** Resizing database from one size to another can create greater performance. Remember that this action make you pay more.
2. **Scaling Storage:** storage can be resized, but it's only able to go up, not down.
3. **Read Replicas:** Creating read-only copies of our data can help spread out the workload. A major point to note for read replicas is that, obviously, they can't be used as any writing purposes.
4. **Aurora Serverless:** Excels with unpredictable workloads.

![[image.159.png]]

## Scaling Non-Relational DBs

Scaling for non relational database is simplified when using Amazon DynamoDB, as AWS does all the heavy lifting for you.
![[image.160.png]]
Read Capacity Unit (RCU) is a unit of measurement for reads per second for an item up to **4KB in size.**
Anything over 4KB require an additional RCU.
Write Capacity Unit (WCU) is a unit measurement for writes per second for an item up to **1KB in size.**
![[image.161.png]]

## Disaster Recovery Strategies

In the event of a disaster/failure, we have to decide at what point in time you want your data to be recovered. Typically speaking, the lower the time, the greater the cost. This period of time is called **Recovery Point Objective (RPO).**
Then, if we talk about **Recovery Time Objective (RTO),** is when we have to decide how fast we want to fail over. Also for this, the lower the time, the greater the cost.
The most basic disaster recovery strategy is **Backup and Restore.**

![[image.162.png]]
**Pilot Light** is a disaster recovery strategy.
![[image.164.png]]
As another strategy we have **Warm Standby.** Instead to replicate just Database we replicate also WebApp so if a region fails we can scale on the region which is in "warm standby" state.
![[image.163.png]]
The final strategy is Active/Active Failover. This strategy is also the most expensive disaster recovery. You have two sites, both active and traffic split between the two. If one site fails, the other site takes the load.

# Machine Learning

## Amazon Comprehend

Comprehend uses **natural-language processing (NLP)** to help you understand the meaning and sentiment in your text
![[image.136.png]]

## Amazon Kendra

Kendra allows you to create **intelligence search service** powered by **machine learning.**
Enterprise search applications can bridge between different silos of information (such as S3 buckets, file servers), allowing your enterprise to have all data intelligently in one place
![[image.137.png]]

## Amazon Textract

Textract uses machine learning to **automatically extract text, handwriting, and data** from scanned documents.
![[image.138.png]]

## Amazon Forecast

![[image.139.png]]
Amazon Forecast is a **time-series forecasting** service that uses machine learning and is built to give you important business insights.
You can send data automatically learn your data, select the right machine learning algorithm, and then help you forecast your data.

## Amazon Fraud Detector

Fraud Detector is a AI service that is built to detect fraud in your data. This service create a **fraud detection machine learning model** that is based on your data. This process can also be automated.
![[image.140.png]]

## Amazon Polly, Transcribe and Lex

**Transcribe** is used to convert **speech to text** automatically. You can use this service to generate subtitles on the fly.
**Lex** allows you to build conversational interfaces in your applications using **natural language models.** Probably, when you are talking to an automated bot online, you are **interacting with Lex Service.**
![[image.141.png]]
**Polly** turns your text into **lifelike speech** and allows you to create applications that talk to and interact with you using a variety of languages and accents.

## Amazon Rekognition

Rekognition is Amazon's computer vision product that automates the recognition of pictures and videos using deep learning and neural networks
![[image.142.png]]

## Amazon SageMaker

Amazon SageMaker is a fully managed machine learning (ML) service. With SageMaker, data scientists and developers can quickly and confidently build, train, and deploy ML models into a production-ready hosted environment. It provides a UI experience for running ML workflows that makes SageMaker ML tools available across multiple integrated development environments (IDEs).

In the AWS Console, it's divided into four sub-sections:
![[image.143.png]]![[image.144.png]]
Training data can come from a lot of different services such as AWS Console, SDK, S3.
SageMaker Neo allows you to customize your machine learning models for specific CPU hardware, such as ARM, Intel, and INVIDIA processors.
It includes a compiler to convert the machine learning model to an environment that is optimized to execute the model on the target architecture.
![[image.145.png]]
Elastic Inference (EI) speeds up throughput and decreases latency real-time inferences deployed on SageMaker hosted services using only CPU-based instances.

## Amazon Translate

A machine learning service that allows you to automate **language translation.** Using deep learning and neural networks, Amazon Translate allows you to translate from one language to another.
![[image.146.png]]

# Decoupling, Serverless and Automation

**Thight coupling** means we have an ec2 instance talking directly with another ec2 instance. This is a single point of failure. **Loose Coupling** Between user and front-end and between frontend and backend we should put an ELB with at least 3 ec2 instances talking with ELB. So, if an ec2 instance fail, not all our application go down.
ELB is not always the answer. We have to take a look to other services that can help on this:

## Simple Queue Service (SQS)

Fully managed message queuing service that enables you to decouple and scale microservices, distributed systems, and serverless applications.

## Simple Notifications Service (SNS)

Fully managed messaging service for both application-to-application (A2A) and application-to-person (A2P) communication.

## API Gateway

Fully managed service that makes it easy for developers to create, publish, mantain, monitor and secure APIs at any scale.
