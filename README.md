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
