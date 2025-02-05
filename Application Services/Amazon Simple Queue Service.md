* message queuing service
* buffer between application components that receive the data and those components that process the data
* work is queued if the servers can't process it
* SQS supports multiple components to use the queue simultaneously 
* doesn't guarantee FIFO but can be enabled
* messages are sent to queue from producers
* messages are pulled from queue by consumers
* after processing the message is deleted from the queue
* one of first service in AWS
* unlimited throughput, unlimited number of messages
* default 4 days retention period
* max 14 days retentions period
* low latency (< 10 ms)
* limitation of 256KB per message
* can have duplicate messages
* 
* ![[Screenshot 2025-01-23 at 6.54.17 PM.png]]
#### Delay Queues and Visibility Timeouts
* Delay queues halt the delivery of new messages in a queue for a specific number of seconds
* After a message is polled by a consumer, it becomes invisible to other consumers, this is called visibility timeout
#### Long Polling
* consumers wait for messages if there are no messages in the queue
* decreases the no.of API calls made to SQS while increasing latency
* between 1 second adn 20 second
* 