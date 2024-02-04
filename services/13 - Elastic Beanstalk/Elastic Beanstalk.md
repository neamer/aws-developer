So far, the go-to for deploying applications in this course was [[Three Tier Architecture]]. Configuring architecture manually can take a lot of time, and managing and scaling it is another concern.

Elastic beanstalk is a developer centric view of deploying an application on AWS which combines all the components we have used so far (like EC2, ASG, ELB, RDS ...)

It is a managed service which automatically handles:
- Capacity provisioning
- Load balancing
- Scaling the application
- Health monitoring
- Instance configuration

We still have control over the configuration

# Components

**Application** - A collection of Beanstalk components (environments, versions, configurations)

**Application version** - A iteration of your application code

**Environment** - Collection of AWS resources running **one** application version. Environments can be of a certain tier (Web Server Environment Tier and Worker Environment Tier). You can create multiple environments.

![[Pasted image 20240204122924.png]]

# Environment tiers

### Web Server Tier

![[Pasted image 20240204123103.png]]

This is a classic setup for serving end users with a [[ELB]] which is connected to a [[ASG]] which scales our [[EC2]] instances in multiple AZs

### Worker tier

![[Pasted image 20240204123225.png]]

In this environment, no end users are going to be accessing our EC2 instances. They will instead process messages from an SQS queue. We can push the messages to the SQS queue from a Web Server Tier environment

# Deployment modes

### Single instance

![[Pasted image 20240204123435.png]]

Based on one EC2 instance with an Elastic IP (has the ability to launch RDS databases or similar).

**Good for development purposes**

### High availability with load balancer

![[Pasted image 20240204123556.png]]

Meant for production environments, this deployment mode provides high availability, scalability and load balancing.

# Lifecycle Policy

Elastic Beanstalk can store up to 1000 application versions

If you don't remove the old versions, you won't be able to deploy anymore.

To phase out the old versions, we use livecycle policies:
- Based on time (older versions are removed first)
- Based on space 

Versions that are currently in use will not be deleted

# Extensions

A zip file containing our code must be uploaded to Elastic Beanstalk to deploy our application.

All the UI parameters and more can be configured in the files we upload with **Elastic Beanstalk Extensions**.

The files have to be in the `.ebextensions/` directory in the root and must be in YAML or JSON format. Their name has to end with `.config`.

With these files we are able to modify some default settings as well as add resources such as RDS, ElastiCache, DynamoDB...

Resources managed by .ebextensions get deleted if the environment goes away

# Cloning

This feature allows you to clone an environment with the exact same configurationIt is useful for deploying a "test" version of your application

All resources and configurations are preserved:
- Load balancer type and configuration
- RDS database type (but the data is not preserved)
- Environment variables

After cloning an environment, you can change the settings