The CLI will look for credentials in this order:

![[Pasted image 20240117133643.png]]


Consider the following scenario:

![[Pasted image 20240117133719.png]]

**The answer is that the environment variable used will take precedence over IAM Instance Profile because of the credential precedence chain**.

# Credentials best practices

![[Pasted image 20240117133918.png]]