* fastest way to get an app up and running on AWS
* reduces management complexities
* components  include environments, versions and configurations
* here an application is conceptually similar to folder
* application version is available
* application version points to S3 object that contains the deployable code
* can version can be deployed
* environment is the application version that is deployed onto AWS resources
* each environment runs a single application at a time
* Elastic BeanStalk provisions the resources needed
* environment configuration identifies a collection of parameters and settings that define how an environment associated with resource behaves
* supports java, node, php, python, ruby, GO
* 