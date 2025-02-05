* fully managed, on demand Hadoop framework
* spin up large Hadoop clusters instantly
* options:
	* instance type of cluster nodes
	* no.of nodes in the cluster
	* version Hadoop 
	* additional tools like Hive, Pig, Spark or Pesto
#### Hadoop Distributed File System (HDFS)
* standard file system that comes with Hadoop
* all data is replicated across multiple instances to ensure durability
* can use EC2 instance storage and EBS for HDFS
* when a cluster is shut down, instance storage is lost and data doesn't persist
* with EBS storage HDFS can trade in the cost effectiveness of instance storage for data persistance
#### EMR File System (EMRFS)
* implementation of HDFS that allows clusters to store data in S3
* durable and low cost
* no data loss on cluster shutdown
#### What to select?
* key factor to look for is whether the cluster is persistent or transient
* persistent cluster runs 24x7
* so it is appropriate to use HDFS with instance storage for low latency, when there is constant operation there is no data lost when the cluster is shut down
* bid data workloads are inconsistent and it is cost effective to turn off the clusters when not in use
* these are called transient clusters
* EMRFS is best suited
* combination of EMRFS and HDFS is also possible
#### Use Cases
* process logs
* clickstream analysis
* genomic and life sciences
* 