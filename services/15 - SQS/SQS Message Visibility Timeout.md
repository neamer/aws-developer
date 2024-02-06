After a message is polled by a consumer, it becomes invisible to other consumers.

By default the message visibility timeout is set to 30 seconds, which means that the consumers has 30 seconds to process the message. After that period expires the message becomes visible again.

![[Pasted image 20240206202906.png]]

If the consumer is unable to process the message during the visibility timeout, it will be processed again by another consumer. To prevent this, we can manually set the message visibility using the **ChangeMessageVisibility API** to get more time.

If the visibility timeout is too high, and the consumer crashes during processing, it will take a lot of time to re-process the message.

On the other hand, if the timeout is too low, we run the risk of processing the same message multiple times.