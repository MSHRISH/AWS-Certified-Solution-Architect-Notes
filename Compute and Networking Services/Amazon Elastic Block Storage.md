* Persistent block level storage
* replicates automatically to recover from failures or data loss
* one volume can be attached to one instance at a time
#### Types

* Magnetic Volumes: lowest performance-low cost-1GB to 1TB-avg 100 IOPS-best for infrequent access-billed for space provisioned regardless of how much data is stored
* General-Purpose SSD: strong performance-moderate price-wide range of workloads-1GB to 16TB-3 IOPS per GB provisioned-capping 10,000 IOPS-baseline performance for 1TB is 3000 IOPS-won't got above the 10K cap
* Provisioned IOPS SSD: I/O intensive workloads-DB workloads-most expensive-high performance-4GB to 16TB-can select desired IOPS-max of 30 times or 20K
#### Amazon EBS-Optimized Instance
* to ensure EC2 is ready to take advantage of the I/O of the EBS
* additional charges
#### Protecting the Data
* Snapshots: incremental backups-only the blocks that have changes are saved-stored using S3 tech-but managed by AWS-controlled storage-constrained to region-new volume can be created from the snapshot
* Encryption: uses AWS KMS-AES-256-minimal effect on latency

