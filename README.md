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

-----------------------------------------------------------------------------------------------

Difference between ECR and DockerHub
-
- When we start using containers, first registry we use is dockerhub as it is free and can create our public repo where we can push images so others can access and download. Dockerhub also has private repo where only authorized people can access our image.
- ECR supports private repo concept by default whereas in Dockerhub by default repository created is public. (We can create public repos in ECR as well). So ECR is security prompt.
- Advantage here is we can use our IAM users along with ECR, we can integrate IAM with ECR. If we tag IAM users with ECR, only authorized users can access it keeping our images secure.
- If dockerhub goes down we dont have that much support which we have in AWS's ECR.
- ECR has very good integration with other AWS services like ECS, EKS, Fargate.
- For personal projects, we can use dockerhub but for organizational level always use ECR as it is private container registry.

-----------------------------------------------------------------------------------------------

Practical Demo
-
