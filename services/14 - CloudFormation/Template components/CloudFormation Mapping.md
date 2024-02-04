Mappings are fixed variables within your CloudFormation template. IE all the values are hardcoded directly in the template

They're very handy to differentiate templates between:
- environments
- AWS regions
- AMI types ...

```yml
Mappings:
	RegionMap:
		us-east-1:
			"32": "ami-24515sdgy"
			"64": "ami-ds3hy4421"
		us-west-1:
			"32": "ami-24515sdgy"
			"64": "ami-ds3hy4421"
		eu-west-1:
			"32": "ami-24515sdgy"
			"64": "ami-ds3hy4421"
```
*Example of mapping containing AMI-s for specific regions and 32-64 bit architectures*

To access mapping values, we use the `Fn::FindInMap` function

it takes 3 parameters in the form of a array:
- MapName
- TopLevelKey
- SecondLevelKey

```yml
SomeProperty: !FindInMap [RegionMap, !Ref "AWS::Region", 32]
```
*Example usage of FindInMap based on the mapping example above*