**Amazon DynamoDB**  
==DynamoDB is a fully managed NoSQL database that provides fast, consistent performance at any scale. It has a flexible billing model, tight integration with infrastructure as code (IaC), and a hands-off operational model. DynamoDB has become the database of choice for two categories of applications: high-scale applications and serverless applications. Although DynamoDB is the database of choice for high-scale and serverless applications, it can work for nearly all online transaction processing (OLTP) application workloads. We will explore DynamoDB more in the next lesson.== 

**Amazon ElastiCache**   
==ElastiCache is a fully managed, in-memory caching solution. It provides support for two open-source, in-memory cache engines: Redis and Memcached. You aren’t responsible for instance failovers, backups and restores, or software upgrades.==

**Amazon MemoryDB for Redis**  
==MemoryDB is a Redis-compatible, durable, in-memory database service that delivers ultra-fast performance. With MemoryDB, you can achieve microsecond read latency, single-digit millisecond write latency, high throughput, and Multi-AZ durability for modern applications, like those built with microservices architectures. You can use MemoryDB as a fully managed, primary database to build high-performance applications. You do not need to separately manage a cache, durable database, or the required underlying infrastructure.==

**Amazon DocumentDB (with MongoDB compatibility)**  
==Amazon DocumentDB is a fully managed document database from AWS. A document database is a type of NoSQL database you can use to store and query rich documents in your application. These types of databases work well for the following use cases: content management systems, profile management, and web and mobile applications. Amazon DocumentDB has API compatibility with MongoDB. This means you can use popular open-source libraries to interact with Amazon DocumentDB, or you can migrate existing databases to Amazon DocumentDB with minimal hassle.==

**Amazon Keyspaces (for Apache Cassandra)**  
==Amazon Keyspaces is a scalable, highly available, and managed Apache Cassandra compatible database service. Apache Cassandra is a popular option for high-scale applications that need top-tier performance. Amazon Keyspaces is a good option for high-volume applications with straightforward access patterns. With Amazon Keyspaces, you can run your Cassandra workloads on AWS using the same Cassandra Query Language (CQL) code, Apache 2.0 licensed drivers, and tools that you use today.==

**Amazon Neptune**  
==Neptune is a fully managed graph database offered by AWS. A graph database is a good choice for highly connected data with a rich variety of relationships. Companies often use graph databases for recommendation engines, fraud detection, and knowledge graphs.==

**Amazon Timestream**  
==Timestream is a fast, scalable, and serverless time series database service for Internet of Things (IoT) and operational applications. It makes it easy to store and analyze trillions of events per day up to 1,000 times faster and for as little as one-tenth of the cost of relational databases. Time series data is a sequence of data points recorded over a time interval. It is used for measuring events that change over time, such as stock prices over time or temperature measurements over time.==

**Amazon Quantum Ledger Database (Amazon QLDB)**  
==With traditional databases, you can overwrite or delete data, so developers use techniques, such as audit tables and audit trails to help track data lineage. These approaches can be difficult to scale and put the burden of ensuring that all data is recorded on the application developer. Amazon QLDB is a purpose-built ledger database that provides a complete and cryptographically verifiable history of all changes made to your application data.==

**Resources**  
For more information, see the following resource:

- AWS website: [AWS Cloud Databases](https://aws.amazon.com/products/databases/)