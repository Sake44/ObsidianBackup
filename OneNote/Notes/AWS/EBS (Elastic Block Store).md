**Amazon EC2 instance store**  
Amazon Elastic Compute Cloud (Amazon EC2) instance store provides temporary block-level storage for an instance. This storage is located on disks that are physically attached to the host computer. This ties the lifecycle of the data to the lifecycle of the EC2 instance. If you delete the instance, the instance store is also deleted. Because of this, instance store is considered ephemeral storage.
 ![Two types of block storage in AWS are Amazon EC2 instance store and Amazon EBS.](Exported%20image%2020250315115731-0.png)  

**Amazon EBS**  
As the name implies, Amazon Elastic Block Store (Amazon EBS) is block-level storage that you can attach to an Amazon EC2 instance.
 - **Detachable:** ==You can detach an EBS volume from one EC2 instance and attach it to another EC2 instance in the same Availability Zone to access the data on it.==
- ==•====￼==**Distinct:** ==The external drive is separate from the computer. That means that if an accident occurs and the computer goes down, you still have your data on your external drive. The same is true for EBS volumes.==
- ==•====￼==**Size-limited:** ==You’re limited to the size of the external drive, because it has a fixed limit to how scalable it can be. For example, you might have a 2 TB external drive, which means you can only have 2 TB of content on it. This also relates to Amazon EBS, because a volume also has a max limitation of how much content you can store on it.==
- ==•====￼==**1-to-1 connection:** ==Most external drives can only be connected with one computer at a time. Most EBS volumes have a one-to-one relationship with EC2 instances, so they cannot be shared by or attached to multiple instances at one time.==
- ==When you create an EBS volume, it is automatically replicated in its Availability Zone to prevent data loss from single points of failure.==          

**Amazon EBS use cases**  
Amazon EBS is useful when you must retrieve data quickly and have data persist long term. Volumes are commonly used in the following scenarios.
 
**Operating systems**
 
Boot and root volumes can be used to store an operating system. The root device for an instance launched from an Amazon Machine Image (AMI) is typically an EBS volume. These are commonly referred to as EBS-backed AMIs.
 
**Databases**
 
As a storage layer for databases running on Amazon EC2 that will scale with your performance needs and provide consistent and low-latency performance.
 
**Enterprise applications**
 
Amazon EBS provides high availability and high durability block storage to run business-critical applications.
 
**Big data analytics engines**
 
Amazon EBS offers data persistence, dynamic performance adjustments, and the ability to detach and reattach volumes, so you can resize clusters for big data analytics.

**EBS volume types**  
EBS volumes are organized into two main categories: solid-state drives (SSDs) and hard-disk drives (HDDs). SSDs are used for transactional workloads with frequent read/write operations with small I/O size. HDDs are used for large streaming workloads that need high throughput performance.  AWS offers two types of each.
 
**SSD**
 ![Exported image](Exported%20image%2020250315115731-1.png)

![Exported image](Exported%20image%2020250315115732-2.png)

**Amazon EBS snapshots**  
Errors happen. One error is not backing up data and then inevitably losing it. To prevent this from happening to you, always back up your data, even in AWS. Because your EBS volumes consist of the data from your EC2 instance, you should make backups of these volumes, called snapshots.
 
EBS snapshots are incremental backups that only save the blocks on the volume that have changed after your most recent snapshot. ==For example, if you have 10 GB of data on a volume and only 2 GB of data have been modified since your last snapshot, only the 2 GB that have been changed are written to Amazon S3.==

==Resources==
 - ==AWS user guide:== ==Amazon EC2 Instance Store==
- ==AWS user guide:== ==Amazon Elastic Block Store (Amazon EBS)==
- ==AWS FAQs:== ==Amazon EBS==