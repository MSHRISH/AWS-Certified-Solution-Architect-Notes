* accelerates the transfer of large amount of data into and out of AWS using physical storage appliances, bypassing the internet.
* data is copied to a device at the source, shipped via standard shipping mechanism and then copied to the destination
#### Amazon Snowball
* a literal physical device
* protected by KMS[[Security]] 
* two sizes: 50TB and 80TBs
* import and export data between on-prem and AWS S3
* encryption is enforces 
* manage the jobs through AWS console
* ![[Screenshot 2025-02-03 at 10.39.33 AM.png]]
#### AWS Import/Export Disk
* transfer data directly onto and off of storage devices using Amazon high-speed internal network
* import into S3, EBS and Glacier
* export data from S3
* encryption is optional not enforced
* upper limit of 16TB
* can't manage jobs from console
#### Use Cases
* storage migration
* migrating applications
