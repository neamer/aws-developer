The optional `Outputs` section declares output values that you can import into other stacks (to create cross-stack references), return in response (to describe stack calls), or view on the AWS CloudFormation console. For example, you can output the S3 bucket name for a stack to make the bucket easier to find.

They are very useful when you define a network CloudFormation and then output the variables such as VPC ID and your subnet IDs

You cannot delete a stack whose outputs are being referenced anywhere else

```yml
Outputs:
	StackSSHSecurityGroup:
		Description: The SSH Security Group for our Company
		Value: !Ref MyCompanyWideSSHSecurityGroup
		Export:
			Name: SSHSecurityGroup
```

To import this value in another template, we will use the `Fn::ImportValue` function

```yml
SecurityGroups:
	- !ImportValue SSHSecurityGroup
```
