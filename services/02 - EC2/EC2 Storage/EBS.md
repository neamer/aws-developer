
An EBS (Elastic Block Store) Volume is a network drive you can attach to your instances while they run.

It allows your instances to persist data, even after termination.

**They can only be mounted to one instance at a time**
They are bound to a specific AZ.

*Think of them like network USB sticks*



# Important characteristics

Because its a network drive:
- It uses the network to communicate with an instance, so there might be some latency
- It can be detached from an EC2 instance and attached to another one quickly

They are bound to a specific AZ:
- An EBS Volume in one region cannot be attached to a instance in another
- We can move volumes across AZs with snapshotting

They have a provisioned capacity (size in GBs or IOPS):
- You get billed for all the provisioned capacity
- You can increase the capacity of the drive over time

Their relationship with EC2 Instances is one to many, that means that an EBS volume can only be attached to one EC2 Instance but an EC2 instance can have multiple EBS volumes.

#### Delete on termination attribute

Controls the EBS behaviour when an EC2 Instance is terminated

By default:
- The root EBS volume is deleted
- Any other attached EBS volumes are not deleted

# EBS Snapshots

Make a backup (snapshot) of your EBS volume at a point in time

Not necessary to detach the volume first, but it is recommended.

Snapshots can be copied across AZ and regions.

##### EBS Snapshot archive

Snapshots can be moved to an "archive tier" that is 75% cheaper.

It takes within 24 to 72 hours for restoring the archive

##### Recycle bin for EBS Snapshots

Retain deleted snapshots so you can recover them after an accidental deletion

Retention time is specified by user (from 1 day to 1 year)

##### Fast snapshot restore (FSR)

Force full initialization of snapshot to have no latency on first use (very expenive)


