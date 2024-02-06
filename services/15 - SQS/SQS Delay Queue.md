Delay queues let you postpone the delivery of new messages to consumers for a number of seconds, for example, when your consumer application needs additional time to process messages. If you create a delay queue, any messages that you send to the queue remain invisible to consumers for the duration of the delay period. The default (minimum) delay for a queue is 0 seconds. The maximum is 15 minutes.

![[Pasted image 20240206213432.png]]

Delay queues are similar to visibility timeouts because both features make messages unavailable to consumers for a specific period of time. The difference between the two is that, for delay queues, a message is hidden _when it is first added to queue_, whereas for visibility timeouts a message is hidden _only after it is consumed from the queue_. The following diagram illustrates the relationship between delay queues and visibility timeouts.

