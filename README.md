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
- Go to ECR - Create (Private repo by default) - Provide repo name - Enable tag immutability (If we try to overwrite images by same tag, it is prevented), keep it disabled - Image scan settings (when pushing images they will get scanned)
- People accessing these repos should have an IAM user with them

![image](https://github.com/user-attachments/assets/5d2af9c2-5ba8-4c28-838c-4ab05aca1c6d)
![image](https://github.com/user-attachments/assets/9d2106e3-a952-4dbf-bd2c-796c1d2e94e9)

- We can see "View Push commands" for our created repo to get things done, following which we can push our images to ECR

![image](https://github.com/user-attachments/assets/357b57c4-e767-4422-910d-cc3f65e2e50b)

- To run commands, we must have AWS CLI installed

- To login to ECR registry, first login to docker hub and then run below command
  - Command :- **aws ecr get-login-password --region eu-north-1 | docker login --username AWS --password-stdin 975049937461.dkr.ecr.eu-north-1.amazonaws.com**
  - Here first part fetches our AWS ECR creds and then pipe is used to give output of first command to second
 

- Here we're using root account so image gets pushed. If logged in using IAM users we need to grant access explicitly.

- Now using container image build the dockerfile.
  - For now just enter "FROM ubuntu:latest" to dockerfile and build image
  - Command :- d**ocker build -t demo-app-repo .**
 
![image](https://github.com/user-attachments/assets/23406251-5616-40d4-ba20-9629e0a3d571)

- Now tag the docker image
  - Command :- **docker tag demo-app-repo:latest 861276124894.dkr.ecr.us-east-2.amazonaws.com/demo-app-repo:latest**
  - Tag means image created on local tag it to docker registry. So that the image is pushed to our registry

- Now to push the image
  - Command :- **docker push 861276124894.dkr.ecr.us-east-2.amazonaws.com/demo-app-repo:latest**
  - After pushing image to ECR, anyone with proper IAM access can access the image
  - Now image built in local in available in AWS ECR

![image](https://github.com/user-attachments/assets/15b4fa83-8d9a-465a-9f9e-799598872c26)





