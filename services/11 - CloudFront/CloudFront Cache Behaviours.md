We can configure different behaviours for a given URL pattern

We can route to different kind of origins/origin groups based on the content type or path pattern

When adding additional Cache Behaviors, the Default Cache Behaviour is always the last to be processed and is always /* 

![[Pasted image 20240125205613.png]]

In this example we have two Cache behaviors:
- For the /api/\*: The origin is an [[ALB]]
- For all other routes: The origin is an S3 bucket

###  Example: Sign in page

![[Pasted image 20240125210041.png]]

*In this example we want to be able to authenticate the users before they can access the content from the S3 bucket. For this we set up our Cache behaviours so that /login request are taken from a EC2 instance origin which generates Signed Cookies. After getting a signed cookie the user can access all other routes on the S3 Bucket.*

### Example: Separate dynamic and static distributions

![[Pasted image 20240125210341.png]]

*In this example we want to maximize cache hits for Static requests and we will set up our caching rules to maximize cache hits by disregarding headers and session data. But for the dynamic content, we will cache based on corrct headers and cookies for our dynamic content.*