ECS Rolling Updates allow us to update our service without downtime by switching out instances over a period of time.

We have two parameters which control how the rolling update will be done:
- **Minimum healthy percent** - the minimum percentage of healthy instances available at any time during the update. The update process will terminate tasks running the old version while it is above this percentage.
- **Maximum percent** - the maximum amount of instances which can be instantiated during the rolling update

![[Pasted image 20240131155158.png]]

### Example: Min 50%, Max 100%

Starting number of tasks: 4

![[Pasted image 20240131155325.png]]

The rolling update will be performed in the following steps:
1. Two tasks are going to be terminated
2. Two tasks running the new version are going to be instantiated to replace them
3. Then, the remaining two tasks running the old version will be terminated
4. And finally, another two tasks running the new version will be instantiated


### Example: Min 100%, Max 150%

Starting number of tasks: 4

![[Pasted image 20240131155611.png]]

1. Two instances are going to be added because we cannot drop under 100%
2. Our percentage of healthy instances will be at 150%, so then we will terminate two to get back to 100%
3. After that we will repeat the process once more, terminating the old versions and adding new ones
