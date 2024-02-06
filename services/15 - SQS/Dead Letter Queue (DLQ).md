We can set a threshold to how many times a message can be received after it has failed to be processed. This is called the **Maximum Receives** threshold. After a message reaches this threshold it is sent to a dead letter queue.

![[Pasted image 20240206210134.png]]

**DLQ of a FIFO queue must also be a FIFO queue**

**DLQ of a Standard Queue must also be a standard queue**

It is good to set the retention time to 14 days for these queues to make sure it is processed.

# Redrive to Source

You can configure a _dead-letter queue redrive_ to move standard unconsumed messages out of an existing dead-letter queue back to their source queues

![[Pasted image 20240206210616.png]]

The idea is that we do manual inspection of the messages in the DLQ, and then we fix the issue that was causing this. Then, if we conclude that the issue was not caused by faulty messages we can use this feature to send them back to the queue to be processed.