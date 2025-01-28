* message queuing service
* buffer between application components that receive the data and those components that process the data
* work is queued if the servers can't process it
* SQS supports multiple components to use the queue simultaneously 
* doesn't guarantee FIFO
* ![[Screenshot 2025-01-23 at 6.54.17 PM.png]]
#### Delay Queues and Visibility Timeouts
* Delay queues halt the delivery of new messages in a queue for a specific number of seconds
* 