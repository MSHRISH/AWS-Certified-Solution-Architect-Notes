* provides AWS Resource inventory, configuration history and configuration change notifications
* discover existing and deleted AWS Resources
* generates configuration item for resources
* config item represents point-in-time view of various attributes of AWS resources
* config item is generated each time when a configuration of resource is modified
* historical record is maintained
* AWS config rule represents the desired configuration settings
* if the resources doesn't meet the config rules then a SNS notification is sent
* 