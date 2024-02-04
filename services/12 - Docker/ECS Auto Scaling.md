ECS Auto Scaling allows us to increase/decrease the desired number of ECS tasks

Amazon ECS Auto Scaling uses AWS Application Auto Scaling which allows us to scale based on:
- ECS Service Average CPU utilization
- ECS Service average memory utilization
- ALB request count per target - metric coming from the ALB

Then, we can setup different kinds of auto-scaling:
- **Target Tracking** - scale based on target value for a specific CloudWatch metric
- **Step Scaling** - scale based on a specified CloudWatch Alarm
- **Scheduled Scaling** - scale based on a specified date/time (predictable changes)

Remember that **scaling your ecs service at the task level is not equal to scaling your cluster of ec2 instances** if you are in the EC2 launch type

# Auto Scaling EC2 Instances

If we want to scale the underlying EC2 Instances in order to accommodate ECS Service scaling, we can do that in two ways:
- **Auto Scaling Group Scaling** allows us to scale our [[ASG]] based on CPU utilization
- **ECS Cluster Capacity Provider** automatically provisions and scales the infrastructure for our ECS Tasks. The Capacity Provider is paired with a ASG, and it adds instances when we are missing capacity (CPU,RAM...). **This is the recommended option**

#### Example: ECS Scaling on CPU Usage

![[Pasted image 20240131154222.png]]

*In this example we have a web server which is running with ECS. When a increase in number of users causes the CPU usage to reach critical levels, it will trigger a CloudWatch Metric alarm. Which will then increase the amount of tasks. Optionally, if we have a ECS Cluster Capacity Provider Set up, it would also scale the underlying EC2 instances.*