Instead of running `aws configure`, which would expose our access key to anyone with access to the instance. In order to access resources in our EC2 instance we should use IAM Roles for EC2 Instances. 

We can attach an IAM Role for our instance by 
1. Navigating to instance tab
2. Selecting the instance
3. Actions
4. Security
5. Modify IAM Role