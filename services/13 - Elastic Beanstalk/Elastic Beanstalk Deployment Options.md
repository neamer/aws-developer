# All at once

![[Pasted image 20240204124852.png]]

The update will be done in the following steps:
1. All instances will be stopped
2. New instances with the new version will be launched

This option has the fastest deployment time, but has downtime. It is great for quick iterations in development where we don't care about downtime.

There is also no additional cost for this option.

# Rolling

![[Pasted image 20240204125226.png]]

The update will be done in the following steps:
1. The first bucket will get selected (in this ex. we have a bucket size of 2)
	1. Stop all instances in the bucket
	2. Start new version for the bucket
2. Then the exact same step will be iterated through the remaining buckets

This option will have our application running below capacity while the update is in progress, but there is no downtime. As we can see, the application will be running two versions simultaneously during the process.

We can control the speed of the deployment vs the available capacity by tweaking the bucket size.

There is no additional cost with this option.

# Rolling with additional batches

![[Pasted image 20240204125825.png]]

This option takes a very similar approach as Rolling updates, like the name suggests. The main difference is that a new batch will be created to ensure that **our application never run below capacity.** 

An important thing to note is that this approach **has additional cost associated to it**.

# Immutable

![[Pasted image 20240204130128.png]]

The new version will be deployed on a new temporary ASG. When the new version instances pass health checks, they will be moved to the current ASG and the previous version instances will be terminated.

This option has zero downtime and offers quick rollback in terms of failures, but it is **high cost** due to needing double the capacity to perform an update. It also has the longest deployment time.

# Blue / Green

Not that this is not a direct feature of Elastic Beanstalk and some documentation will not even mention it.

The idea is to create a new "stage" environment and deploy the new version there

The new environment (green) can be validated independently and rolled back if there are issues. In Route 53 we can set up weighted traffic policies to redirect a small amount of traffic to the new environment.

When we want to complete the update, we will swap the URLs and shut down the blue environment

![[Pasted image 20240204130802.png]]


# Traffic Splitting

This approach offers a automated approach to **Canary testing** (if you see Canary testing on the exam, think Traffic Splitting).

![[Pasted image 20240204131322.png]]

The idea is similar to the immutable option, a temporary ASG with the new version instances will be created. Then, a small percentage of traffic will be sent to that new ASG, and deployment health will be closely monitored. If failure happens, then a very quick automatic rollback will be triggered. After the new version is deemed stable, the instances are migrated to the primary ASG and the old version is terminated.

# Comparison of all the options

![[Pasted image 20240204131308.png]]