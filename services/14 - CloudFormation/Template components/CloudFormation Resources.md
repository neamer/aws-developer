Resources are the core of your CloudFormation template (the only mandatory component). They represent the different AWS components that will be created and configured

Resources we declare can reference other resources

There are over 224 types of resources, but they all folllow this form
```
AWS::aws-product-name::data-type-name
```

Just note that everything in the CloudFormation template has to be declared, and you cannot perform code generation there