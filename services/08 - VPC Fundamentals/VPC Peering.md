VPC peering connects two VPC, privately using AWS' network and makes them behave as if they were part of the same network.

Important things to note:
- T**he VPCs can't have overlapping [[CIDR]]**
- **VPC Peering connection is not Transitive**, it must be established for each VPC that need to communicate with one another. 

![[Pasted image 20240104120244.png]]

In this example VPC B and VPC C are not connected, to connect them we need to have the following setup:

![[Pasted image 20240104120319.png]]