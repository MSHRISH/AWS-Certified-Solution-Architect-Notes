* Elastic Cache allows to deploys and manage cache environments running either Memcached or Redis
* distributed in-memory caching environment
* automatically detect and recover from a failure of a cache node
#### Cache Engines
* ##### Memcached
	* simple interface allows to read and write into in memory key/value data stores
	* elastically grow and shrink a cluster
	* cluster can be partitioned into shards and support parallelised operations
* ##### Redis
	* write/read in-memory data onto disk
	* create snapshots and data can be recovered
	* support 5 read replicas to offload requests
	* read replica can be promoted and become new master incase of failure
	* advance features make it easy to sort and rank data
#### Nodes and Clusters
* each deployment consists of one or more nodes in a cluster
* Memcached cluster can contain upto 20 nodes
* redis clusters have only single node, but multiple clusters can be grouped into a Redis Replication Group
* t2 cache node family optimal for low-volume apps
* for Memcached clusters it is likely to use high number of small nodes rather than small number of higher capacity nodes. This will reduce the impact of failure
#### Memcached Auto Discovery
* simplifies the application code by no longer needing awareness of the infrastructure topology of the cache cluster
* available for .NET, Java and PHP
* gives ability of identify automatically all of the nodes in a cache cluster and maintain connections
#### Horizontal Scaling
* Memcached can scale horizontally by partitioning the data into 20 nodes or more
* with Auto Discovery the application can connect with all nodes
* Redis has only one node, so additional clusters can be created and grouped into a Redis replication group
* One node can handle write commands and up to 5 nodes can be read replicas handling only read-request
#### Vertical Scaling
* can't change node size and type directly
* create a new cluster and start redirecting requests here
* Memcached clusters start empty but Redis cluster can be initialised from a backup
#### Replication
* Memcached are standalone without any redundant data protection services
* Redis support replication groups
* a Multi-AZ replication group increases availability and minimize loss of data
* in the event of failure the replication node will becom primary node and DNS of the new primary node will be updated
#### Backup and Recovery
* Redis cluster allow to create snapshots and store in disk
* snapshots can't be created for Memcached and they always start empty
* Redis backup file gets stored in S3
* snapshot can have a performance impact on heavily used clusters
* best practice is to set replication group and take snapshot of the one of replicas
* automatic snapshots are also allowed in a time window
