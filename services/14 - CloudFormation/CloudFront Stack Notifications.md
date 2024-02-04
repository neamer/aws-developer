We can enable SNS integration using Stack Options to send stack events to a SNS topic.

We can then hook this up to a Lambda, or a Email service

![[Pasted image 20240204215045.png]]
In this example we only want to send emails for `ROLLBACK_IN_PROGRESS` events.