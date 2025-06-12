# End-to-End-DevOps-Implementation-for-Microservices-Architecture
:star: This project shows the demonstration and implementation of a Demo application using DevOps tools 
## 🧰 Tech Stack :
- 

## understing the architecture or the main components of the project

<img width="699" alt="Screenshot 2025-06-01 at 11 50 59 AM" src="https://github.com/user-attachments/assets/73ccd336-db74-439d-acfc-f229f6ac6b53" />
<img width="681" alt="Screenshot 2025-06-01 at 11 55 25 AM" src="https://github.com/user-attachments/assets/ac9b4fdf-ffbd-4760-8340-5aaf12511518" />

- internet :- to access the project
- load generator :- to simulate real time load
- React Native :- for application to be mobile compatible
- Frontend Proxy(reverse proxy)(Envoy) :- A reverse proxy is a server that sits in front of backend servers to forward client requests, providing load balancing, security, and caching.
- Frontend :- From front end you can go to your product catalog service, cart service, shipping service , payment service , email service

## 📝 Steps to Run the Project

- launch an EC2 Inastance :- image = Ubuntu , AMI = latest , instance type = t2.large , create keypair , auto assign publicIP shoud be enabled now launch the instance.
<img width="1280" alt="Screenshot 2025-06-01 at 1 00 11 PM" src="https://github.com/user-attachments/assets/d997f0d2-5905-4e19-9468-e648de5aba92" />

- connect to the instance using the terminal (ssh)
<img width="1280" alt="Screenshot 2025-06-01 at 1 01 29 PM" src="https://github.com/user-attachments/assets/812d6ce5-e0fd-42c2-933e-87b689b7f472" />

- download docker engine to our instance (refer docker documentation)
<img width="1280" alt="Screenshot 2025-06-01 at 1 13 40 PM" src="https://github.com/user-attachments/assets/de4b9e74-63bf-4c35-a005-958eee05ca8b" />

- install kubectl on our instance to interact with kubernetes cluster
<img width="1280" alt="Screenshot 2025-06-01 at 1 25 41 PM" src="https://github.com/user-attachments/assets/8078038e-07d0-433c-9c2d-d73bca54f63b" />

- install terraform (IaC - infrastructure as code):
<img width="1280" alt="Screenshot 2025-06-01 at 1 36 29 PM" src="https://github.com/user-attachments/assets/073e4c32-9c36-4c29-9dbd-d889f83e9a33" />

## lets try to run the project locally

- we use Docker compose to run the project locally
- clone the project to our instance using git clone

:warning: now we are facing an issue that there is no space left on instance
<img width="1280" alt="Screenshot 2025-06-01 at 3 43 13 PM" src="https://github.com/user-attachments/assets/b6ac3cef-1534-4c0f-a70a-8684b4b2a2ad" />

- lets resolve the issue:-
1. lets go to volume of our instance on aws account we can see the volume of our instance
<img width="1280" alt="Screenshot 2025-06-01 at 3 46 11 PM" src="https://github.com/user-attachments/assets/0bb62a4f-6c49-48e8-bb23-cc641796cc6f" />

2. select the volume
3. click on the actions modify the volume
4. change the size to 30 gb and click on modify
<img width="1280" alt="Screenshot 2025-06-01 at 3 49 27 PM" src="https://github.com/user-attachments/assets/8eaf2eaf-3d20-48dd-9a2b-da744cbc56e9" />
5. also we have to mount the volume to file system then only it can be in use
<img width="1280" alt="Screenshot 2025-06-01 at 4 02 09 PM" src="https://github.com/user-attachments/assets/54a619fc-669e-4a56-9222-6c6c48bd947e" />
6. our volume is mounted and process got started
<img width="1280" alt="Screenshot 2025-06-01 at 4 05 30 PM" src="https://github.com/user-attachments/assets/53f03a4f-b07f-44e2-8a43-9a863c58ba9d" />

7. now lets see how to access it on the browser we have to open some ports for our instance first
8. allow all traffic and save the rules
<img width="1280" alt="Screenshot 2025-06-01 at 4 13 35 PM" src="https://github.com/user-attachments/assets/034d19aa-7faa-454c-bde4-526252241e91" />

10. now copy the public ip of instance and paste it to browser and add 8080 port to it to see the output

:rocket: here are the output result
<img width="1280" alt="Screenshot 2025-06-01 at 4 13 55 PM" src="https://github.com/user-attachments/assets/1f004e24-cc6f-4ba5-8187-18e8cda5f649" />

## Now lests see the process of containerization of the project

There are multiple microservices are used in this project which are developed using different different tech stack like Python ,java, go lang ,etc.
- now we will se how to containerize it

:star: Docker lifecycle: Dockerfile -> DockerImage -> container.

- ✅ lets containerize product catalog(microservice)
- It is a go lang based application so we need go lang to be installed.
- export it to any port
- now execute the build command for the application which is already provided by the developer
- every programming language has a dependancy file for eg: python has requirements.txt , java has if you are using maven it will be in pom.xml similarly in golang it is go.mod (it is developers responsibility to write dependencies)
- bulid process download the dependencies
-following is example of how you run it locally
<img width="1280" alt="Screenshot 2025-06-02 at 12 40 25 PM" src="https://github.com/user-attachments/assets/8f96eeaf-b4c4-4bed-a8fc-00d69fc34614" />
- now lets write the Dockerfile to create a docker image for application (using multi stage docker build) because in multi stage we use very lightweight images so it does not download unwanted binaries so the chances of vulnerability are low. in multiple stahe you jut copy required binary from first stage and use it in second stage.

<img width="1280" alt="Screenshot 2025-06-02 at 1 32 34 PM" src="https://github.com/user-attachments/assets/816dca72-63cb-4299-b6c9-936b5e2cf203" />

- we have got our expected output
<img width="1280" alt="Screenshot 2025-06-02 at 2 40 10 PM" src="https://github.com/user-attachments/assets/d55c3ac9-2509-4d56-ae24-eb54335a4923" />


- ✅ now containerize Ad microservice(java) :-
- go to github repo and see the instructions provided by the developer to build the service locally (every developer provides it)
- in this microservice gradle is used instead of maven
- lets run this project locally before creating docker file
<img width="1280" alt="Screenshot 2025-06-02 at 3 12 09 PM" src="https://github.com/user-attachments/assets/185c9b06-344c-4c80-a2d5-51ca98610de1" />

- following is our dockerfile
<img width="1280" alt="Screenshot 2025-06-02 at 3 26 23 PM" src="https://github.com/user-attachments/assets/068455b7-19a7-475e-8b69-8a621e76a299" />
- following is our expected output after running our containerized app

<img width="1280" alt="Screenshot 2025-06-02 at 3 52 55 PM" src="https://github.com/user-attachments/assets/e6f8c2a4-a2f7-4422-82a8-e217e72d625f" />


- ✅ now lets containerize the python based microservice :-
- following is our dockerfile for this application
- <img width="1280" alt="Screenshot 2025-06-02 at 4 13 29 PM" src="https://github.com/user-attachments/assets/95d7a1a7-1323-4f62-a1ac-aa6f3fc2262d" />
- this is the output
- <img width="1280" alt="Screenshot 2025-06-02 at 4 12 35 PM" src="https://github.com/user-attachments/assets/f10b9780-c5d3-45b4-bad5-7f55b690ebed" />

## Using Terraform to create EKS cluster using cloud
- we are using local machine and VScode to write and use teraform code
- create access key and secret access key of our user
- download the aws cli to your machine
- and configure it
- now we will  write a terraform code to create aws resources
- following code is to create s3 bucket and dynamoDB table for terraform state file
<img width="1280" alt="Screenshot 2025-06-08 at 7 56 23 PM" src="https://github.com/user-attachments/assets/0ec665de-68bd-4fcd-ad5e-86bdc358d714" />
<img width="1280" alt="Screenshot 2025-06-08 at 7 56 46 PM" src="https://github.com/user-attachments/assets/7ac88643-7bff-4842-8f1d-91e87a6e82e6" />
<img width="1280" alt="Screenshot 2025-06-08 at 7 57 09 PM" src="https://github.com/user-attachments/assets/02e5e262-337a-4842-b567-871e7413d44a" />
<img width="1280" alt="Screenshot 2025-06-08 at 7 57 37 PM" src="https://github.com/user-attachments/assets/8caaf076-d10b-4183-8109-d5d3066e6051" />

- Now we will create VPC And EKS cluster module in terraform
- the code is provided in our repo
- now we have created a eks cluster and VPC using terraform (for code see repository)
  
- <img width="1280" alt="Screenshot 2025-06-10 at 11 13 04 AM" src="https://github.com/user-attachments/assets/cae07ec4-6602-48ea-8c2c-e677d775bea1" />

## Now we will deploy project to kubernetes

- now we will use our ec2 instance to communicate to eks cluster
- install AWS CLI to our instance
- now we will add our kubernetes cluster context to our instance
- <img width="1280" alt="Screenshot 2025-06-10 at 2 05 10 PM" src="https://github.com/user-attachments/assets/06d49fd4-b524-4246-bac5-191726cb2b59" />
- there are yaml files and service files are written already but we will understand them and implement them
- now we will create a service account
- now we will access the project using loadbalancer
- we have changed the tye to loadbalancer
- loadbalancer is created
- <img width="1280" alt="Screenshot 2025-06-10 at 3 26 06 PM" src="https://github.com/user-attachments/assets/e8a5b45a-c697-4939-a515-dd4ee2605e62" />
- output of our project using eks loadbalancer
<img width="1280" alt="Screenshot 2025-06-10 at 3 27 34 PM" src="https://github.com/user-attachments/assets/0404e7de-44f7-4412-a704-1e5248bc344a" />

- now we will deploy the ALB ingress controller
- we just downloaded our abl ingress controller
- <img width="1280" alt="Screenshot 2025-06-11 at 12 23 16 PM" src="https://github.com/user-attachments/assets/49f4cdb1-fb61-4601-8ada-d070573818a0" />

- now lets create the ingress resource
- in ingress file we are only allowing tht if we hit example.com then only show the output
- we have changed the dns records on our local host for host based rputing
- following is the output using ingress 
- <img width="1280" alt="Screenshot 2025-06-11 at 3 14 44 PM" src="https://github.com/user-attachments/assets/9d3ea6cb-4e57-45a3-a97b-74f018a7de0f" />

