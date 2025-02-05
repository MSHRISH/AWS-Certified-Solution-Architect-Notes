#### Principals
* IAM Entity that is allowed to interact with resources
* RootUser, IAM User and roles/temp tokens
#### Root User
* full privileges, can close the acct
* best practice is just use Root User to create users
#### IAM User
* represent individual people
* can be created with principals with administrative privileges
* users are persistent i.e no expiration time
* allow only least privileges to users
#### Roles/Temporary Security Tokens
* to grant specific privileges to specific actors for a certain duration
* the actors can be authenticated by AWS or some trusted external systems
* AWS provides the actor a temporary security token from AWS Security Token Service (STS)
* range of temp tokens lifetime is 15mins to 36hrs
* Main use cases are :
* ##### Amazon EC2 Roles
	* can be helpful when we have application that need to access other AWS services running in EC2
	* IAM role can be a safer option
* ##### Cross-Account Access
	* give access to IAM users of another account to resources
* ##### Federation
	* organizations can facilitate with AWS to leverage their identity repository to create IAM Users
	* similar to Google login
	* IAM can integrate with two diff types of IdP (identity provider)
	* for web identities such as Facebook, Google or Amazon it supports OpenID Connect (OIDC)
	* for internal identities such as AD or LDAP, IAM supports integration via Security Assertion Markup Language 2.0 (SAML)
	* federation works by returning a temporary token associated with a role to the IdP
#### Permission Boundary
* A permissions boundary can be used to control the maximum permissions employees can grant to the IAM principals (that is, users and roles) that they create and manage.
* 
#### Authentication
* User name/password- mostly for human interactions
* access keys- combination of access key ID (20 charcters) and access secret key (40 charcters). Used to make API calls to access the AWS
* Session Token- calls to AWS must contain both access and session tokens
#### Authorization
* process of specifying exactly what actions a principal can or cannot do is `authorization`
* handled by IAM by specific privileges in policies and associating them with principals
#### Policies
* JSON doc that defines set of permission to access AWS resource
* can contain one or more permissions
* each permission contains:
	* Effect- single word (Allow or Deny)
	* Service- the service in AWS the permission applies to
	* Resource-specific ARN (Amazon Resource Name) for which this permission applies
	* Action- subset of actions that the permission allows or denies
	* condition- defines one or more optional restrictions
#### Associating Policies with Principals
* User Policy- exist only in context of the user to which they are attached. Created on IAM User page.
* Managed Policies- created in Policies tab on IAM page. exist independently of any individual user. can be assigned with many users or groups. there are predefined managed policies. custom policies can also be created
* User Groups- any policy attached to a Group will be inherited to the users part of the group
* an actor (IAM User or a person or process authenticated by a trusted service outside the AWS) can be associated to a policy by assuming a role
#### Multi-Factor Authentication (MFA)
* MFA can be assigned to any IAM user account
* added protection
#### Rotating Keys
* access keys are rotated in a regular basis
