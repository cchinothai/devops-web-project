# CI/CD Architecture
<img width="2770" height="952" alt="image" src="https://github.com/user-attachments/assets/82366512-76eb-43f9-9b14-f9c289808e26" />




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



# Connect a GitHub Repo with AWS

**Author:** Cody Chinothai  
**Email:** cchinothai@gmail.com

---

## Connect a GitHub Repo with AWS

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-github_dd9d254e)

---

## Introducing Today's Project!

In the next step of our project, we will connect our GitHub repo to AWS

Key Concepts:
CI/CD
Amazon EC2
VSCode
GitHub

### Key tools and concepts

Services used: 
CI/CD
Amazon EC2
VSCode
GitHub

### Project reflection

This project took me approximately 1-2 hours

Day 2 of DevOps challenge

Continue to day 3 of devops project ... 

---

## Git and GitHub

 I installed Git using the commands...

sudo dnf install git -y

Use github as our main source code repository and link it into our pipeline process

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-github_efaadbf7)

---

## My local repository

//setup github repo

//run git init

//start with master branch

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-github_7bf21bae)

---

## To push local changes to GitHub, I ran three commands

### git add

//add all files 

### git commit

//create commit

### git push

//push commit

---

## Authentication

github needs credentials to verify the account your are accessing

### Local Git identity

Git needs author information for commits to track who made what change. If you don't set it manually, Git uses the system's default username, which might not accurately represent your identity in your project's version history.

git log output: 
- commit id
- author
- date

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-github_9a27ee3b)

---

## GitHub tokens

GitHub authentication failed when I entered my password because it only supports token authentication for security purposes

We use a Gtihub PAT to securely log into github using the token as a random generated sequence of characters.

We set up the personal access token within our github account settings

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-github_fa11169d)

---

## Making changes again

//update index.jsp

//commit and push changes

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-github_6becb2bc)


