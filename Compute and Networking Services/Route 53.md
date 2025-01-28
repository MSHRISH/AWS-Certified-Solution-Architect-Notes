#### Domain Name System
* translates domain name to ip address
* hierarchical name structure, separated with (.)
* www.amazon.com here com is Top-Level Domain (TLD), amazon is Second-Level Domain(SLD), there can be any number of lower levels below SLD
* Route53 is an authoritative DNS system
#### Top-Level domains (TLDs)
* farthest part in the right
* .com, .net, .org
* Internet Corporation for Assigned Names and Numbers (ICANN) provides management authority to certain parties
* they can distribute domain names under TLD, through domain resgistar
* domain names are unique across internet
* each domain gets registered in a central DB called WhoIS
#### Hosts
* hosts refer to separate services accessible through a domain
* www.example.com www is the host
* api.example.com for APIs
* ftp.example.com for FTP
#### Sub-domains
* TLDs can have many subdomains under them
* left most portion of a domain are most specific
* most to least specific from left to right
#### Name Servers
* a computer that translates domain names to IP addresses
* sometimes point to other servers which will contain the IP
* can serve cached copies of data of other name servers
#### Zone files
* simple text file that contains mappings between domain names and IP addresses
* resides inside name servers
#### Domain Name Registrars
* ensure all the domain names are unique
* an org or a commercial entity
#### Records
* each zone file contains records
* mapping between resource and a name
#### Start of Authority Record
* mandatory in all zone files
* stores DNS server, zone admin, etc details
#### A and AAAA
* A record map to a IPv4 host
* AAAA record map to a IPv6 host
#### Canonical Name (CNAME)
* alias for the CNAME of the server
#### Mail Exchange (MX)
* define mail servers
#### Pointer (PTR)
* reverse of A record
* maps an IP to DNS name
#### Route 53 Overview
* domain registration
* DNS Service
* Health checking the resources
#### Routing Policy
* Simple
* Weighted
* Latency-based
* Failover
* Geolocation

