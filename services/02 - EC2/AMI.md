Amazon Machine Image

AMI are a customization of an EC2 Instance

They contain an operating system, additional software, configuration and monitoring

Faster boot / configuration because all your software is pre-packaged

AMI are built for a specific region (but can be copied across regions)

AMI options:
- Public AMI (AWS provided)
- Custom AMI (You have to make and maintain them yourself)
- AWS Marketplace AMI (A marketplace that a 3rd party made and potentially sells)

### Process of creating an AMI from a EC2 Instance

1. Start an EC2 Instance and customize it
2. Stop the instance (for data integrity)
3. Build an AMI (will also create EBS snapshots)
4. Launch instances from other AMIs

**AMIs are built for a specific AWS Region, they're unique for each AWS Region. You can't launch an EC2 instance using an AMI in another AWS Region, but you can copy the AMI to the target AWS Region and then use it to create your EC2 instances.**