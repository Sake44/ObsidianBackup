Amazon RDS is a managed database service customers can use to create and manage relational databases in the cloud without the operational burden of traditional database management.
 
==With Amazon RDS, you can offload some of the unrelated work of creating and managing a database. You can focus on the tasks that differentiate your application, instead of focusing on infrastructure-related tasks, like provisioning, patching, scaling, and restoring.==
 
==Amazon RDS supports most of the popular RDBMSs, ranging from commercial options to open-source options and even a specific AWS option. Supported Amazon RDS engines include the following:==

- **Commercial:** ==Oracle, SQL Server==
- **Open source:** ==MySQL, PostgreSQL, MariaDB==
- **Cloud native:** ==Aurora== 
 
Underneath the DB instance is an EC2 instance. However, this instance is managed through the Amazon RDS console instead of the Amazon EC2 console.  
**Storage on Amazon RDS**  
The storage portion of DB instances for Amazon RDS use Amazon Elastic Block Store (Amazon EBS) volumes for database and log storage. This includes MySQL, MariaDB, PostgreSQL, Oracle, and SQL Server.   
When using Aurora, data is stored in cluster volumes, which are single, virtual volumes that use solid-state drives (SSDs). A cluster volume contains copies of your data across three Availability Zones in a single AWS Region. For nonpersistent, temporary files, Aurora uses local storage.
 
Amazon RDS provides three storage types: General Purpose SSD (also called gp2 and gp3), Provisioned IOPS SSD (also called io1), and Magnetic (also called standard). They differ in performance characteristics and price, which means you can tailor your storage performance and cost to the needs of your database workload.

**Amazon RDS in an Amazon Virtual Private Cloud**  
When you create a DB instance, you select the Amazon Virtual Private Cloud (Amazon VPC) your databases will live in. Then, you select the subnets that will be designated for your DB. This is called a DB subnet group, and it has at least two Availability Zones in its Region. The subnets in a DB subnet group should be private, so they don’t have a route to the internet gateway. This ensures that your DB instance, and the data inside it, can be reached only by the application backend.
 
Access to the DB instance can be restricted further by using network access control lists (network ACLs) and security groups. With these firewalls, you can control, at a granular level, the type of traffic you want to provide access into your database.
    
**Data Backup**
 
To take regular backups of your Amazon RDS instance, you can use automated backups or manual snapshots.
 
**Automated Backups**
 
Automated backups are turned on by default. This backs up your entire DB instance (not just individual databases on the instance) and your transaction logs. When you create your DB instance, you set a backup window that is the period of time that automatic backups occur. Typically, you want to set the window during a time when your database experiences little activity because it can cause increased latency and downtime.
 
**Retaining backups:** Automated backups are retained between 0 and 35 days. You might ask yourself, “Why set automated backups for 0 days?” The 0 days setting stops automated backups from happening. If you set it to 0, it will also delete all existing automated backups. This is not ideal. The benefit of automated backups that you can do point-in-time recovery.
 
**Point-in-time recovery:** This creates a new DB instance using data restored from a specific point in time. This restoration method provides more granularity by restoring the full backup and rolling back transactions up to the specified time range.
 
**Manual Snapshots**  
If you want to keep your automated backups longer than 35 days, use manual snapshots. Manual snapshots are similar to taking Amazon EBS snapshots, except you manage them in the Amazon RDS console. These are backups that you can initiate at any time. They exist until you delete them. For example, to meet a compliance requirement that mandates you to keep database backups for a year, you need to use manual snapshots. If you restore data from a manual snapshot, it creates a new DB instance using the data from the snapshot.

**Redundancy with Amazon RDS Multi-AZ**  
In an Amazon RDS Multi-AZ deployment, Amazon RDS creates a redundant copy of your database in another Availability Zone. You end up with two copies of your database—a primary copy in a subnet in one Availability Zone and a standby copy in a subnet in a second Availability Zone.
 
The primary copy of your database provides access to your data so that applications can query and display the information. The data in the primary copy is synchronously replicated to the standby copy. The standby copy is not considered an active database, and it does not get queried by applications.
 ![Diagram depicting Amazon RDS Multi-AZ creating a redundant copy of a database in another Availability Zone.](Exported%20image%2020250315115739-0.png)  

**Resources**  
For more information, see the following resources:
 
- AWS website: [Amazon RDS](https://aws.amazon.com/rds/)￼
- AWS user guide: [Configuring an Amazon RDS DB Instance](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_RDS_Configuring.html)￼
- AWS user guide: [Backing up and restoring an Amazon RDS DB instance](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_CommonTasks.BackupRestore.html)￼
- AWS user guide: [Security in Amazon RDS](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.html)