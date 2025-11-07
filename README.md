# CI/CD Architecture
<img width="1227" height="442" alt="image" src="https://github.com/user-attachments/assets/9aa2dfb0-6c0f-4722-a7f3-bba586b5800c" />



<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Set Up a Web App in the Cloud


**Author:** Cody Chinothai  
**Email:** cchinothai@gmail.com

---

## Set Up a Web App Using AWS and VS Code

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-vscode_7a1de541)

---

## Introducing Today's Project!

In this project, I will demonstrate setting up my AWS environment for hosting a web app using connection to EC2

### Key tools and concepts

Services I used were
- EC2 t3.micro (we had to use a swap storage to accomodate for the limited compute space in order to use the remote ssh) - refer to https://community.nextwork.org/c/i-have-a-question/fixing-vs


### Project reflection

Key things I learned were
- EC2 setup within VS Code using SSH 
- Using Maven as a build atuomation tool to structure the web app 

Roughly 2-3 hours

This project is part one of a series of DevOps projects where I'm building a CI/CD pipeline! 

---

## Launching an EC2 instance

We are launching this ec2 instance to use amazon's virtual server to build and deploy our application. We will connect to it via SSH

### I also enabled SSH

SSH is a secure protocol to allow remote access to a server. I enabled SSH so that my connection to the server is private and ecrypts all data

### Key pairs

A key pair is an encrypted key file that allows us to connect to our instance securely

Once I set up my key pair, AWS automatically downloaded the key pair as a .pem file 

---

## Set up VS Code

We use VS Code for our IDE

we will install vscode to connect to our ec2 instance

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-vscode_53d05e68)

---

## My first terminal commands

We use the terminal to access our key pair in the DevOps folder

allow access into key pair: 
 $ chmod 400 myNewKeyPair.pem

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-vscode_9328ada1)

---

## SSH connection to EC2 instance

To connect to my EC2 instance, I ran the ssh command using the key pair as the first argument and 'ec2-user@[public dns] as the second argument

### This command required an IPv4 address

A server's IPV4 DNS is the public ip address it uses for inbound connection

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-vscode_e3069dca)

---

## Maven & Java

Apache Maven provides a uniform build system to build, compile, and test a java project

We use maven in this project to build our web app using archetypes 

//Install java into our instance 

Maven requires Java in order to operate

---

## Create the Application

I generated a Java web app using: 
mvn archetype:generate \

specifying the project name and web app as the type

Use Remote - SSH extension to connect to the ec2 instance and get more granular control of the web files 

we added the ec2 connection route into our  user's .ssh file 

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-vscode_2939cf01)

---

## Create the Application

//VSCode file explorer ssh'd with ec2

src - source code 
-> webapp - web app's files
-> resources - config files (ex. for database connection)


![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-vscode_45f91fd7)

---

## Using Remote - SSH

The index.jsp is the HTML file for java to display markup for a web app 

We can add HTML elements directly within index.jsp

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-vscode_7a1de541)

---

## Using nano

---

---
