* handles massive streaming data
* easy to load and analyze streaming data
* build custom streaming data applications 
* consists of 3 services:
	* Amazon Kinesis Firehose: load massive volumes of streaming data into AWS
	* Amazon Kinesis Streams: build custom applications for more complex analysis of streaming data in real time
	* Amazon Kinesis Analytics: analyze streaming data in real time with standard SQL
* handle virtually limitless data streams
* ideally suitable for ingestion and processing streams of data
* less appropriate for ETL processes (use AWS Data Pipeline [[AWS Data Pipeline]]
* retention period of 365 days
* data can't be deleted by consumers
* Kinesis Producer Library (KPL) to write. optimized producer apps
* Kinesis Client Library (KCL) to write optimized consumer apps
#### Kinesis Data Streams - Capacity Modes
* Provisioned Mode:
	* choose no.of shards
	* each shard gets 1 MB/S (1000 records per second)
	* each shard gets 2MB/S out
	* scale manually
	* pay per shard provisioned per hour
* On-demand Mode:
	* no provisioning
	* default capacity 4MB/S (4000 records per second)
	* scale automatically
	* pay per stream per hour and data In/Out per GB
#### Amazon Kinesis Firehose
* receives stream data and stores it in S3, Redshift or Elasticsearch
* no code, jus create delivery stream and configure the destination
* clients write data to the stream using AWS API and the data is sent to the destination
* ![[Screenshot 2025-02-03 at 9.52.46 AM.png]]
* if the configured destination is S3 the data is directly sent t it
* if the configured destination is Redshift then the data is first sent to S3 and then Redshift `COPY` command is used to load data into Redshift
* destination can be Elasticsearch with the backup option as S3
#### Amazon Kinesis Streams
* collect and process large streams of data records in real time
* AWS SDKs can be used to create `Amazon Kinesis Streams` applications that process data as it moves through the stream
* processing is typically lightweight and the response time for data intake and processing is near real time
* scale to support limitless data streams by distributing incoming data to multiple shards
* the processing is done on the consumers side, which read data from the shards and run the Streams application
* ![[Screenshot 2025-02-03 at 9.58.57 AM.png]]
#### Amazon Kinesis Analytics


#### Use Cases
* Data ingestion (Firehose)
* Real time processing massive data streams