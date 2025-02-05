* configuration management service that helps you to configure and operate application using chef
* supports linux and windows
* supports EC2 instances and servers in own data centers
* single configuration management service to deploy and operate applications across hybrid architectures
* a group of resources is called `stack`
* ![[Screenshot 2025-02-03 at 10.54.41 AM.png]]
* AWS OpsWork provides simple and flexible way to create and manage stacks and applications
* stack is the core AWS OpsWork component
* stack is basically a container for AWS resources that have common purpose
* defines some default configuration settings for the resources in the stack for example, OS in EC2
* each stack's permission can be configured to let users access the specific part of the stack
* one or more layers can be added to the stack
* layer is set of resources that serve a particular purpose
* AWS OpsWork key feature is a set of lifecycle events that automatically run on specified set of recipes on certain time
* OpsWorks sends all resource metrics to CloudWatch[[Amazon Cloudwatch]]
#### Use Cases
* host multi tier web apps
* support CI
