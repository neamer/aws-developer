Docker is a tool that is used to automate the deployment of applications in lightweight containers so that applications can work efficiently in different environments in isolation.

A Docker **container** is a standardized, encapsulated environment that runs applications. It is a process created from an image.

Docker images are stored in Docker Repositories:
- Docker Hub, which is a public repository that contains base images for many technologies and operating systems
- Amazon ECR, which is a private repository in AWS. With a public option called Amazon ECR public gallery


![[Pasted image 20240128154735.png]]

A Dockerfile essentially the source code of a docker image, it contains instructions and configurations which defines how a container will act. We can use this file to **build** a docker image. Then we can **push** the docker image on docker repositories to store it. Then we can **pull** these images from the repositories when we need them. Then we can **run** the images which will create containers


# Docker on AWS

Amazon [[ECS]]

Amazon [[EKS]]

AWS Fargate

Amazon [[ECR]]