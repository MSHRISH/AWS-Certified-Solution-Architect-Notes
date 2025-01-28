* Amazon RDS doesn't provide shell access to the DB
* supports multiple engines, manages infra and automates lot
#### Database Instance
* isolated DB environment deployed in private network
* can run a DB engine such as mysql, postgresql, mariaDB, Amazon Aurora etc.
* DB Parameter and DB option group???
#### DB Engines
* MySQL
* PostgreSQL
* MariaDB
* Oracle
* MS SQL Server
* Amazon Aurora
#### Amazon Aurora
* enterprise-grade commercial database tech
* 5x than MySQL
* applications can use existing MySQL DBs with Aurora
* It is a DB cluster with one or more instances and a cluster volume
* cluster volume is a virtual DB storage that spans multiple AZs, each AZ has copy of the cluster data
* Primary Instance: supports read and write-each cluster has one primary instance
* Replica Instance: only read ops-each cluster can have upto 15 replicas-distributed read workload and increase in performance
#### Storage Options
* RDS built using EBS
* Magnetic: standard storage-cost-effective-light I/O applications
* General Purpose (SSD): called gp2-faster than magnetic-burst performance to meet the spikes
* Provisioned IOPS (SSD): I/O Intensive workloads
#### Backup and Recovery
* automated backups and manual snapshots
* RPO- Recovery Point Objective (Max period of dataloss that is acceptable)
* RTO- Recovery Time Objective (max amount of downtime)
* Automated backups creates a storage volume snapshot of DB Instance
* not just individual databases but the DB instance as a whole is backed up
* by default backups are retained for 1 day (can be changed till 35days)
* when DB Instance is deleted all automated backups are deleted
* manual snapshots are retained though
* automated backups occur daily in a custom 30-min window
#### High Availability with Multi-AZ
* allows a secondary copy of the DB in another AZ
* primary and secondary instances are in sync continuously
* each AZ has its physically distinct, independent infra which is highly reliable
* automatically fail over to the standby instance
* same DNS but CNAME points to the standby
#### Security
* use IAM to enforce what actions users can perform
* best practice is to deploy DBInstances in private subnets
* have a DB subnet group (which is private) in which the instances can be deployed
* restrict network access using ACLs
* create users at database level with strong passwords and rotate regularly
* encrypt at transit and rest
