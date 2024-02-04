Parameters are a way to provide input for you CloudFormation templates

Common use cases are:
- You want to reuse your templates across the company
- Some inputs can not be determined ahead of time

Parameters are extremely powerful and can prevent errors from happening in your templates thanks to types

```yml
Parameters:
	SecurityGroupDescription:
		Description: 'Security Group Descripiton (Simple Parameter)'
		Type: String
```

To reference parameters in our template, we use the Fn::Ref function. The shorthand for this in YAML is !Ref

```yml
DbSubnet1:
	Type: AWS::EC2::Subnet
	Properties:
		VpcId: !Ref MyVPC
```

The Ref function can also be used to reference resources, it will return the physical ID of the resource


### Pseudo Parameters

Pseudo parameters are parameters that can be used any time and are enabled by default

![[Pasted image 20240204202247.png]]