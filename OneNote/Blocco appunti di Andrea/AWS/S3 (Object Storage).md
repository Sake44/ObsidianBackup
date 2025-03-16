Object storage is built for the cloud and delivers virtually unlimited scalability, high durability, and cost effectiveness.
 
**Amazon S3**  
Unlike Amazon EBS, Amazon Simple Storage Service (Amazon S3) is a standalone storage solution that isn’t tied to compute. With Amazon S3, you can retrieve your data from anywhere on the web. If you have used an online storage service to back up the data from your local machine, you most likely have used a service similar to Amazon S3. The big difference between those online storage services and Amazon S3 is the storage type.
 
Amazon S3 is an object storage service. Object storage stores data in a flat structure. An object is a file combined with metadata. You can store as many of these objects as you want. All the characteristics of object storage are also characteristics of Amazon S3.

In Amazon S3, you store your objects in containers called buckets. You can’t upload an object, not even a single photo, to Amazon S3 without creating a bucket first. When you store an object in a bucket, the combination of a bucket name, key, and version ID uniquely identifies the object.  
 
**Object key names**  
The object key (key name) uniquely identifies the object in an Amazon S3 bucket. When you create an object, you specify the key name. As described earlier, the Amazon S3 model is a flat structure, meaning there is no hierarchy of subbuckets or subfolders. However, the Amazon S3 console does support the concept of folders. By using key name prefixes and delimiters, you can imply a logical hierarchy.  
 ![By using prefixes and delimiters, you can infer a logical hierarchy resembling folders.](Exported%20image%2020250315115734-0.png)

**Amazon S3 use cases**
 
Amazon S3 is a widely used storage service, with far more use cases than could fit on one screen.
 
**Backup and storage**
 
Amazon S3 is a natural place to back up files because it is highly redundant. As mentioned in the last lesson, AWS stores your EBS snapshots in Amazon S3 to take advantage of its high availability.
 >  

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

**Amazon S3 and IAM policies**  
Previously, you learned about creating and using AWS Identity and Access Management (IAM) policies. Now you can apply that knowledge to Amazon S3. When IAM policies are attached to your resources (buckets and objects) or IAM users, groups, and roles, the policies define which actions they can perform. Access policies that you attach to your resources are referred to as _resource-based policies_ and access policies attached to users in your account are called _user policie_**s**.
 
**Amazon S3 encryption**  
Amazon S3 reinforces encryption in transit (as it travels to and from Amazon S3) and at rest. To protect data, Amazon S3 automatically encrypts all objects on upload and applies server-side encryption with S3-managed keys as the base level of encryption for every bucket in Amazon S3 at no additional cost.
 
**Amazon S3 bucket policies**  
Like IAM policies, S3 bucket policies are defined in a JSON format. Unlike IAM policies, which are attached to resources and users, S3 bucket policies can only be attached to S3 buckets. The policy that is placed on the bucket applies to every object in that bucket. S3 bucket policies specify what actions are allowed or denied on the bucket.
 >  

==You should use S3 bucket policies in the following scenarios:==

- ==You need a simple way to do cross-account access to Amazon S3, without using IAM roles.==
- ==Your IAM policies bump up against the defined size limit. S3 bucket policies have a larger size limit.==

==For examples of bucket policies, see the== ==Bucket Policy Examples== ==link here or in the resources section.==
 
**Amazon S3 encryption**  
Amazon S3 reinforces encryption in transit (as it travels to and from Amazon S3) and at rest. To protect data, Amazon S3 automatically encrypts all objects on upload and applies server-side encryption with S3-managed keys as the base level of encryption for every bucket in Amazon S3 at no additional cost.

==Storage Classes==
    
|
|
==Storage Class== ==Description==
==S3 Standard== ==This is considered general-purpose storage for cloud applications, dynamic websites, content distribution, mobile and gaming applications, and big data analytics.==
==S3 Intelligent-Tiering== ==This tier is useful if your data has unknown or changing access patters. S3 Intelligent-Tiering stores objects in three tiers: a frequent access tier, an infrequent access tier, and an archive instance access tier. Amazon S3 monitors access patterns of your data and automatically moves your data to the most cost-effective storage tier based on frequency of access.==
==S3 Standard-Infrequent Access (S3 Standard-IA)== ==This tier is for data that is accessed less frequently but requires rapid access when needed. S3 Standard-IA offers the high durability, high throughput, and low latency of S3 Standard, with a low per-GB storage price and per-GB retrieval fee. This storage tier is ideal if you want to store long-term backups, disaster recovery files, and so on.==
==S3 One Zone-Infrequent Access (S3 One Zone-IA)== ==Unlike other S3 storage classes that store data in a minimum of three Availability Zones, S3 One Zone-IA stores data in a single Availability Zone, which makes it less expensive than S3 Standard-IA. S3 One Zone-IA is ideal for customers who want a lower-cost option for infrequently accessed data, but do not require the availability and resilience of S3 Standard or S3 Standard-IA. It's a good choice for storing secondary backup copies of on-premises data or easily recreatable data.==
==S3 Glacier Instant Retrieval== ==Use S3 Glacier Instant Retrieval for archiving data that is rarely accessed and requires millisecond retrieval. Data stored in this storage class offers a cost savings of up to 68 percent compared to the S3 Standard-IA storage class, with the same latency and throughput performance.==
==S3 Glacier Flexible Retrieval== ==S3 Glacier Flexible Retrieval offers low-cost storage for archived data that is accessed 1–2 times per year. With S3 Glacier Flexible Retrieval, your data can be accessed in as little as 1–5 minutes using an expedited retrieval. You can also request free bulk retrievals in up to 5–12 hours. It is an ideal solution for backup, disaster recovery, offsite data storage needs, and for when some data occasionally must be retrieved in minutes.==
==S3 Glacier Deep Archive== ==S3 Glacier Deep Archive is the lowest-cost Amazon S3 storage class. It supports long-term retention and digital preservation for data that might be accessed once or twice a year. Data stored in the S3 Glacier Deep Archive storage class has a default retrieval time of 12 hours. It is designed for customers that retain data sets for 7–10 years or longer, to meet regulatory compliance requirements. Examples include those in highly regulated industries, such as the financial services, healthcare, and public sectors.==
==S3 on Outposts== ==Amazon S3 on Outposts delivers object storage to your on-premises AWS Outposts environment using S3 API's and features. For workloads that require satisfying local data residency requirements or need to keep data close to on premises applications for performance reasons, the S3 Outposts storage class is the ideal option.== 

Amazon S3 versioning
 
 Versioning keeps multiple versions of a single object in the same bucket. This preserves old versions of an object without using different names, which helps with object recovery from accidental deletions, accidental overwrites, or application failures.
   

**Managing your storage lifecycle**  
If you keep manually changing your objects, such as your employee photos, from storage tier to storage tier, you might want to automate the process by configuring their Amazon S3 lifecycle. When you define a lifecycle configuration for an object or group of objects, you can choose to automate between two types of actions: transition and expiration.

- **Transition actions** define when objects should transition to another storage class.
- **Expiration actions** define when objects expire and should be permanently deleted.
    ![Select transition and expiration actions for objects with storage lifecycles.](Exported%20image%2020250315115737-1.png)

**Resources**  
[(opens in a new tab)](https://aws.amazon.com/s3/)  
For more information, see the following resources:

- AWS website: [Amazon S3](https://aws.amazon.com/s3/)
- AWS website: [Amazon S3 Storage Classes](https://aws.amazon.com/s3/storage-classes/)
- AWS user guide: [Using Versioning in S3 Buckets](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Versioning.html)
- AWS user guide: [Bucket Naming Rules](https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucketnamingrules.html)
- AWS user guide: [Bucket Policy Examples](https://docs.aws.amazon.com/en_us/AmazonS3/latest/userguide/example-bucket-policies.html)