The optional [`Conditions`](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-condition.html) section contains statements that define the circumstances under which entities are created or configured. For example, you can create a condition and then associate it with a resource or output so that AWS CloudFormation only creates the resource or output if the condition is true. 

Common conditions are:
- Environment (dev / test / prod)
- AWS Region
- Any parameter value

```yml
Conditions:
	CreateProdResources: !Equals [!Ref EnvType, prod]
```

The logical id (in this example CreateProdResources) can be whatever you want

The function can be any of the following:
- `Fn::And`
- `Fn::Equals
- `Fn::If`
- `Fn::Not`
- `Fn::Or`

Conditions can be applied to resources / outputs ...

```yml
Resources:
	MountPoint:
		Type: "AWS::EC2::VolumeAttachment"
		Condition: CreateProdResources
```