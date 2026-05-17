Assignment 2 - Database Selection Framework

Problem Statement: For each category below, compare the options, explain when you would pick one over the other, and justify your choice with a real-world scenario:

1. Relational Databases - compare available options, when would you pick one over another and why?
2. NoSQL Databases - compare available options, what is the fundamental difference in data patterns between them?
3. Cloud Data Warehouses - compare available options, what are the pricing and architectural differences that drive your choice?
4. In-Memory Databases - compare available options, what completely different problems do they solve?
5. Object Storage - compare available options, when does vendor lock-in become a real concern?

Solution:

Relational Databases:
Relational databases store data in tables with rows and columns and use SQL for querying. They are best when data has relationships, consistency is important, and transactions must be reliable.

1.	MySQL: Beginner Friendly
You are a beginner, Building small-to-medium web applications.  Need simple setup and fast development and budget is limited.

2.	PostgreSQL: Complex Queries, High Reliability
You need complex queries and analytics. Data integrity is very important. Working on large  scalable applications. You need JSON support along with relational features.
A fintech company handling financial transactions selects PostgreSQL because of strong ACID compliance, reliability, and advanced SQL capabilities.

3.	Oracle Database: Enterprise Security, Large Enterprises, High Reliability
 Security and high availability are critical. Large enterprise systems are involved. Handling massive real-time workloads.
A national bank uses Oracle Database for secure transaction processing and disaster recovery.

4.	SQL Server: Best GUI Tools
Your organization already uses Microsoft technologies. You need strong reporting and business intelligence tools. You prefer GUI-based administration.
A corporate company using Windows servers and Power BI chooses Microsoft SQL Server for seamless integration.

5.	SQLite: Lightweight Projects, Beginner Friendly
Building mobile apps or embedded systems. Need a local lightweight database. No dedicated database server is required.
An Android offline notes application stores user data locally using SQLite

For relational databases, I would choose MySQL for learning, small projects, and simple websites because it is easy and beginner-friendly. For bigger and more complex projects, I would choose PostgreSQL because it is more powerful and reliable. Large companies may use Oracle Database for security and large-scale systems.




NoSQL Databases:
NoSQL databases are designed for flexible, large-scale, and unstructured data.

1.	MongoDB: JSON documents
Data structure changes frequently. JSON data is heavily used. Fast development is needed.

2.	Redis: Key-Value
Unlike traditional databases that store data mainly on disk, Redis stores data in RAM, making it extremely fast. 
Ultra-low latency is needed. Frequent reads/writes happen. Temporary data is stored.Real-time analytics are needed. But RAM is Expensive.
Instagram or YouTube cache popular posts/videos in Redis.

3.	Apache Cassandra: Column-family
Cassandra is a distributed NoSQL column-family database. It can handle billions of records across many servers without a single point of failure.
Massive scalability is needed. System downtime is unacceptable. High-speed writes occur continuously. Data is globally distributed
Ex. Netflix

4.	Neo4j: Graph
Neo4j is a graph database designed to manage Relationships, Connections and Networks,
Neo4j stores: Nodes, Relationships,Properties
Neo4j focuses on: Connections between data
Relationships are central, Network analysis is important, Recommendation systems are needed, Fraud detection is required
Ex. Facebook-like friend connections.

I would choose MongoDB for flexible applications because it is easy to work with JSON data. For fast caching and real-time speed, I would use Redis. For huge systems with lots of data, companies can use Apache Cassandra. For apps based on connections like social media, Neo4j is better.




Cloud Data Warehouses:
Cloud Data Warehouses are designed for
Big data analytics, Business intelligence (BI), Reporting, Machine learning analytics, Data engineering pipelines.

1.	Snowflake:
Storage and compute scale independently. Multiple teams can run workloads separately without affecting each other. 
Snowflake uses: Virtual warehouses, Decoupled architecture, Multi-cluster compute 
Choose Snowflake when: Teams share one data platform. Workloads change frequently. Multi-cloud support is needed. Ease of management matters.
Pay-per-compute credits. Flexible enterprise workloads

2.	BigQuery:
No infrastructure management, No clusters to maintain, Google handles scaling automatically.This makes it very beginner-friendly.
Choose BigQuery when:
Minimal administration is preferred. Teams mainly run analytics queries. Google Cloud ecosystem is already used. Data engineers are limited
charged based on: Amount of data scanned and Storage used

3.	Azure Synapse Analytics:
Synapse combines: Data warehousing, Big data analytics, Spark integration,Microsoft BI tools
Choose Synapse when: Company uses Microsoft ecosystem. Power BI integration is important. Enterprise governance is required.

4.	Databricks:
Databricks is based on: Lakehouse Architecture
It combines: Data lake, Data warehouse, Machine learning platform 
Built on Apache Spark.
Choose Databricks when: AI/ML workloads are important. Data engineering pipelines are large. Both structured and unstructured data exist.

When Would You Choose Which?

Situation           	  Best Choice
Beginner-Friendly   	  BigQuery
Multi-Cloud Flexibility	  Snowflake
AWS-Centric Company	      Redshift
Microsoft Enterprise	  Synapse
AI + ML Heavy Workloads	  Databricks

I would choose Google BigQuery because it is simple and serverless. If better scaling and flexibility are needed, I would choose Snowflake. Companies already using AWS may choose Amazon Redshift.




In-Memory Databases:
An in-memory database stores data primarily in RAM instead of traditional disk storage.
Because RAM is much faster than HDDs or SSDs: Data access becomes extremely fast,Latency reduces significantly,Real-time processing becomes possible.
These databases are designed for applications where: Millisecond or microsecond response time matters and Huge numbers of requests happen simultaneously.

In-memory databases store data in RAM instead of disk, making them extremely fast for real-time applications. Different databases solve different problems. Redis is mainly used for caching, sessions, and real-time apps to improve speed. Memcached is a simple caching tool that reduces database load. SAP HANA is used for real-time enterprise analytics and business reporting. Hazelcast and Apache Ignite are used for distributed computing and large-scale data processing, while Aerospike is designed for massive high-speed transactions.

Comparison of In-Memory Databases

Database    	Main Strength	      Best Problem Solved
Redis	        Ultra-fast cache      Real-time applications
Memcached	    Lightweight cache	  Simple caching
SAP HANA	    Real-time analytics	  Enterprise analytics
Hazelcast	    Distributed memory	  Clustered applications
Apache Ignite	Distributed compute	  Real-time computation
Aerospike	    Massive transactions  Ultra-scale systems
		
I would choose Redis because it is very fast and useful for caching and real-time apps. For simple caching only, Memcached is enough. Big companies needing live analytics may use SAP HANA.




Object Storage:
Object storage is used to store large amounts of unstructured data such as images, videos, backups, logs, documents, and data lake files. Popular object storage options include Amazon S3, Google Cloud Storage, Azure Blob Storage, and MinIO.

1. Amazon S3 
•	Most popular object storage service 
•	Highly scalable and reliable 
•	Best for AWS ecosystem users 
•	Used for backups, media files, and data lakes 

2.  Google Cloud Storage 
•	Strong integration with Google analytics and AI tools 
•	Good for big data and machine learning workloads 
•	Best for Google Cloud users 
•	
3. Azure Blob Storage 
•	Best for Microsoft Azure ecosystem 
•	Commonly used in enterprises using Windows and Azure services 
•	Good integration with Microsoft tools 

4. MinIO 
•	Open-source and S3-compatible 
•	Can run on private servers or any cloud 
•	Best for avoiding vendor dependency and improving portability

I would choose Amazon S3 because it is popular and reliable. If the company uses Google Cloud or Azure, then Google Cloud Storage or Azure Blob Storage are good choices. To avoid depending on one company, I would choose MinIO.



