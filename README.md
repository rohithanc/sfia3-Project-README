# sfia3-Project-README

## Aim / Introduction
The aim of the project is to create a Help Queue web application consisting of three applications, a front-end, back-end and a gateway service. The purpose of the Help Queue is so that trainees can post issues and queries about things they are not sure about so that trainers can solve them. The tickets are placed in a chronological list, with the oldest ticket at the top. The trainer would deal with the issue, mark the ticket as Done and added to a completed list.

The ticket comprises of the following attributes:

* Title
* Author
* Description
* Time Created
* Urgency
* Solution
* Status
* Email
* Topic

Software Development Requirements:

* Databases
* Java SE
* Spring Boot
* Front-End Development
* Automated Testing
* Continuous Integration
* Cloud Fundamentals

DevOps Requirements:

* Continuous Integration
* Containerisation
* Configuration Management
* Cloud Solutions
* Infrastructure Management
* Orchestration

## Planning and Development
A Jira board was used to assign tasks and stories to different members of the team.

![Jira Board](https://i.imgur.com/pIwZami.png)

## Risk Assessment

#####Pictured below is our risk assessment for this project:

![Risk assessment](https://i.imgur.com/ym53yIN.png)

## Front-end
The front-end service acts as the web application’s user interface and is written in React. 

### Templates and Wireframes
At the start of the project, research was done, looking up previous Help Queue services and establishing what key features would be best for this project. Templates were drawn up and wireframes were constructed for both MVP and stretch goal designs.

### Initial Development of Tickets

![First Development of Ticket]

![Latest Version of Ticket]

### Wireframes

![MVP Create Tickets](https://i.imgur.com/ITyaCe0.png) 

***MVP Create Tickets***

![Stretch Create Tickets](https://i.imgur.com/C3VLve5.png) 

***Stretch Goals Create Ticket***

## Gateway
The gateway service acts as a middleman between the front-end and back-end service. The front-end makes requests to the backend via the gateway service, using Spring Boot.
This was configured with NGINX in Kubernetes. 

## Back-end
The Backend is written in Java and consists of several microservices: *create*, *delete*, *get*, *getSingle* and *update*:

![CRUD gateway](https://i.imgur.com/I2Z50wA.png) 

Microservices benefitted us throughout the cloud computing process. We initally tested our application in a GCP cluster as it was free. Having our application split up into smaller, composable fragments made the testing process much smoother as the free virtual machines weren't being worked to fulll capacity.

Microservice infrastructure also provided flexibility. Once we realised a certain service wasn't needed for the application, we could decouple the service quickly and smoothly.

We used the *postman* application to test our backend (whilst the frontend wasn't built yet) with JSON http requests. JSON object example:

    {
        "id": 111,
        "title": "My Macbook wont allow me to connect to Teams",
        "author": "Carlos Aguila",
        "description": "My macbook wont allow me to access teams. It is working on my ubuntu laptop so it is not a big deal but i would like to be able to use my mac.",
        "timeCreated": [
            2020,
            12,
            16,
            16,
            18,
            35,
            369000000
        ],
        "urgency": "low",
        "solution": "no solution",
        "status": false,
        "email": "ca@qa.com",
        "topic": "Mac"
    }

We managed to write the java code for *cohorts*, *trainers* etc. but didn't manage to implement the stretch goal into our website. Pictured below is a comparison diagram which shows how we would use relational databases to implement this stretch goal:

![ERD](https://i.imgur.com/eRaopD5.png)

## Database
The data is persisted in an AWS RDS database.

## DevOps
Terraform was used to spin up Virtual Machines (VMs), one each to hold a Bastion Host, Jenkins and Nexus and an additional one to run tests on. Each VM is configured with a Virtual Private Cloud (VPC). Each VPC has three subnets (one private and two public), three security groups and an internet gateway. A separate RDS is also spun up, assigned with a private security group.

![Terraform Diagram with attributes](https://i.imgur.com/DxwfSG2.jpg)

The Jenkins Pipeline is not accessible directly from the Internet, only through the Bastion Host and is initially set up via Ansible.
![Jenkins Pipeline](https://i.imgur.com/TISjH4X.png)

Kubernetes clusters are used to containerize the frontend, gateway and backend services, with a NGINX reverse proxy used as a Load Balancer.
