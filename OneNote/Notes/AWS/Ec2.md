Amazon EC2 is a web service that provides secure, resizable compute capacity in the cloud. With this service, you can provision virtual servers called EC2 instances.

### Amazon Machine Image
 
When launching an EC2 instance, the first setting you configure is which operating system you want by selecting an Amazon Machine Image (AMI).

#### Amazon EC2 instance types
EC2 instances are a combination of virtual processors (vCPUs), memory, network, and, in some cases, instance storage and graphics processing units (GPUs). When you create an EC2 instance, you need to choose how much you need of each of these components.
 ![Instance types are named based on their family, generation, additional capabilities, and size.](Exported%20image%2020250315115714-0.jpeg)

### Ec2 instance families

Pick the optimal instance family for the type of workload you plan to deploy. Doing this saves time and cost, and reduces the need to resize later. Some instance types are only available in certain Regions.

![[Pasted image 20251026125739.png]]

**General Purpose: **
- Balance of compute, memory and networking
- Diverse workloads
- Web applications
**Compute Optimized:**
- Scientific modeling
- Machine learning
- Compute-bound applications
**Memory Optimized:**
- Fast delivery of large datasets in memory
- Database servers
- Web caches
- Data analytics
**Accelerated Computing:**
- High-graphics processing
- GPU bound
- Machine learning
- High performance computing (HPC)
**Storage Optimized:**
- High sequential read/write
- Large datasets
- NoSQL databases
- Amazon OpenSearch Service
**High performance Computing (HPC) optimezed:**
- Purpose-built
- Compute-intensive high performance computing (HPC) workloads
- Workloads at scale

### AWS Compute Optimizer
**AWS Compute Optimizer** uses machine learning to analyze the current configuration of your resources and your usage data from Amazon CloudWatch. You receive compute recommendations based on your configuration and usage.
![[Pasted image 20251026131206.png]]

### Amazon Ec2 Key Pairs
A key pair, consisting of a private key and a public key, is a set of security credentials that you use to prove your identity when connecting to an instance. Amazon EC2 stores the public key and you store the private key. You use the private key instead of a password to securely access your instances.

### Tenancy
AWS compute tenancy refers to how EC2 instances are distributed across the underlying physical hardware, with three main options - shared tenancy, dedicated instance, or dedicated host.

1. **Shared Tenancy:** By default, EC2 instances have shared tenancy, meaning multiple AWS accounts might share the same physical hardware.
2. **Dedicated Instance:** Dedicated Instances are EC2 instances that are physically isolated at the host hardware level from instances that aren't dedicated and from instances that belong to other AWS accounts.
3. **Dedicated host:** When you launch instances on a Dedicated Host, the instances run on a physical server with EC2 instance capacity fully dedicated to your use.

### Placement group and Use cases
  
The Amazon EC2 service attempts to spread out all of your instances across underlying hardware to minimize correlated failures. You can use placement groups to influence the placement of a set of interdependent instances to meet the needs of your workload.
**Cluster placement groups** are recommended for your applications that benefit from low network latency, high network throughput, or both.
**Spread placement groups** are recommended for applications that have a small number of critical instances that should be kept separate from each other.
**Partition placement groups** can be used to deploy your large distributed and replicated workloads.

### User Data
When creating your EC2 instances, you have the option of passing user data to the instance. User data can automate the completion of the instance launch.
The user data field is executed by **cloud-init** on Linux and by the **EC2Launch** service on Windows.