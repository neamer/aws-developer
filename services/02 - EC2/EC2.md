EC2 stands for Elastic Compute Cloud and provides Infrastructure as a service.

The main capabilities of EC2 are:
- Renting virtual machines (EC2)
- Storing data on virtual drives (EBS)
- Distributing load across machines (ELB)
- Scaling the services using a auto-scaling group (ASG)

### EC2 configuration options

Operating system
- Linux
- Windows
- MacOS

Computing power & cores (CPU)

Random access memory

Storage space
- Network-attached (EBS & EFS)
- Hardware (EC2 instance Storage)

Network
- Network adapter
- Public IP adress

Firewall rules: security group

Bootstrap script: [[EC2 User Data]]

### EC2 Instances


![[Pasted image 20231029114553.png]]

Our EC2 instance gets generated public and private addresses. The public address is used for accessing the instance from the web and the private address is used internally from within aws.

The private ipv4 will always stay the same but the public one may change (when restarting the instance for ex.)

