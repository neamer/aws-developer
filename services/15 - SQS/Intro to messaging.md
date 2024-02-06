When we deploy multiple applications, they will inevitably need to communicate with each other

There are two patterns for application communication:

### Synchronous communication
a.k.a application to application

![[Pasted image 20240205215659.png]]

### Asynchronous / Event based
a.k.a application to queue to application

![[Pasted image 20240205215741.png]]

The main problem with synchronous communications is the possibilities of overwhelming the applications we are communicating with if there are sudden spikes of traffic.

To avoid that we should **decouple** our applications:
- using [[SQS]] - queue model
- using [[SNS]] - pub/sub model
- using [[Kinesis]] - real-time streaming model

Theses services can scale independently from our application