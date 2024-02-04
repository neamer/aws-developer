It is possible to bootstrap EC2 instances using an EC2 User Data script.

Bootstrapping means launching commands when a machine starts.

This script is only run **once** at first start.

EC2 User Data is used to automate tasks such as:
- Installing updates
- Installing software
- Downloading common files from the internet

The EC2 User Script runs with the root user.