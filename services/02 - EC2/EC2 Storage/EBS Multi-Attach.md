Attach the same EBS volume to multiple EC2 instances

**Only available for the io1 and io2 families** 

Each instance has full read-write permissions to volume

Use cases:
- Achieve higher application availability in clustered Linux applications
- Applications must manage concurrent write operations

Important to know:
- **Volumes can be connected to 16 instances at a time**
-  All instances must be in the same AZ
- Must use a file system that is cluster-aware