* service that helps to reliably process and move data between different AWS compute and storage services and also on-prem data sources
* regularly access data from storage and transform and process in scale
* efficiently transfer the result to AWS services such as S3, RDS, DynamoDB etc
* a pipeline schedules and runs tasks according to the definition
* pipeline interacts with data stored in data nodes
* data nodes are locations where pipeline reads input data (S3, Mysql DB, Redshift cluster)
* data nodes can be on AWS or on-prem
* pipelines execute activities such as moving data from one location to another, running HIVE queries
* activities will require additional resources such as EMR cluster[[Amazon Elastic MapReduce (Amazon EMR)]] and EC2 [[Amazon Elastic Compute Cloud (EC2)]] 
* AWS Data Pipeline will spin up these resources and will tear it down when activity is completed
* data flows often have dependencies. Data Pipeline supports preconditions, a set of conditional statements that must be true before an activity can be run
* conditions such as S3 key should be present, DynamoDB table has data
* if an activity fails retry is automatic
* can retry upto configured no.of tries
* can define the action in the event the activity reaches the fail limit
#### Use Cases
* virtually used for any batch mode ETL
* best for batch process. Use Kinesis[[Amazon Kinesis]] for data streams