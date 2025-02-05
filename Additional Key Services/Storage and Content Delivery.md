### Cloudwatch
* global Content Delivery Network (CDN) service
* integrates with other AWS services gives low latency, high data transfer speeds
* globally distributed network of caching servers
* uses DNS geo-location to determine geographic location of each request and then they store the data in the closest edge caching servers and serve the next request from there
* increase scalability in response to peak traffic
* can work with AWS supported and non-AWS service like on-prem
* served over http or https
* supports media streaming using HTTP and RTMP
#### Basics
* 3 core concepts: distributions, origins and cache control
* ##### Distributions
	* start by creating a distribution identified by a DNS domain name
	* you can use this DNS domain name to serve file using cloudfront 
	* no need to change file paths 
	* can also create a user friendly domain name and make the cloudfront url a cname in the DNS record using Route 53 [[Route 53]]
* ##### Origins
	* the DNS domain name of the source(origin) must be specified
	* S3 bucket or HTTP server from which cloudwatch get the objects
	* ![[Screenshot 2025-01-30 at 3.41.49 PM.png]]
* ##### Cache Control
	* objects cached in edge locations stay there until expiration or evicted to make room for more frequently accessed data
	* by default objects expire from cache in 24 hrs
	* after the object is expired cloudfront forwards the request to origin to check if the object is unchanged or fetch a new version
	* we can control how long an object is cached by editing the Cache-Control headers set by origin server 
	* we can also set minimum, maximum and default TTL in cloudfront distribution
	* we can remove copies of an object from all edge locations at any time irrespective of the expiration time by calling `invalidation` API
	* only to be used in unexpected circumstances
	* best practice is to use version identifier as a part of the object path name
#### Dynamic Content, Multiple Origins and Cache Behaviours
* cloudfront can server dynamic content
* can use more than one origin server
* can control which requests are served by which origin
* and how requests are cached by using cache behaviours
* cache behaviour allows us to configure various functionalities for a given URL path pattern
* ![[Screenshot 2025-01-30 at 3.54.34 PM.png]]
* can serve private content by using signed urls, signed cookies and Origin Access Identities (OAI).
* OAI can restrict access to S3 buckets only to special Cloudfront users associated with your distribution 
* If all or most requests originate from a single location cloudfront wont be beneficial
* If all or most requests come through a corporate VPN cludfront won't be beneficial too because all request appear to come from a same location even though the users are in different places
#### AWS Storage Gateway
* connection from on-prem to cloud based storage to provide seamless and secure integration between the organisation's on-prem environment and AWS storage infrastructure
* industry standard storage protocols
* low-latency performance by cachin frequently accessed data on-premises
* AWS Storage Gateway is available as a VM to download
* the VM is installed on the host on-prem and registered with AWS account
* the storage associated is exposed as iSCSI device that can be mounted by the on-prem applications
* there are 3 configurations
* ##### Gateway-Cached Volumes
	* expand local storage capacity into S3
	* all data stored in Gateway-Cached Volume is moved to S3 
	* recently read data is retained on the local storage to provide low-latency access
	* each volume is limited to 32TB
	* single gateway can support 32 volumes for a max storage of 1PB
	* point-in-time snapshots can be taken to back up the gateway
	* snapshots are performed incrementally only data that is changed is stored
	* the data is transferred securely to S3 by SSL
	* encrypted at rest using server side encryption
	* these data can't be directly accessed from S3 API or S3 console
	* must be accessed from Gateway service
* ##### Gateway-Stored Volumes
	* store data on-prem ans asynchronously back up that data to S3
	* low-latency access and cloud backup
	* backed up in form of EBS snapshots
	* each volume limit is 16TB
	* single gateway can support 32 volumes for a max storage of 512TB
	* can take snapshots of Gateway-Stored volumes
	* snapshots stored as EBS snapshots in S3
	* encrypted in transit (SSL)
	* can't be accessed from S3 only from Gateway service
* ##### Gateway Virtual Tape Libraries (VTL)
	* archive in cloud
	* tape based backup application infrastructure
	* stores data on virtual tape cartridges
	* gateway can have 1500 tapes (1PB)
	* when our tape software ejects a tape it is archived on a Virtiual Tape Shelf(VTS) and stored in Glacier
	* 1 VTS per region
	* multiple gateways in a region can share a VTS
