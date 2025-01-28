* balance traffic among multiple EC2 instances
* can manage instances in one or multiple AZs
* offers routing, HTTP, HTTPS, SSL
* provides a stable CNAME and DNS easy to access
* supports internet facing and internal traffic
* scales properly and high availability
#### Internet-Facing Load Balancers
* manages traffic between Ec2s and internet
* can be accessed by clients with a DNS name
* always recommended to address the ELB by DNS name instead of it's public IP
* since it is elastic and scales accordingly it is bad practice to reference public IP in applications since the IP maybe changed
* ELB in VPC supports IPv4 only
* ELB in EC2 supports IPv6 too
#### Internal Load Balancers
* route traffic within VPCs
#### HTTPS  Load Balancers
* uses SSL/Transportation Layer Security for encrypted connections
* have security policies that have predefined SSL negotiating configurations
* must install SSL cert on the Load Balancer
* #### REVISIT
#### Listeners
* every load balancers must have a listener configured
* process that checks for a connection request
* configured with a protocol and a port (Client to LB and LB to EC2s)
* supports HTTP, HTTPS, TCP, SSL
* in OSI model, layer 4 (transport layer) describes TCP connection between client and back-end instance through load balancer
* layer 4 is the lowest configurable layer
* layer 7 (application layer) describes use of HTTP and HTTPS from clients to LB and from LB to back-end isntances
#### Configuring ELB
* ##### Idle Connection Timeout
	* for every request LB maintains two connections-one from client to LB and one from LB to back-end isntances
	* idle timeout is triggered when no data is sent through the connection
	* default is 60seconds
	* closes the connection if timeout is triggered even if the data is still being transferred
	* `keep-alive` option is recommended to use in web-server. allows LB to reuse connections to back-end instance, reduces CPU util.
	* ##### REVISIT
* ##### Cross-Zone Load Balancing
	* ensures even traffic distribution and high availability
	* if client caches the DNS then the LB will favour one AZ
	* cross-zone load balancing ensures the load is spread evenly through all AZs
* ##### Connection Draining
	* can be enabled to stop sending request to unhealthy or deregistered instances
	* can specify max-timeout before closing a unhealthy connection (between 1 sec to 3600 sec.default 300 sec)
* ##### Proxy Protocol
	* #### REVISIT
* ##### Sticky Sessions
	* a feature that allows to bind a client session to an instance
	* ELB creates cookie named AWSELB which is used to map the session to the instance
* ##### Health Checks
	* status of EC2s
	* healthy instances means `InService`
	* unhealthy instance means `OutOfService`
	* health check is a ping sent out periodically by the LB