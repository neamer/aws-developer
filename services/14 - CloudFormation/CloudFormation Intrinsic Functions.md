Here are the intrinsic functions that you must know for the exam:
- **`Fn::Ref`** used for referencing parameters or resources - described in [[CloudFormation Parameters]]

- **`Fn::GetAtt`** used for getting values from specified attributes. Attributes are attached to any resource you create and they are all listed on the [aws documentation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-template-resource-type-ref.html)
```yml
...
Properties:
	AvailabilityZone: !GetAtt MyExampleEC2Instance.AvailabilityZone
```
*Example: Getting the availablity zone of a EC2 instance*

- **`Fn::FindInMap`** used to return a named value from a specific key - described in [[CloudFormation Mapping]]

- **`Fn::ImportValue`** used for importing values that are exported in other templates - described in [[CloudFormation Outputs]]

- **`Fn::Join`** used for joining values with a delimiter
```yml
!Join [":", [a, b, c]] # This creates a:b:c
```

- **`Fn::Sub`** is used to substitute variables in an input string with values that you specify
```yml
Name: !Sub 
  - 'www.${Domain}'
  - Domain: !Ref RootDomainName
```
We do not need to specify mappings if we are substituting template parameters, resource IDs or resource attributes. Example:
```yml
!Sub 'arn:aws:ec2:${AWS::Region}:${AWS::AccountId}:vpc/${vpc}'
```
