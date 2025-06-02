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





