
| Relational Database                                                                                                                                           | NoSQL Database                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| You require strict schema rules and data quality enforcement.                                                                                                 | You need your database to scale horizontally.                                                             |
| Your database doesn’t need extreme read/write capacity.                                                                                                       | Your data does not lend itself well to traditional schemas.                                               |
| If you have a relational data set that does not require extreme performance, a relational database management system can be the best, lowest effort solution. | Your read/write rates exceed those that can be economically supported through a traditional SQL database. |
## Amazon Relational Database Service (RDS)
Amazon RDS is a managed database service customers can use to create and manage relational databases in the cloud without the operational burden of traditional database management.
Amazon RDS supports most of the popular RDBMSs, ranging from commercial options to open-source options and even a specific AWS option.
Just like the databases you build and manage yourself, Amazon RDS is built from compute and storage. The compute portion is called the database (DB) instance, which runs the DB engine.
Underneath the DB instance is an EC2 instance. However, this instance is managed through the Amazon RDS console instead of the Amazon EC2 console.

Amazon RDS provides three storage types: General Purpose SSD (al
so called gp2 and gp3), Provisioned IOPS SSD (also called io1), and Magnetic (also called standard). They differ in performance characteristics and price, which means you can tailor your storage performance and cost to the needs of your database workload.

### Amazon RDS in VPC
When you create a DB instance, you select the Amazon Virtual Private Cloud (Amazon VPC) your databases will live in. Then, you select the subnets that will be designated for your DB. This is called a DB subnet group, and it has at least two Availability Zones in its Region. The subnets in a DB subnet group should be private, so they don’t have a route to the internet gateway. This ensures that your DB instance, and the data inside it, can be reached only by the application backend.

## Purpose-built Databases
AWS offers more than 15 purpose-built engines to support diverse data models, including relational, key-value, document, in-memory, graph, time series, wide column, and ledger databases.

### Amazon DynamoDB
DynamoDB is a fully managed NoSQL database that provides fast, consistent performance at any scale. It has a flexible billing model, tight integration with infrastructure as code (IaC)
DynamoDB has become the database of choice for two categories of applications: high-scale applications and serverless applications.
### Amazon Elastic Cache
ElastiCache is a fully managed, in-memory caching solution. It provides support for two open-source, in-memory cache engines: **Redis and Memcached**.
### Amazon MemoryDB for Redis
MemoryDB is a Redis-compatible, durable, in-memory database service that delivers ultra-fast performance. With MemoryDB, you can achieve microsecond read latency, single-digit millisecond write latency, high throughput
### Amazon DocumentDB (with MongoDB compatibility)
Amazon DocumentDB is a fully managed document database from AWS. A document database is a type of NoSQL database you can use to store and query rich documents in your application.
These types of databases work well for the following use cases: content management systems, profile management, and web and mobile applications.
### Amazon Keyspaces (for Apache Cassandra)
Amazon Keyspaces is a scalable, highly available, and managed Apache Cassandra compatible database service. Apache Cassandra is a popular option for high-scale applications that need top-tier performance.
### Amazon Neptune
Neptune is a fully managed graph database offered by AWS. A graph database is a good choice for highly connected data with a rich variety of relationships.
### Amazon Timestream
Timestream is a fast, scalable, and serverless time series database service for Internet of Things (IoT) and operational applications. It makes it easy to store and analyze trillions of events per day up to 1,000 times faster and for as little as one-tenth of the cost of relational databases.

## Amazon DynamoDB
With DynamoDB, you can do the following:

- Create database tables that can store and retrieve any amount of data and serve any level of request traffic. 
- Scale up or scale down your tables' throughput capacity without downtime or performance degradation. 
- Monitor resource usage and performance metrics using the AWS Management Console.
### DynamoDB core components
In DynamoDB, tables, items, and attributes are the core components that you work with. A table is a collection of items, and each item is a collection of attributes. DynamoDB uses primary keys to uniquely identify each item in a table and secondary indexes to provide more querying flexibility.
### DynamoDB Use cases
1. **Develop software applications**: Build internet-scale applications supporting user-content metadata and caches that require high concurrency and connections for millions of users and millions of requests per second.
2. **Create media metadata stores**: Scale throughput and concurrency for analysis of media and entertainment workloads, such as real-time video streaming and interactive content. Deliver lower latency with multi-Region replication across Regions.
3. **Scale gaming platforms**: Focus on driving innovation with no operational overhead. Build out your game platform with player data, session history, and leaderboards for millions of concurrent users.