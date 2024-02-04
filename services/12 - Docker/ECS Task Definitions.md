Task definitions are metadata in JSON form to tell ECS how to run a Docker container

It contains crucial information, such as:
- Image name
- Port Binding for Container and Host
- Memory and CPU
- Environment variables
- Networking information
- IAM Role
- Logging configuration (e.g. CloudWatch)

![[Pasted image 20240131162421.png]]

In this example we have a EC2 Instance running our ECS Task which runs a Apache HTTP server. We set up the container port to be 80 and the host port to be 8080. This means that the container port will be 80, but the EC2 instance will expose the 8080 port.

We can define up to 10 containers in a task definition

### ECS Load balancing on EC2 launch type

![[Pasted image 20240131163140.png]]

**We get a Dynamic Host Port Mapping if we only define the container port in the task definition**. Therefore, each ECS task running on a EC2 instance will be accessible with different random ports. 

Then if we link an ALB to this ECS service, it will use the Dynamic Host Port Mapping to find the right ports on our EC2 instances

For this to work, we have to configure the EC2 instances Security Group to allow any port to be accessed by the ALB's Security Group

### ECS Load balancing with Fargate

Each ECS Task will receive a unique private IP this time.

Since we have no direct control over the host, we will **only define the container port**

![[Pasted image 20240131164000.png]]

For this example to work, we will need to configure:
- The **ECS ENI Security Group** to allow port 80 from the ALB
- **ALB Security Group** to allow port 80/443 from web


# IAM Roles in ECS

### IAM Roles are assigned per Task Definition

![[Pasted image 20240131164323.png]]

All ECS Tasks created from this task definition will inherit the role, but the **roles are assigned at the task definition level**


# Environment Variables

Our task definitions can have environment variables, and they can come from different places

- Hardcoded - for nonsensitive information such as URLs
- SSM Parameter Store - sensitive data (e.g. API keys, shared configs)
- Secrets Manager - sensitive variables (e.g. DB password)

Then we also have the option to load them directly from an S3 bucket and this is called a bulk variable loading through a file.

# Sharing data between tasks

With bind mounts, a file or directory on a host, such as an Amazon EC2 instance or AWS Fargate, is mounted into a container. Bind mounts are supported for tasks that are hosted on both Fargate and Amazon EC2 instances.

This will create a shared storage between our tasks

![[Pasted image 20240131164951.png]]

in this example, our application containers will write to the shared storage (mounted in /var/logs) and our metrics & logs container will read from it

**EC2 Tasks** will use EC2 instance storage and the data is tied to the lifecycle of the EC2 instance

**Fargate Tasks** will use ephemeral storage. Data is tied to the container using them. We can choose from 20GiB to 200GiB

Use cases: 
- Share data between multiple containers
- "Sidecar" container pattern, where the "sidecar" container used to send metrics/logs to other destinations (separation of concerns)