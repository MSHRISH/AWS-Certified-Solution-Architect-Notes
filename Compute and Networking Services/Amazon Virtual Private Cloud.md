* own private cloud virtual network with lot of customisations
* the VPC CIDR range can't be changed after creation
#### Subnet
* segment of a VPC
* their CIDRS should not overlap with each other
* one subnet lies only in one AZ
* can add one or more subnets in each AZ
* public, private and VPN only
* public subnet redirects traffic to IGW
* private subnet doesn't directly redirect traffic to IGW
* VPN Subnet redirects the traffic to VPC VPG (Virtual Private Gateway) and doesn't have a route to IGW
* Default Amazon VPC contains one public subnet in every AZ within region, with net mask of /20
#### Route Tables
* rules to determine network traffic routing
* each RT has default local route for internal routing-can't be modified or deleted
#### Internet Gateways
* communication with internet to VPC-horizontally scalable
* network address translation for instances with public IP
#### Dynamic Host Configuration Protocol (DHCP)
* #### REVIST
#### Elastic IP Address (EIPS)
* static public IP
* Amazon holds a pool of public IPs in each region
* they are region specific i.e EIP in one region can't be assigned to another region instance
* one-to-one relationship between network interfaces and EIPS
* charges are even EIPS is not assigned to a instance
#### Elastic Network Interfaces (ENIs)
* virtual network interface that can be attached to an instance in VPC
* can have one public IP and multiple private IPs
* dual-homed instances
#### Endpoints
* private connection between VPC and other AWS Services without internet
* currently support communication with S3
#### Peering
* connection between two VPCs
* peer owned VPCs or with VPC in others accounts within region
* VPCs with matching CIDRs or overlapping CIDR blocks cannot be peered
* can't create peering to VPC in diff region
* do not support transitive routing
* ![[Screenshot 2025-01-16 at 4.11.35 PM.png]]
* two VPCs can have only one Peering connection between them
#### Security Groups
* virtual stateful firewall
* default security group denies all inbound, allows all outbound and allows communication between all resources
* 500 Sec-groups per VPC
* 50 inbound and 50 outbound rules to each sec-group
* can specify allow rules but not deny rules (imp diff between ACLs and Sec-group)
* they are stateful i.e allowed inbound can be allowed to flow outbound and viceversa (another diff between ACL and Sec-group)
#### Network Access Control List (ACLs)
* stateless firewall
* numbered list of rules that AWS evaluates in order, starting with lowest number
* associated with subnet level
* by default all subnets have ACLs allowing all inbound and outbound
* support allow and deny rules
* ![[Screenshot 2025-01-16 at 4.25.02 PM.png]]
#### Network Address Translation (NAT) Instance and NAT Gateways
* allow instances deployed in private subnets access to internet
* NAT gateway is better than NAT instances
* ##### NAT Instances
	* instances with Amazon-linux AMI
	* takes traffic from private subnet and translates the source IP to public IP of NAT instance and forward the traffic to internet
	* maintains the state of the forwarded request to return the response to the source instance
	* have `amzn-ami-vpc-nat` in their names
* ##### NAT Gateways
	* similar to NAT instances but much simpler to manage and highly available within AZ
#### Virtual Private Gateways (VPGs), Customer Gateways (CGWs) and Virtual Private Network (VPNs)
* #### REVISIT
