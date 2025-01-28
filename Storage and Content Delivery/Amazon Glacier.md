* optimised for data archiving at low-cost
* "cold data" data that is rarely accessed
* retrieval time of 3-5 hrs
* extremely durable
#### Archives
* can contain 40TB data
* unlimited no.of archives
* unique archive id at the time of creation
* user-friendly names not allowed for archives unlike S3
* encrypted and immutable
#### Vaults
* containers for archives
* each account can have 1000 vaults
* control access through IAM and vault access policies
#### Vault Locks
* policy that enforces compliance for vaults
* specify controls such as Write Once Read Many (WORM) in policy and lock it
* once locked a policy can't be changed
#### Retrieval
* 5% of data stored can be retrieved each month for free
* anything above would incur cost
* can set policy that limits retrieval within free tier and maybe low cost
#### Difference between S3 and Glacier
* S3 obj 5TB, Glacier archives are upto 40TB
* S3 has user friendly custom keys, archives have system generated ID
* In S3 encryption is option, Glacier encrypts by default
* Make the best out of both by using Glacier as storage class for S3
