# AWS-ECR
Elastic Container Registry vs DockerHub. 

- ECR is an AWS service to store and manage containers.
- ECR means Elastic Container Registry :-
  - Container is a package which contains our application code and software dependencies required to run it.
  - ECR is a AWS service which is container registry similar to dockerhub
  - Primary use of registry is to store docker images
  - If we have docker image on our laptop and we have to share it to anyone across in the world (in same or different region). So we can push image to ECR and others can pull the same and use it.
  - Elastic means like any AWS service, ECR is highly scalable and available in nature, it can scale up and down according to requirements (capacity of services can be increased to accommodate any no of resources).
  - In ECR we can store any no of container images.
  - It is pay as you go service where AWS does not restrict us for the number of images
  - AWS will take care that ECR is available all the time
