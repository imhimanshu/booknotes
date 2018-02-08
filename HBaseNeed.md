**HBASE: Need of Hbase**

Apache Hadoop used to store big data, managing and processing big data as it can handle a high volume of multi-structured data. Although Hadoop cannot handle high velocity of random read and write and also cannot change a file without completely 
rewriting it. 

HBase is a NoSQL, column-oriented database built on top of Hadoop to overcome the drawbacks of HDFS as it allows fast random 
writes and reads in an optimized way.Also, with exponentially growing data, relational databases cannot handle the variety of 
data to render better performance. HBase provides scalability and partitioning for efficient storage and retrieval.


HBase provide random access to high volume of structured or unstructured data.HBase provides real-time read or write access to data in HDFS. HBase can be referred to as a data store instead of a database as it misses out on some important features of traditional RDBMs like typed columns, triggers, advanced query languages and secondary indexes.

**HBase Data Model**
HBase data model stores semi-structured data having different data types, varying column size and field size. It provides data partitioning and distribution across the cluster. 

HBase data model consists of several logical components- row key, column family, table name, timestamp, etc. Row Key is used to uniquely identify the rows in HBase tables. Column families are static whereas column are dynamic by nature.

**HBase Tables** - Logical collection of rows stored in individual partitions known as Regions.
**HBase Row** - Instance of data in a table.
**RowKey** - Every entry in an HBase table is identified and indexed by a RowKey.
**Columns** - For every RowKey an unlimited number of attributes can be stored.
**Column Family** - Data in rows is grouped together as column families and all columns are stored together in a low level storage file known as HFile.

**Where to use HBase**:
- Data very dynamic and require real time access at same time ACID also important.
- perform read or write on subset of data efficiently, without having to scan through the complete dataset. 
- Data can grow horizontaly and verticaly

**HBase Architecture**:
HBase provides low-latency random reads and writes on top of HDFS. HBase, tables are dynamically distributed by the system whenever they become too large to handle (Auto Sharding). The simplest and foundational unit of horizontal scalability in HBase is a Region.

A continuous, sorted set of rows that are stored together is referred to as a region (subset of table data).  HBase architecture has a single HBase master node (HMaster) and several slaves i.e. region servers. Each region server (slave) serves a set of regions, and a region can be served only by a single region server. Whenever a client sends a write request, HMaster receives the request and forwards it to the corresponding region server.

**3 important components** - HMaster, Region Server and ZooKeeper.
**1. HMaster:** a lightweight process that assigns regions to region servers in the Hadoop cluster for load balancing.
    - Manages and Monitors the Hadoop Cluster
    - Performs Administration (Interface for creating, updating and deleting tables.)
    - Controlling the failover
    - DDL operations are handled by the HMaster
    - Whenever a client wants to change the schema and change any of the metadata operations, HMaster is responsible for all these operations.

**2. Region Server:** These are the worker nodes which handle read, write, update, and delete requests from clients. Region Server process, runs on every node in the hadoop cluster. Region Server runs on HDFS DataNode and consists of the following components –
    - Block Cache – This is the read cache. Most frequently read data is stored in the read cache and whenever the block cache is full, recently used data is evicted.
    - MemStore - This is the write cache and stores new data that is not yet written to the disk. Every column family in a region has a MemStore.
    - Write Ahead Log (WAL) is a file that stores new data that is not persisted to permanent storage.
    - HFile is the actual storage file that stores the rows as sorted key values on a disk.

**3. Zookeeper:** HBase uses ZooKeeper as a distributed coordination service for region assignments and to recover any region server crashes by loading them onto other region servers that are functioning. ZooKeeper is a centralized monitoring server that maintains configuration information and provides distributed synchronization. Whenever a client wants to communicate with regions, they have to approach Zookeeper first. HMaster and Region servers are registered with ZooKeeper service, client needs to access ZooKeeper quorum in order to connect with region servers and HMaster. In case of node failure within an HBase cluster, ZKquoram will trigger error messages and start repairing failed nodes.

ZooKeeper service keeps track of all the region servers that are there in an HBase cluster- tracking information about how many region servers are there and which region servers are holding which DataNode. HMaster contacts ZooKeeper to get the details of region servers. Various services that Zookeeper provides include 

    - Establishing client communication with region servers.
    - Tracking server failure and network partitions.
    - Maintain Configuration Information
    - Provides ephemeral nodes, which represent different region servers.



Reference:https://www.dezyre.com/article/overview-of-hbase-architecture-and-its-components/295
