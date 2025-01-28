* Simple Storage Service
* object storage service
* pay for what you store
* target storage for Kinesis and Elastic MapReduce
* used to store snapshots of RDS and EBS
* storage classes based on use cases: general purpose, infrequent access and archive
* Lifecycle policies can help migrate data to most appropriate storage class
#### Bucket
* container for objects
* top-level namespace and global
* bucket name must be unique across globe
* 63 lowercase letter,numbers,hyphens and periods
* 100 buckets per account by default
#### AWS Region
* each S3 bucket is stored in a region that we choose
* we can control the location of the bucket
#### Objects
* entities of files in S3
* from 0 bytes to 5TB
* each obj has data and metadata
* S3 doesn't care what type of data we store
* the data is treated as stream of bytes
* metadata is a set of name/value pairs describing the obj
* system metadata and user metadata
* SysMetadata created and used by Amazon (date modified, obj size, MD5 digest and HTTP Content-type)
* UserMetadata is custom and optional and can be specified only on time of creation (tags)
#### Keys
* uniqe identifier 
* almost like filename
* can be upto 1024 bytes of Unicode UTF-8 characters
* includes slashes, backslashes, dots, and dashes
* combination of bucket name, key (and version, optional) uniquely identifies an obj
* though S3 is a flat hierarchy S3 console will allow us to navigate through objects like files and folders.
#### S3 Operations:
* Create/delete buckets
* read/write/delete objects
* list keys in bucket
#### S3 API
* initially supported SOAP (still there but doesn't support new features)
* REST API is now in major use
#### Access Control
* Course grained AC- S3 Access Control List
* Fine grained- S3 bucket policy, IAM policy, query-string authentication
* ### REVISIT
#### Prefix and Delimiters
* S3 allows use of slash (/) and backslash (\) as delimiters
* this allows user to have a logically hierarchical folder-file system for ease of use
* but remember S3 is always a flat system without any hierarchy
#### Storage Classes
* Generally S3 Standard is used for general purpose
* ##### S3 Standard
	* General purpose
	* low latency high throughput
	* Standard Infrequent Access (Standard-IA) for long-lived less accessed data
	* low price for per GB-month
	* but minimum obj size 128KB, minimum duration 30 days, and per GB retrieval
* ##### Reduced Redundancy Storage
	* Low durability
	* used for derived data such as thumbnails
* ##### Glacier Storage [[Amazon Glacier]]
	* Low cost storage that doesn't require real time access
	* retrieval time of several hours
	* To retrieve an object from Glacier restore command is used
	* 3-5 hrs later the obj is copied to RRS
	* 5% of retrieval of data stored is free but other than that it incur fee
#### Object Lifecycle Management
* data generally moves from hot to warm and then cold based on how frequent it is accessed.
* S3 offers to automatically move the object to best suited storage class based on the custom policy we give
#### Encryption
* S3 encrypts data in flight by SSL (https)
* uses SSE (server side encryption) before writing it to disks
* ##### SSE-S3
	* managed by Amazon
	* each obj is encrypted by a key
	* each key is encrypted by a master key
	* master key is in a separate host machine
	* master key is rotated in a month
* ##### SSE-KMS
	* uses KMS service
	* gives log info of who used keys to access data and when
	* also gives info of who tried and failed attempt at getting data
* ##### SSE-C
	* Customer-managed service
	* keys will be maintained by the client
* ##### Client side encryption
	* the data is encrypted by the client before sent to S3
#### Versioning
* allows data to be versioned and protects against accidental deletion
* all versions of an obj can be retrieved
* once enabled versioning can't be disabled only temporarily suspended
* when a version of an obj is deleted it is marked as deleted rather than removing it from the physical memory
* meaning any version of the obj can be retrieved
* when an root obj(first version of the obj) is deleted then it is permanently removed from the bucket
#### MFA Delete
* enabled only by root account
* requires additional auth for an obj to be deleted permanently
#### Pre-signed URLs
* allows the object to be shared by generating an URL by using the security creds of the owner of the buckets
* limited for a time
#### Multipart upload
* allows objects to uploaded in chunks
* used for obj where initial size is unknown
* the upload can be paused and resumed when needed
* 3 steps: initiation, upload and completion
* Parts can be uploaded independently in arbitrary order, with retransmission if needed.
* S3 assembles the part to recreate the obj
* incomplete multipart uploads can be deleted by obj lifecycle management
#### Range Gets
* can be used to get only a portion of an obj
* specified in HTTP header or parameters if SDK
#### Cross region replication
* used to replicate objects from source bucket in one region to target bucket in another region
* versioning must be turned on in source and target buckets
* metadata and ACLs associated with the obj are also replicated
* any changes in data trigger a new replication to the target bucket
* must use IAM policy to give access to S3 to replicate objs 
* used to place data in multiple regions so that users can access it with low-latency
* if turned, only new objs will be replicated. To replicate old objs need to give separate command
#### Logging
* off by default can be enabled easily
* must choose a bucket to store logs can be the same bucket itself
* almost real time 
#### Event notification
* sent based on actions over objs in a bucket or when they are uploaded
* can trigger a workflow or simply a alert
* set at bucket level
#### Best practices, patterns and performance
* primary storage of DB can be in on-prem and the back is stored in S3 through internet
* using S3 to store bulk data and index in a separate service as  DynamoDB or RDS allowing quick queries and lookups
* To support higher request rates, it is best to ensure some level of random distribution of keys, for example by including a hash as a prefix to key names.
* Cloudfront can be used to cache get intensive bucket objs