### AWS Directory Service
* directories that contain info about organization, including users, groups, computers and other resources
* manages identity
* highly-available
* data replication and automated snapshots
* #### AWS Directory Service for Microsoft Active Directory (Enterprise Edition)
	* Microsoft AD hosted on AWS cloud
	* offers functionality offered by Microsoft AD and integrates with AWS 
	* set up trust relationships with existing AD domains to extend those directories to AWS cloud services
	* supports more than 5000 users and best for trust relationship set up between AWS-hosted directory and on-prem directory
* ##### Simple AD
	* Microsoft AD compatible directory from AWS that is powered by Samba 4
	* supports common functions such as user accounts, group memberships, domain-joining Amazon EC2 Instances running Linux and Microsoft Windows, SSO and group policies
	* can't setup trust relation between simple AD and other ADs
	* not supported features: MFA, Lightweight Directory Access Protocol (LDAP), Powershell AD cmdlets and transfer of Flexible Single-Master Operations (FSMO) roles
	* least expensive option, within 5000 users
* ##### AD Connector
	* proxy service to connect on-prem Microsoft AD to AWS cloud without complex directory sync or cost
	* forwards sign-in request to AD domain controllers for authentication and applications can query the directory for data
	* users can use their corporate credentials to log into AWS
	* MFA can be enables
	* we can manage AD on-prem as usual
	* best choice if we want to use our on-prem AD with AWS services
### AWS Key Management Service (KMS) and CloudHSM
* management of cryptographic keys within a crypto system
* generation, exchange, storage, use and replacement of keys
* CloudHSM: secure cryptographic key storage by Hardware Security Modules (HSMs) available on AWS Cloud
* uses envelope encryption
* ##### AWS KMS
	* create and control keys to encrypt data
	* keys never can't be exported from the service
	* only encrypt and decrypt based on policies
	* maintain control over who use your keys and gain access to encrypt the data
	* ##### Customer Managed Keys
		* Customer Master Key (CMK) to encrypt and decrypt the data
		* can be used to encrypt/decrypt 4KB of data directly
		* used to encrypt generated data keys that will be used to encrypt/decrypt large data outside the service
		* CMKs can never leave the KMS unencrypted but data keys can
	* ##### Data Keys
		* encrypt large data objects
		* when `GenerateDataKey` KMS returns plain text version of the key and ciphertext of key being encrypted by a specific CMK
		* KMS tracks which CMK was used to encrypt the data
		* use the plaintext key to encrypt and then store the encrypted key alongside the encrypted data
		* best practice is to remove the plaintext key as soon as the use is over
		* to decrypt the data pass the encrypted key to the function
		* KMS will use the CMK to decrypt the key and use it to decrypt the data
		* the decrypted key will be removed from memory
		* This is called Envelope Encryption
	* ##### Encryption Context
		* KMS accepts optional key/value map called `encryption context`
		* the context must be same for both encryption and decryption
		* context is logged and available as context in AWS policy language for fine-grained policy based authorization
* ##### AWS CloudHSM
	* helps meeting compliance and regulations for data security by using dedicated HSM appliances in AWS Cloud
	* HSM is hardware appliance provides secure key storage and cryptographic operations within a tamper-resistant hardware module
	* securely store cryptographic key material and use the key without exposing it outside the boundary of appliance
	* ##### Scalable Symmetric Key Distribution
		* symmetric encryption and decryption need same key 
		* the key must be sent from sender to receiver through a known secure channel or 3rd party process
	* ##### Government-Validated Cryptography
		* data protected with cryptography that has been validated by an outside party 
