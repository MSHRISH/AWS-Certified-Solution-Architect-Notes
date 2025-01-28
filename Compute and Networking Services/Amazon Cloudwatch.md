* monitoring tools
* Default Basic Monitoring-sends data points to CloudWatch every 5 mins of limited no.of metrics at no charge
* Detailed Monitoring-sends data points every minute and data aggregation costs extra
* aggregate data across AZs but not regions
* custom metrics that are not visible to AWS can be `PUT` into CloudWatch with help of API
* each AWS Account has 5000 alarms 
* metrics data is retained for 2weeks default
#### Amazon CloudWatch Logs
* used to store and monitor logs 
* logs can be stored in S3 or Glacier and retained according to aging policies
* can track error logs and trigger events
* CloudWatch Logs Agent sends logs to CloudWatch from EC2 (need to be installed and configured)