* petabyte-scale data warehouse service
* RDS designed for OLAP and high-performance analysis
* fast querying over structured data 
* integrates with various data tools
* cluster can be snapshot and backed up automatically and manually
#### Clusters and Nodes
* a cluster is composed of leader node and more compute nodes
* client app interacts with leader node only
* 6 types of nodes, two categories: Dense Compute and Dense Storage
* Dense Compute 326TB using fast SSDs
* Dense Storage 2PB using magnetic disks
* disk storage for commute nodes is divided into slices (2 to 16 slices, varies based on node size of cluster)
* nodes perform parallel query execution
* increase query performance by adding more nodes to cluster
* a query is executed in parallel across all nodes
* we can set up a `distribution stratergy` to spread our data across nodes
* cluster size and node capacity can be modified. Redshift will create a new cluster and migrate the data 
#### Compression Encoding
* gives performance optimisations
* when data is loaded into empty table Redshift will automatically select the best compression scheme for each column
* it can also be specified when creating the table
#### Distribution Strategy
* how to distribute the records across nodes and slices
* configured to best meet the query patterns
* EVEN Distribution: default option, data distributed across all slices uniformly
* KEY distribution: rows are distributed according to the values in one column. leader node store matching values together to increase query performance in joins
* ALL distribution: full copy of entire table is distributed to all nodes. useful for lookup tables and large tables that are not updated frequently
#### Sort Keys
* define one or more column as sort keys
* enables efficient rang-restricted predicates
#### Loading Data
* similar to SQL has INSERT and UPDATE
* but for bulk writes COPY
* COPY command can load data into table the most efficient manner
* after each bulk loading VACCUM command must be run to reorganize data 
* ANALYZE command also recommended
#### Querying Data
* queried similar to SQL
* performance of cluster and queries can be monitored in CloudWatch
* Workload Management (WLM) allows to configure multiple queues and set priority to it