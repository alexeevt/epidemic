# Notes on technologies
Timur Alexeev, 2018

## Terraform

Use: Write, plan, and create infrastructure as code (IaC)

### File System:
HDFS:
A distributed file system that protects from machine and network failure by storing large blocks of data redundantly. The Hadoop Distributed File System (HDFS) typically stores three copies of the blocks on a cluster of “worker” machines, with the meta-data that tracks the blocks maintained by a single “master” machine. HDFS is one of the most ubiquitous technologies, and works well as a source of truth for almost every other technology.

AWS S3:
A distributed file system that stores data persistently in machines maintained by Amazon Web Services. Amazon’s Simple Storage Service provides a durable, scalable, and reliably available solution for storing all types of data in AWS. S3 is a very popular alternative to HDFS that is compatible with most technologies and can circumvent the need to purchase machines for storage.
Terraform:
Terraform enables you to safely and predictably create, change, and improve infrastructure.
It is an open source tool that codifies APIs into declarative configuration files that can be shared amongst team members, treated as code, edited, reviewed, and versioned.

Azure Blob Storage:
Azure Blob Storage is a subset of Azure’s entire storage offering, optimized for general-purpose block-based and append operations. Data is stored in binary form (‘blobs’) and is designed to be efficient at moving around or operating on large volumes of data. Azure’s service is popular amongst businesses already on (or seeking to leverage other offerings of) the Microsoft stack and is becoming increasingly compatible with other Linux technologies.

GCP:
Google’s Cloud Storage Standard offers much the same basic features as does AWS S3: simple, durable storage. Cloud Storage Standard utilizes the familiar constructs such as buckets and objects as well as a variety of storage classes to support differing availability requirements. Adoption for this service is gaining as more companies are beginning to explore Google’s Cloud offering.

Alluxio:
Formerly known as Tachyon, Alluxio is a distributed file system that aims to provide a more storage-agnostic alternative to HDFS. Alluxio is fully compatible with Hadoop MapReduce and Spark code and achieves better performance by utilizing memory rather than disk. Following its 1.0 release in 2016, Alluxio has enjoyed increasing adoption at a number of high-profile companies across a variety of industries.

Ceph:
Ceph is an open source distributed storage system for objects, blocks, and files. Ceph is specifically designed to scale without a single point of failure and supports auto-healing. At this point Ceph is still fairly academic, but is has a few notable users such as Bloomberg, Cisco, and DreamHost.

#### Ingestion:
Ingestion is the process of collecting data from real-time and static sources. Many tools are available for ensuring that data can be collected reliably by a distributed cluster of machines, even when the machines or network are imperfect.

Kafka:
A flexible publisher-subscriber messaging system that allows multiple producers to pass large amounts of streaming data quickly and reliably to multiple consumers. Data is passed by a distributed cluster of "broker" machines that balance the load and store data durably to disk. For several years, Kafka has been one of the most popular ingestion tools for high-throughput systems and now touts its own lightweight stream processing library with Kafka Streams.
Kafka enables powerful ingestions: recently as much as 1 trillion messages a day.
All messages written to Kafka are persisted and replicated to peer brokers for fault tolerance.
Kafka can be very fast.
A high-throughput, low-latency distributed messaging system designed for hangling real time data feeds.

AWS Kinesis:
Amazon's managed service for collecting streaming data from a variety of sources and reliable passing it to multiple consumers in Amazon Web Services. Kinesis provides similar features as Kafka, but provides it as a fully managed and elastically scalable service. Kinesis has been a popular tool due to its integration with the AWS ecosystem and S3.

GCP Pub/Sub:
Google's real-time messaging service that allows users to push or pull data from practically any source or sink. Behind the scenes, Google guarantees messages are delivered "at least once" in a scalable manner. Pub/Sub provides similar features to Kafka and AWS Kinesis for Google Cloud Platform users.

Logstash:
A collection tool that can parse and enrich a variety of logs and pass them to longer term storage or search engines. Logstash uses customizable plug-ins that can transform and enrich data with features like location from IP addresses as it is collected. Logstash was made popular as the ‘L’ in the formerly named ELK stack (now known as the Elastic Stack).

RabbitMQ:
A ‘traditional’ message queue that now supports complex routing of streaming messages to different consumers, with flexible configurations that allow trade-offs between reliability and performance. Message delivery can be guaranteed using acknowledgments, except in the case of network partitions on distributed clusters. While RabbitMQ doesn’t provide the same throughput as Kafka, after 10 years in production at thousands of companies, it's a popular and reliable choice for smaller throughputs.

Fluentd:
A tool for unifying logs from multiple sources to a variety of consumers. Fluentd allows a cluster of machines to filter, buffer, and route a variety of data sources using hundreds of custom plug-ins. While it is not as general purpose as Kafka, Fluentd remains popular at many companies as one of the easiest log ingestion tools to learn and configure.

Sqoop:
A tool for bulk transfer of data between relational databases and Hadoop. Sqoop allows a cluster of machines to transfer data in parallel to HDFS or directly to tools like Hive, HBase, or Accumulo. Sqoop is one of the best tools for transitioning data from traditional databases like MySQL and Oracle.

ActiveMQ:
A more “traditional” message broker that offers a respectable feature set similar to RabbitMQ. ActiveMQ trades raw performance to enable support for protocols such as AMQP, MQTT, and more. While not the most performant or most feature rich tool, it has been called the swiss army knife of message queues for its all-around ability.

##### Batch Processing:
Batch processing is the general process of computing information from vast amounts of “bounded” data by using a distributed cluster of machines, typically over the course of several minutes or hours. The MapReduce paradigm for parallel programming has been the standard, but there are other alternatives developing.

Spark:
A general purpose computation framework that can process vast amounts of data in a distributed cluster of machines. Spark uses resilient distributed datasets (RDD), a paradigm that can perform MapReduce and iterative algorithms, optimized for in-memory computations. While Spark is written in Scala, it has support for Python and Java, as well as an interactive shell. Spark is quickly becoming one of the most popular batch processing technologies, with rapid development, adoption, and community support.
A fast general engine for distributed, large scale data processing.

Hadoop MapReduce:
A distributed computation framework that can process vast amounts of data using a cluster of machines. The MapReduce (MR) programming paradigm splits up input data to be processed in parallel in the map phase, then brings the resulting data back together in the reduce phase, shuffling it around the cluster if necessary. There are many high level abstractions like Pig, Hive, Cascading, and Scalding that run on top of Hadoop MR in a variety of languages. While Hadoop MapReduce is still a dominant framework, in many case’s it is quickly being eclipsed by Spark.

Presto:
A distributed system that runs SQL-like queries from an interactive command line interface (CLI). Presto can simultaneously use vast amounts of data from a variety of sources like HDFS or Cassandra, but uses in-memory processing rather than the MapReduce paradigm. Though Presto isn’t compatible with the entire Hadoop ecosystem, it remains popular for ad-hoc, interactive analysis and data exploration.

AWS EMR:
A general purpose computation framework that provides the functionality of Hadoop MapReduce and Spark in Amazon Web Services. Instead of purchasing machines or instances, Amazon’s Elastic MapReduce allows a pay-per-hour services for processing vast amounts of data. Though some of the features lag a few months behind other technologies, EMR is a popular, cost-effective alternative in the AWS ecosystem.

Hive:
A high-level abstraction of Hadoop MapReduce that provides a SQL-like language. Hive is compatible with many formats like Parquet, and is optimized for large batch jobs on immutable data rather than transactional updates and inserts. Since Hive is well-integrated with the Hadoop ecosystem and relatively easy to learn, it remains one of the most popular tools for processing large datasets.

Pig:
Pig is a platform that consists of a high-level language for creating MapReduce programs. It is built on Hadoop and provides ease of programming, optimization opportunities and extensibility by allowing UDFs in Java, Python and JavaScript. The language for this platform is called Pig Latin. Pig is well adopted in the Hadoop Ecosystem and has proven to speedup the development process.

Tez:
A general purpose framework for optimizing Hadoop MapReduce. Tez can simplify several sequential map and reduce phases into one directed acyclical graph (DAG) to streamline the computation. Tez is has been integrated into the popular Hadoop projects: Pig, Hive, and Cascading.

Cascading:
Cascading is a software abstraction layer for Apache Hadoop. It is used to create and execute complex data processing workflows on a Hadoop cluster using any JVM-based language (Java, JRuby, Clojure), hiding the underlying complexity of MapReduce jobs. While Cascading is popular in it’s own right, the Scala Library, Scalding, that sit’s on top of it, has been even more popular lately.

Giraph:
A graph processing tool for the Hadoop ecosystem. Giraph distributes graphs across machines and supports a wide array of applications including iterative algorithms where the state of the algorithm propagates through the graph. Giraph remains one the important graph processing tools since it is integrated with the Hadoop ecosystem and is popularly used at Facebook.

Spark GraphX:
A graph computation tool that uses Spark’s RDD framework. GraphX represents graphs as tables that can be distributed and processed in parallel across a cluster, and allows users to explore graphs interactively. While GraphX is a new project with fewer algorithms than GraphLab and Giraph, it is has better development features such as SQL integration.

###### Unified Processing
As the most recent generation of distributed computing frameworks have matured, they have have also begun to reimagine the data pipelines more fundamentally. In line with the paradigm shift of the Kappa architecture, many technologies are now take the view that batch processing problems are simply a subset of stream processing problem. These tools in particular have created abstraction for operators that can be run on batch and streaming data sets as well as the required underlying architecture.

Flink:
Flink is a general platform for scalable stream and batch processing that uses a streaming dataflow engine at its core and most closely matchs the Beam model specs. It implements memory management inside the JVM to guarantee efficient and robust switching between in-memory and out-of-core data processing. Flink has also graduated to a top level project in the ASF, and while adoption has been slow, it has seen steady growth and it continues to prove itself in industry.

Spark Structured Streaming:
A unified real-time and batch processing interface to Spark. Spark Structured Streaming enables developers to Spark SQL context to incrementally processing incoming data while retaining end-to-end exactly-once fault-tolerant guarantees. While still in Alpha release (as of Spark 2.1), with it's great feature set and simplified API, Structured Streaming appears to be a promising option.

GCP Dataflow:
Google Cloud Dataflow enables developers to write batch and streaming processes using a unified programming model. As a fully managed service, Dataflow also enables developers to not have to worry about scaling resources up or down, which is handled automatically. It touts compatibility with the Apache Beam SDK. Dataflow is a powerful and popular option for anyone utilizing other GCP offerings due to it's tight integration and ease of use.

Samza:
A stream processing framework that offers many of the same features are Storm. However, Samza has different ways of guaranteeing that messages are processed and stores the state of the computation locally. At this time, Samza lacks some of the features and adoption of other streaming tools, but is designed to seamlessly integrate with the increasingly popular Kafka.

Apex:
Offering a native streaming architecture, Apex is new framework that seeks to unify stream and batch processing with a rich feature set to boot. Apex applications are defined by a DAG composed of ‘streams’ and ‘operators’ which can support end-to-end exactly once semantics as well as many other ‘advanced’ stream processing features. While relatively new to the distributed processing game, Apex is already being used in production at the likes of GE and Capital One.

NiFi:
NiFi is a processing framework for controlling and tracking the real-time flow of data. NiFi is unique in that it uses a web interface for constructing its dataflow pathways and supports data governance for tracking the integrity of data. NiFi has graduated to a top level project in the Apache Software Foundation and it’s community of adopters is still growing diverse and quite diverse.

Gearpump:
Gearpump is an Apache incubator project which features a light-weight, high throughput, and robust streaming engine. Built on top of Akka, it offers error supervision, isolation and concurrency and also integrates with the Beam SDK. As early-stage project, it does not yet have a large user base, however, it's promising feature set makes it a technology to watch closely.

Onyx:
Onyx is a distributed stream processing engine that aims to leverage Clojure's feature set in the distributed environment. Touting pure functional operators, immutability, and a host of streaming primitives, it presents a very clean and attractive API. While still an early-stage project, Onyx has a number of features that make it appealing, particularly to Clojure developers.

####### Stream Processing:
Unlike batch processing, streaming technologies can process real-time data and events in milliseconds, allowing computations that would be too complicated with messaging queues alone. There are several solutions that support different levels of throughput and guarantees that the data processed, even when machines or the network fails.

Spark Streaming:
A real-time processing tool that processes streaming data using a similar framework as the core Spark engine. Spark Streaming breaks streams of data into small micro-batches and processes them in parallel on a cluster of machines. Spark Streaming is growing in popularity as new features are added and more companies adopt Spark for batch processing.

Storm:
A true real-time computation framework that can process vast amounts of streaming data quickly and reliably with a distributed cluster of machines. Storm uses an intuitive abstraction to process individual tuples of data, guaranteed by a novel acknowledgement algorithm and micro-batch support using the Trident abstraction. Storm provides a mature, documented, and production ready solution for streaming data.

Kafka Streams:
Kafka Streams is light-weight native streaming library for performing real-time analytics. Streams enables impressive features such as stateful streaming and windowing with out-of-order data. Given Kafka's existing widespread adoption, many companies are considering leveraging the newly expanded toolset that Kafka Streams and Kafka Connectors now offer.

Kinesis Streams:
Amazon's analogous offering to Kafka Streams; Kinesis Streams provides the ability to light weight analytics on being ingested through AWS Kinesis. In addition to support for complex event processing (defined by DAGs), Kinesis Streams also provide automatic scaling, load balancing, and routing to downstream AWS consumers. Kinesis Streams is a great option for those already leveraging Kinesis to handle ingestion on AWS or those who are just seeking a no-headache, light-weight stream processor.

AWS Lambda:
A fully managed real-time service available on Amazon Web Services. Lambda launches code within milliseconds of incoming events and only charges based on the small amounts of time used. Depending on the source of data, Lambda is capable of operating in native (or true) streaming mode or micro-batch. Lambda is a popular tool for those seeking a ‘no-ops’ experience that offers real-time, event based computations in AWS based systems.

Celery:
Celery is an easy to use, highly available, asynchronous task queue based on distributed message passing. Interestingly, Celery does not provide built-in message passing support but instead requires installion of a supported bus such as RabbitMQ or Redis. While not that widely-adopted, Celery is currently being used at scale in production at a few notable companies such as Instagram and AdRoll.

GCP Cloud Functions:
Notably limited to Javascript (as of now), Google's 'serverless' offering is capable of being triggered by database, HTTP, Pub/Sub events and more. Cloud Functions provides a low barrier to entry and no headache to setup a simple, elastic, data pipeline. As a relatively new service, early adopters have primarily been from engineering projects with less stringent requirements or teams lacking the resources to build and maintain their own infrastructure.

Heron:
Twitter’s successor to Storm that aims to be more performant at scale as well as easier to deploy and debug all while retaining backwards compatibility. Heron features a simplified processing architecture as well as an improved inter-process communication (IPC) layer. Beyond Twitter, Heron has been adopted at the likes of Microsoft and other organizations that have exceptionally low latency stream processing requirements.

######## Data Store
Once data has been processed by the streaming or batch computations, it needs to be stored in a way that can be quickly accessed by the end user or data scientist. While file systems are designed to store data durably, databases organize data in a way that minimizes unnecessary disk seeks and network transfers to provide the quickest response to queries. There are hundreds of options for databases and finding the correct one that organizes data correctly for a specific use case is one of the most important decisions for data engineers.

MySQL
A database for data that fits the relational model. Data is stored in a row-oriented way (when using the default InnoDB storage engine) and scaling is accomplished by sharding, which can be prohibitive depending on the use case. MySQL is the most popular relational database, especially for web applications.

AWS RedShift
A fully scalable database service with analytics in Amazon Web Services. Amazon’s Redshift stores data in a column-oriented manner that is optimized for analytics and connects well with traditional business intelligence (BI) tools. Given it’s simple integration with AWS tools S3, EMR, and most recently Spectrum, Redshift is one of the most popular databases for companies looking to perform offline analytics on large datasets.

Cassandra
A decentralized NoSQL database that remains available in the event of network partitions (AP in Brewer’s CAP theorem) by avoiding the use of a “master” node. Unlike Riak, Cassandra uses the BigTable data model, which can be thought of as keys that map to sorted key-value pairs, enabling a high volume of writes. Cassandra is one of the most popular highly-available databases that excels at time-series and multiple data centers.

Distributed, highly available database designed to handle large amouns of data across multiple data centers.
Casandra enbales backend storage for write-intensive applications.
Casandra also enables replication of query intensive applications.
Linearly scalable and enables easy cluster resizing.
Good at getting streaming data.
Not designed for batch data, so pre-aggregation of incoming data is needed.
Reliable storage for raw data is still needed.

Druid:
A column-oriented, real-time data store designed for business intelligence and online analytical processing (OLAP) queries. It is highly optimized for scanning billions of rows and performing interactive aggregations for analytical ad-hoc queries. It supports real-time simultaneous data ingestion making data readily available for querying as it arrives. It falls under the AP category of Brewer’s CAP theorem and is gaining popularity as an analytics data store.

Redis:
A key-value database optimized for data small enough to fit into memory. Redis uses very quick in-memory key retrieval and store values of structures like lists, sets, and hash tables. Redis is one of the most popular solutions for smaller datasets and while it does offer cluster support, it does not offer the strongest guarantees. Redis has rapidly become one of most popular cache’s in the open source space.

GCP BigQuery:
Google's managed service for analytical queries on petabytes of data, which guarantees results in a few seconds rather than the few minutes that you'd expect from batch systems. Internally, Google uses thousands and thousands of machines to parallelize queries using the Dremel framework, which inspired the open source projects, Drill and Parquet. BigQuery connects to many popular Business Intelligence and data visualization tools, and offers the same features as AWS Redshift, but with a "pay-by-the-query" pricing model instead of an hourly rate.

Oracle:
A object-relational model database that offers many of the same benefits as MySQL and PostgreSQL, but with an emphasis on stability and providing general features at the cost of additional complexity. Scaling requires a very sophisticated setup and maintenance, but Oracle RDBMS is still one of the most popular ‘enterprise’ relational databases.

PostgreSQL:
A database for data that fits the object-relational model. From the perspective of a data engineer, PostgreSQL has many of the same features and drawbacks as MySQL. It also supports Geospatial queries using the PostGIS plugin. Nonetheless, Postgres is still used in the industry for smaller datasets.

Elasticsearch:
A document oriented technology, optimized for searching text data. Elasticsearch stores schemaless data of any text based format and indexes it with a distributed cluster for quick searching later. Elasticsearch has eclipsed Solr as the most popular distributed text search engine.

AWS RDS:
A database service on AWS for managed instances of MySQL, Oracle, Postgres, and other popular relational databases. While RDS provides the same functionality of traditional relational systems, vertical scaling and maintenance is easier with Amazon. This provides a cost-effective and simple way to build operational databases, without having to learn new technologies.

######### Other technologies
Mesos:
Cluster resource management system that provides efficient resource insolation and sharing across distributed applications.
Fault tolerance and disaster recovery.

Akka:
A toolkit and runtime for building highly concurrent, distributed, and resilient message-driven applications on JVM.





