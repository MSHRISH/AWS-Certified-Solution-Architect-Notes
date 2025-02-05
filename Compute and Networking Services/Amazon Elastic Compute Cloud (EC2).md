* instances that can be spin up  and compute power can be used like a VM
* charged per hour of usage
* not charged when the instance is stopped
* two concepts are key to launch an instance: 
	* amount of virtual hardware dedicated (instance type)
	* the software loaded (AMI)
#### Instance Type:
* virtual hardware defining the instance
* lot of options
* parameters such as virtual CPUs (vCPUs), memory, storage, network performance
* grouped into families based of ratios of the parameters
* the `m4` instance type has balance of all parameters
* ![[Screenshot 2025-01-08 at 2.36.11 PM.png]]
* networking of an instance can be enhanced
#### Amazon Machine Images (AMIs)
* initial software on the system
* defines OS and its config, initial state of patches, applications or sys software
* based on x86, linux or windows
* 4 sources of AMIs:
	* published by Amazon
	* AWS Marketplace
	* Generated from existing instances
	* uploaded virtual servers
#### Securing an Instance
##### Addressing an Instance
* using DNS name assigned by Amazon automatically-persists only when the instance is running
* Public IP is assigned to instance and cannot be specified-unique in the internet-persists only when instance is running can't be transferred to another instance
* Elastic IP- unique IP on internet that is reserved in the internet-IP persists until customer releases it. Can be transferred to another instance when the primary has failed.
##### Initial Access
* Ec2 generates a random password for local admin account and encrypt the password with a public key
* the access is obtained by decrypting the password with a private key
* the decrypted password can be used to login via RDP
##### Virtual Firewall Protection
* Security Groups
* define traffic in and out 
* associated to instance when launching
* by default deny all
* stateful firewall i.e outgoing message can bring in the response through SG without explicit inbound rule
#### Lifecycle of Instance
* Launching
* Bootstrapping - running code while launching. passed through `UserData`. For updates, software installation and patches.
* VM Import/Export - VMs can be imported from on-prem. only imported EC2s can be exported.
* Instance Metadata - call to http://instanceIP/latest/meta-data/ will return top node metadata tree
* Tags can help manage multiple instances
* Instance can be monitored with Cloudwatch
#### Termination Protection
* Termination removes the instance from AWS infra
* termination protection can be enabled 
* prevent accidental deletion
#### Pricing
* charged for each hour the instance is running
* On- Demand Instances- least priced-for unpredictable workloads
* Reserved Instances- capacity reservations for predictable workloads. user reserves instances for a certain time (1yr-3yr) and will be charged less than on-demand.
* ![[Screenshot 2025-01-10 at 2.50.20 PM.png]]
* Spot Instances- uses spare EC2 capacity that is available for less price (than on-demand price). the hourly price for a spot instance is called spot price and set by Amazon EC2 and adjusted based on supply of and demand for Spot instances. preferable for interruptible workloads. Spot Instances run as long as the instance is available. the user is alerted if the Spot instance is about to be interrupted
#### Tenancy Options
* Shared Tenancy- default model. single host machine house instances from different customers. all instances are isolated.
* Dedicated Instances- hardware dedicated to a single customer.
* Dedicated Host- physical server with capacity to host EC2. allows you to use existing server-bound software licenses. ##REVISIT
#### Placement Groups
* logical grouping of EC2s in a single AZ
* enables low latency and high throughput communication
* to utilise fully use enhanced networking and 10Gbps network
	* Cluster-low-latency group in a single AZ
	* spread- spreads instances across underlying hardware (max 7 instances per AZ)
	* partition- spreads instances across many diff partitions-7 partitions per AZ-100s of EC2 instances in a partition-each partition is separated physically
	* 
#### Instance Store
* temp block storage for instances
* including within EC2 cost
