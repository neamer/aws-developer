Amazon Elastic Container Service (ECS) is a fully managed container orchestration service that helps you to more efficiently deploy, manage, and scale containerized applications.

It allows us to launch Docker containers on AWS and then launch ECS Tasks on ECS Clusters

We have two launch types for ECS:

# Launch Types

#### EC2 Launch Type

For this launch type, you will need to provision and maintain the EC2 instances that will be running your containers. The EC2 launch type is suitable for large workloads that must be price optimized.

![[Pasted image 20240129164851.png]]

Every EC2 Instance will have a ECS docker agent running to be able to register in the ECS cluster.

After that, AWS takes care of starting / stopping containers.

#### Fargate Launch Type

The Fargate launch type allows us to launch docker containers on AWS **without provisioning the infrastructure**.

It's serverless, we just create ECS task definitions and AWS will run them based on the CPU / RAM you need.

![[Pasted image 20240129165426.png]]

**The exam has a bias towards this launch type over the EC2 one because it's much easier to manage**

# IAM Roles for ECS

We have two ways of using IAM roles in ECS:

An **EC2 Instance Profile** is used directly by the docker agent on your EC2 instances (only for the EC2 Launch Type). And the profile will be used to:
- Make API calls to ECS
- Send logs to CloudWatch
- Pull images from ECR
- Reference sensitive data in Secrets Manager or SSM Parameter Store

Our ECS tasks will have **ECS Task Roles**. Each task will have a specific role which allows us to use different roles for each ECS Service we run. Task roles are defined in the **task definition**.

![[Pasted image 20240129170124.png]]

**The most important setting in the `ecs.config` file is `ECS_ENABLE_TASK_IAM_ROLE` which enables IAM roles for ECS tasks.**

# Load Balancer Integrations

When we want to expose ECS Tasks as a HTTP/HTTPS endpoint we can setup an Load balancer in front of it which will route the users to the ECS tasks.

- [[ALB]] is supported and works for most use cases
- [[NLB]] is recommended only for high throughput / high performance use cases, or to pair it with AWS Private Link
- You can also use the Classic Load Balancer but it is not recommended (no advanced features - no Fargate)

# Data Volumes (EFS)

We can mount [[EFS]] file systems onto ECS tasks, which will allow all tasks which are running in any AZ to share the same data in the EFS file system

This works for both EC2 and Fargate launch types

**Using Fargate with EFS allows us to have a completely serverless setup**

Note that Amazon S3 cannot be mounted as a file system for ECS tasks