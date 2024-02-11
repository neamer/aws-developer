KCL is a Java library that helps read records from a Kinesis Data Stream with distributed applications sharing the read workload.

Each shard is to be read by only one KCL instance, but instances can read from multiple shards:
- 4 shards = maximum 4 KCL instances
- 6 shards = maximum 6 KCL instances

Things that KCL will handle for us:
- multiple consumer application instances, 
- responding to consumer application instance failures, 
- checkpointing processed records, and 
- reacting to resharding.

KCL will use DynamoDB to checkpoint progress, track other instances and coordinate work between them. Because of this it will need IAM access to DynamoDB

Records are read in order at the shard level

KCL has two versions:
- KCL 1.x (only supports shared consumer)
- KCL 2.x (supports shared and enhanced fanout consumer)


# Scaling Example

### Staring setup: 4 shards and 2 instances

![[Pasted image 20240210200051.png]]

The KCL apps will use DynamoDB to coordinate and they will split the capacity evenly. If a instance were to go down, the other one would continue where it left of thanks to checkpointing. 

### Scaling to 4 instances

If we scale the apps to 4 we will end up with this setup

![[Pasted image 20240210200253.png]]

### Scaling the shards to 6

The work will be split between the instances, and we could end up with a setup like this:

![[Pasted image 20240210200428.png]]

### Scaling the KCL instances to 6

As expected, the apps will coordinate themselves and each will get one shard.

![[Pasted image 20240210200609.png]]

The most important thing to remember is that **we cannot have more KCL instances than shards**. 