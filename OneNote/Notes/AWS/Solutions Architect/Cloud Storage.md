AWS storage services are grouped into three categories: file storage, block storage, and object storage. In file storage, data is stored as files in a hierarchy. In block storage, data is stored in fixed-size blocks. And in object storage, data is stored as objects in buckets.

## Block Storage 
**Block storage**, like AWS EBS, divides data into fixed-size blocks and is ideal for operating systems and databases requiring low-latency

### Amazon EC2 Instance Store
Amazon Elastic Compute Cloud (Amazon EC2) instance store provides temporary block-level storage for an instance. This storage is located on disks that are physically attached to the host computer.
It’s ideal for temporary storage of information that changes frequently, such as buffers, caches, scratch data
![[Pasted image 20251026154908.png]]

### Amazon EBS
As the name implies, Amazon Elastic Block Store (Amazon EBS) is block-level storage that you can attach to an Amazon EC2 instance.
This attachable storage is called an EBS volume. EBS volumes act similarly to external drives in more than one way.

- **Detachable:** You can detach an EBS volume from one EC2 instance and attach it to another EC2 instance in the same Availability Zone to access the data on it.
- **Distinct:** The external drive is separate from the computer. The same is true for EBS
- **Size-limited**: You’re limited to the size of the external drive, because it has a fixed limit to how scalable it can be. This also relates to Amazon EBS
- **1-to-1 connection**: Most EBS volumes can only be connected with one computer at a time. Most EBS volumes have a one-to-one relationship with EC2 instances

**N.B AWS announced the Amazon EBS multi-attach feature that permits Provisioned IOPS SSD (io1 or io2) volumes to be attached to multiple EC2 instances at one time. This feature is not available for all instance types**

#### EBS Volume Types
EBS volumes are organized into two main categories: solid-state drives (SSDs) and hard-disk drives (HDDs).
###### SSD Volumes

| **General Purpose**   <br>**SSD volumes** |                                                                                           |           | **Provisioned IOPS**   <br>**SSD volumes**                                           |             |     |
| :---------------------------------------: | :---------------------------------------------------------------------------------------: | :-------: | ------------------------------------------------------------------------------------ | ----------- | --- |
|              **Volume type**              |                                            gp3                                            |    gp2    | io2 Block Express                                                                    | io1         |     |
|              **Description**              | Provides a balance of price and performance for a wide variety of transactional workloads |           | Provides high-performance SSD designed for latency-sensitive transactional workloads |             |     |
|              **Volume size**              |                                       1 GiB–16 TiB                                        |           | 4 GiB–64 TiB                                                                         | 4GiB–16 TiB |     |
|     **Max IOPS**   <br>**per volume**     |                                          16,000                                           |           | 256,000                                                                              | 64,000      |     |
|       **Max throughput per volume**       |                                        1,000 MiB/s                                        | 250 MiB/s | 4,000 MiB/s                                                                          | 1,000 MiB/s |     |
|        **Amazon EBS Multi-attach**        |                                       Not supported                                       |           | Supported                                                                            |             |     |
###### HHD Volumes
|                               | Throughput Optimized HDD volumes                                                | **Cold HDD volumes**                                                |
| ----------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **Volume type**               | st1                                                                             | sc1                                                                 |
| **Description**               | A low-cost HDD designed for frequently accessed, throughput-intensive workloads | The lowest cost HDD designed for less frequently accessed workloads |
| **Volume size**               | 125 GiB–16 TiB                                                                  | 125 GiB–16 TiB                                                      |
| **Max IOPS per volume**       | 500                                                                             | 250                                                                 |
| **Max throughput per volume** | 500 MiB/s                                                                       | 250 MiB/s                                                           |
| **Amazon EBS Multi-attach**   | Not supported                                                                   | Not supported                                                       |
#### Amazon EBS benefits
1. High Availability: When you create an EBS volume, it is automatically replicated in its Availability Zone to prevent data loss from single points of failure.
2. Data persistence: Storage persists even when your instance doesn’t.
3. Data encryption: When activated by the user, all EBS volumes support encryption.
4. **Flexibility**: EBS volumes support on-the-fly changes. Modify volume type, volume size, and input/output operations per second (IOPS) capacity without stopping your instance.
5. **Backups**: Amazon EBS provides the ability to create backups of any EBS volume.

##### Amazon EBS use cases
Amazon EBS is useful when you must retrieve data quickly and have data persist long term. Volumes are commonly used in the following scenarios.
 
**Operating systems**
Boot and root volumes can be used to store an operating system. The root device for an instance launched from an Amazon Machine Image (AMI) is typically an EBS volume. These are commonly referred to as EBS-backed AMIs.

**Databases**
As a storage layer for databases running on Amazon EC2 that will scale with your performance needs and provide consistent and low-latency performance.
 
**Enterprise applications**
Amazon EBS provides high availability and high durability block storage to run business-critical applications.
 
**Big data analytics engines**
Amazon EBS offers data persistence, dynamic performance adjustments, and the ability to detach and reattach volumes, so you can resize clusters for big data analytics.

#### Amazon EBS Snapshots
Errors happen. One error is not backing up data and then inevitably losing it. To prevent this from happening to you, always back up your data, even in AWS. Because your EBS volumes consist of the data from your EC2 instance, you should make backups of these volumes, called snapshots.
EBS snapshots are incremental backups that only save the blocks on the volume that have changed after your most recent snapshot.

## File Storage

### Amazon EFS

Amazon Elastic File System (Amazon EFS) is a set-and-forget file system that automatically grows and shrinks as you add and remove files. There is no need for provisioning or managing storage capacity and performance.

| Standard storage classes                                                                                                                                                                               | One zone storage classes                                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| Standard storage classes  One zone storage classes  <br>EFS Standard and EFS Standard-Infrequent Access (Standard-IA) offer Multi-AZ resilience and the highest levels of durability and availability. | EFS One Zone and EFS One Zone-Infrequent Access (EFS One Zone-IA) provide additional savings by saving your data in a single availability zone. |

### Amazon FSx
Amazon FSx is a fully managed service that offers reliability, security, scalability, and a broad set of capabilities that make it convenient and cost effective to launch, run, and scale high-performance file systems in the cloud.

## Object Storage

### Amazon S3
Unlike Amazon EBS, Amazon Simple Storage Service (Amazon S3) is a standalone storage solution that isn’t tied to compute. With Amazon S3, you can retrieve your data from anywhere on the web. If you have used an online storage service to back up the data from your local machine, you most likely have used a service similar to Amazon S3. The big difference between those online storage services and Amazon S3 is the storage type.
 
Amazon S3 is an object storage service. Object storage stores data in a flat structure. An object is a file combined with metadata. You can store as many of these objects as you want. All the characteristics of object storage are also characteristics of Amazon S3.

In Amazon S3, you store your objects in containers called buckets. You can’t upload an object, not even a single photo, to Amazon S3 without creating a bucket first.

#### Amazon S3 Use cases
Amazon S3 is a widely used storage service, with far more use cases than could fit on one screen.
 
**Backup and storage**
Amazon S3 is a natural place to back up files because it is highly redundant. As mentioned in the last lesson, AWS stores your EBS snapshots in Amazon S3 to take advantage of its high availability.

**Media hosting**
Because you can store unlimited objects, and each individual object can be up to 5 TB, Amazon S3 is an ideal location to host video, photo, and music uploads.
 
**Software delivery**
You can use Amazon S3 to host your software applications that customers can download.

**Data lakes**
Amazon S3 is an optimal foundation for a data lake because of its virtually unlimited scalability. You can increase storage from gigabytes to petabytes of content, paying only for what you use.
   
**Static websites**
You can configure your S3 bucket to host a static website of HTML, CSS, and client-side scripts.
 
**Static content**
Because of the limitless scaling, the support for large files, and the fact that you can access any object over the web at any time, Amazon S3 is the perfect place to store static content.

#### Amazon S3 Encryption
Amazon S3 reinforces encryption in transit (as it travels to and from Amazon S3) and at rest. To protect data, Amazon S3 automatically encrypts all objects on upload and applies server-side encryption with S3-managed keys as the base level of encryption for every bucket in Amazon S3 at no additional cost.

#### S3 Bucket Policies
Like IAM policies, S3 bucket policies are defined in a JSON format. Unlike IAM policies, which are attached to resources and users, S3 bucket policies can only be attached to S3 buckets. The policy that is placed on the bucket applies to every object in that bucket. S3 bucket policies specify what actions are allowed or denied on the bucket.
You should use S3 bucket policies in the following scenarios:

- You need a simple way to do cross-account access to Amazon S3, without using IAM roles.
- Your IAM policies bump up against the defined size limit. S3 bucket policies have a larger size limit.

#### Amazon S3 Storage Classes
Amazon S3 storage classes let you change your storage tier when your data characteristics change.
Storage Class

##### S3 Standard
This is considered general-purpose storage for cloud applications, dynamic websites, content distribution, mobile and gaming applications, and big data analytics.

##### S3 Intelligent-Tiering
This tier is useful if your data has unknown or changing access patters. S3 Intelligent-Tiering stores objects in four tiers: a frequent access tier, an infrequent access tier, an archive instance access tier, and an archive access tier. Amazon S3 monitors access patterns of your data and automatically moves your data to the most cost-effective storage tier based on frequency of access.

##### S3 Standard-Infrequent Access (S3 Standard-IA)
This tier is for data that is accessed less frequently but requires rapid access when needed. S3 Standard-IA offers the high durability, high throughput, and low latency of S3 Standard, with a low per-GB storage price and per-GB retrieval fee. This storage tier is ideal if you want to store long-term backups, disaster recovery files, and so on.

##### S3 Express One Zone
Optimized for your most frequently accessed data and low-latency applications within a single Availability Zone, often used with S3 Directory Buckets for high-performance workloads.

##### S3 One Zone-Infrequent Access (S3 One Zone-IA)
Unlike other S3 storage classes that store data in a minimum of three Availability Zones, S3 One Zone-IA stores data in a single Availability Zone, which makes it less expensive than S3 Standard-IA. S3 One Zone-IA is ideal for customers who want a lower-cost option for infrequently accessed data, but do not require the availability and resilience of S3 Standard or S3 Standard-IA. It's a good choice for storing secondary backup copies of on-premises data or easily re-creatable data.

##### S3 Glacier Instant Retrieval
Use S3 Glacier Instant Retrieval for archiving data that is rarely accessed and requires millisecond retrieval. Data stored in this storage class offers a cost savings of up to 68 percent compared to the S3 Standard-IA storage class, with the same latency and throughput performance.

##### S3 Glacier Flexible Retrieval
S3 Glacier Flexible Retrieval offers low-cost storage for archived data that is accessed 1–2 times per year. With S3 Glacier Flexible Retrieval, your data can be accessed in as little as 1–5 minutes using an expedited retrieval. You can also request free bulk retrievals in up to 5–12 hours. It is an ideal solution for backup, disaster recovery, offsite data storage needs, and for when some data occasionally must be retrieved in minutes.

##### S3 Glacier Deep Archive
S3 Glacier Deep Archive is the lowest-cost Amazon S3 storage class. It supports long-term retention and digital preservation for data that might be accessed once or twice a year. Data stored in the S3 Glacier Deep Archive storage class has a default retrieval time of 12 hours. It is designed for customers that retain data sets for 7–10 years or longer, to meet regulatory compliance requirements. Examples include those in highly regulated industries, such as the financial services, healthcare, and public sectors.

##### S3 Resources
- AWS website: [Amazon S3](https://aws.amazon.com/s3/)
- AWS website: [Amazon S3 Storage Classes](https://aws.amazon.com/s3/storage-classes/)
- AWS user guide: [Using Versioning in S3 Buckets](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Versioning.html)
- AWS user guide: [Bucket Naming Rules](https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucketnamingrules.html)
- AWS user guide: [Bucket Policy Examples](https://docs.aws.amazon.com/en_us/AmazonS3/latest/userguide/example-bucket-policies.html)
- AWS user guide: [Amazon EC2 Storage](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Storage.html)
- AWS website: [Cloud Storage on AWS](https://aws.amazon.com/products/storage/)
- AWS website: [Amazon EBS](https://aws.amazon.com/ebs/)
- AWS user guide: [Amazon EFS: How It Works](https://docs.aws.amazon.com/efs/latest/ug/how-it-works.html)
- AWS website: [Amazon FSx](https://aws.amazon.com/fsx/)