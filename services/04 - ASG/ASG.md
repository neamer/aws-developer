The purpose of Auto Scaling Group (ASG) is to match the load of the application to the horizontal scale of the infrastructure (The number of instances).

We define a minimum and maximum number of instances and the ASG will scale in (add instances) and scale out (remove instances) as load increases/decreases.

It also has the ability to automatically register new instances to a load balancer and to re-create instances in case of termination.

![[Pasted image 20231126154643.png]]


# ASG Attributes

##### Launch template 
- AMI + Instance Type
- EC2 User Data
- EBS Volumes
- Security Groups
- SSH Key Pair
- IAM Roles
- Network + Subnets Information
- Load Balancer Information
##### Min Size / Max Size / Initial Capacity

# Scaling Policies

### Dynamic Scaling Policies

**Target Tracking Scaling
- Most simple and easy set-up
- Example: I want the average ASG CPU to stay around 40%

**Simple / Step Scaling
- When a CloudWatch alarm is triggered then scale up/down

### Scheduled Actions
- Anticipate a scaling based on known usage patterns
- Example: Increase the min capacity to 10 at 5pm on Fridays

### Predictive Scaling
- Continuously forecast load and schedule scaling ahead

![[Pasted image 20231126161236.png]]

### CloudWatch Alarms & Scaling

It is possible to scale an ASG based on CloudWatch alarms

An alarm monitors a metric (such as Average CPU, or a custom metric)

Metrics such as Average CPU are computed for the overall ASG instances

Based on the alarm we can define scale-in or scale-out policies.

# Scaling Cooldowns

After scaling activity happens, you are in the cooldown period (default 300 seconds)

During the cooldown period, the ASG will not launch or terminate additional instances.

The purpose of scaling cooldowns is to allow for metrics to stabilize

# Instance Refresh

The goal of this feature is to re-create all EC2 instances in the ASG after updating the launch template/

We set a minimum healthy percentage and over time the ASG will delete instances and replace them with new ones.

We can also specify a warm-up time, which specifies how long until the instance is ready to use.