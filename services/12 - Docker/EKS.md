Amazon Elastic Kubernetes Service provides a way to launch managed [[Kubernetes]] clusters on AWS.

It's an alternative to ECS, with a similar goal but a very different API (also a important distinction is that kubernetes is open-source while ECS is closed)

Like [[ECS]], EKS supports EC2 and Fargate launch types

Common use case:
- if a company already uses Kubernetes on-premises and wants to migrate to AWS

![[Pasted image 20240201222641.png]]
*EKS Architecture example*

# Node Types

**Managed Node Groups**
- Creates and manages nodes (EC2 instances) for you
- Nodes are part of an [[ASG]] managed by EKS
- Supports on-demand or spot instances

**Self-Managed Nodes**
- Nodes created by you and registered to the EKS cluster and managed by an [[ASG]]
- You can use prebuilt [[AMI]] - Amazon EKS Optimized AMI
- Supports on-demand or spot instances

**AWS Fargate**
- No maintenance required; no nodes managed

# Data Volumes

You will need to specify StorageClass manifest on your EKS Cluster to attach data volumes

Supports:
- [[EBS]]
- [[EFS]] (the only option which supports fargate)
- Amazon FSx for Lustre
- Amazon FSx for NetApp ONTAP