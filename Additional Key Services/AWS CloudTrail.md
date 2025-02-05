* Captures AWS API calls and related events made by or on behalf of an AWS account
* delivers log files to S3
* can be configured to send SNS when log files reach S3
* two types of trails
* ##### All region Trail
	* applies to all region
	* creates trail in each region and records the log files in each region
	* the log files are deleivered to a single S3 bucket in any region
	* can also send the logs to CloudWatch Logs group in any region
	* one SNS topic is enough for receiving notification about log files in all regions
	* This is the default option when you create cloudtrail
* ##### One Region Trail
	* a bucket that receives events only from that region
* by default log files are encrypted
* log files delivered within 15mins of API calls
* used for external compliance audits
* watches for unauthorized accesses
* 