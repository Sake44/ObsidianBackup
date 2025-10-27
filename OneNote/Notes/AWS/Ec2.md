Amazon EC2 is a web service that provides secure, resizable compute capacity in the cloud. With this service, you can provision virtual servers called EC2 instances.

### Amazon Machine Image
 
When launching an EC2 instance, the first setting you configure is which operating system you want by selecting an Amazon Machine Image (AMI).

#### Amazon EC2 instance types
EC2 instances are a combination of virtual processors (vCPUs), memory, network, and, in some cases, instance storage and graphics processing units (GPUs). When you create an EC2 instance, you need to choose how much you need of each of these components.
 ![Instance types are named based on their family, generation, additional capabilities, and size.](Exported%20image%2020250315115714-0.jpeg)

### Ec2 instance families

Pick the optimal instance family for the type of workload you plan to deploy. Doing this saves time and cost, and reduces the need to resize later. Some instance types are only available in certain Regions.

![[Pasted image 20251026125739.png]]

**General Purpose:**
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

## Ec2 Instance Lifecycle
![The transition between different EC2 instance states from launch through to termination.](Exported%20image%2020250315115714-0.png)


1. When you launch an instance, it enters the **pending** state. When an instance is pending, billing has not started. At this stage, the instance is preparing to enter the running state. Pending is where AWS performs all actions needed to set up an instance, such as copying the AMI content to the root device and allocating the necessary networking components.
2. When your instance is **running**, it's ready to use. This is also the stage where billing begins. As soon as an instance is running, you can take other actions on the instance, such as reboot, terminate, stop, and stop-hibernate.
3. When you reboot an instance, it’s different than performing a stop action and then a start action. **Rebooting** an instance is equivalent to rebooting an operating system. The instance keeps its public DNS name (IPv4) and private and public IPv4 addresses. An IPv6 address (if applicable) remains on the same host computer and maintains its public and private IP address, in addition to any data on its instance store volumes.
4. When you stop your instance, it enters the **stopping** and then **stopped** state. This is similar to when you shut down your laptop. You can stop and start an instance if it has an Amazon Elastic Block Store (Amazon EBS) volume as its root device. When you stop and start an instance, your instance can be placed on a new underlying physical server. Your instance retains its private IPv4 addresses and if your instance has an IPv6 address, it retains its IPv6 address. When you put the instance into stop-hibernate, the instance enters the stopped state, but saves the last information or content into memory, so that the start process is faster.
5. When you== **terminate** an instance, the instance stores are erased, and you lose both the public IP address and private IP address of the machine. Termination of an instance means that you can no longer access the machine. As soon as the status of an instance changes to== **shutting down** or **terminated**, you stop incurring charges for that instance.