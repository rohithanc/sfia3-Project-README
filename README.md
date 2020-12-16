# sfia3-Project-README

# README
## Aim / Introduction
The aim of the project is to create a Help Queue web application consisting of three applications, a front-end, back-end and a gateway service. The purpose of the Help Queue is so that trainees can post issues and queries about things they are not sure about so that trainers can solve them. The tickets are placed in a chronological list, with the oldest ticket at the top. The trainer would deal with the issue, mark the ticket as Done and added to a completed list.

The ticket comprises of the following attributes:

•	Title

•	Author

•	Description

•	Time Created

•	Urgency

•	Solution

•	Status

•	Email

•	Topic

## Planning
A Jira board was used to assign tasks and stories to different members of the team.

## Risk Assessment

## Front-end
The front-end service acts as the web application’s user interface and is written in React. 

### Templates and Wireframes
At the start of the project, research was done, looking up previous Help Queue services and establishing what key features would be best for this project. Templates were drawn up and wireframes were constructed for both MVP and stretch goal designs.
![MVP 

## Gateway
The gateway service acts as a middleman between the front-end and back-end service. / / The front-end makes requests to the backend via the gateway service, using Spring Boot.
This was configured with NGINX in Kubernetes. 

## Back-end
The Backend is written in Java and consists of several microservices: *create*, *delete*, *get*, *get Single* and *update*

## Database
The data is persisted in an AWS RDS database.

## DevOps
Terraform was used to spin up Virtual Machines (VMs), one each to hold a Bastion Host, Jenkins and Nexus and an additional one to run tests on. Each VM is configured with a Virtual Private Cloud (VPC). Each VPC has three subnets (one private and two public), three security groups and an internet gateway. A separate RDS is also spun up, assigned with a private security group.

![Terraform Diagram with attributes](https://i.imgur.com/DxwfSG2.jpg)

The Jenkins Pipeline is not accessible directly from the Internet, only through the Bastion Host and is initially set up via Ansible.
![Jenkins Pipeline](https://i.imgur.com/TISjH4X.png)

Kubernetes clusters are used to containerize the frontend, gateway and backend services, with a NGINX reverse proxy used as a Load Balancer.
