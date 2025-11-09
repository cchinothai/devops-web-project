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

# Secure Packages with CodeArtifact

---

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codeartifact-updated_1d79e699)

---

## Introducing Today's Project!

In this step of the project, we'll setup our CodeArtifact repository to store the packages for our web app. 

We use an artifact repository within AWS to ensure security and consistency with the packages/package version that we use 

### Key tools and concepts

Services I used were: 
- EC2
- CodeArtifact

Key concepts I learnt include
- Connecting our EC2 instance to codeartifact
- setting up maven central as our upstream repo
- configuring maven to access codeartifact to check for dependencies

### Project reflection

This project took me approximately 2 hours

Continue to Day 4 of CI/CD project

---

## CodeArtifact Repository

Benefits of using CodeArtifact
- team members can retrieve packages from a secure repository 
- if public package websites go down, you have backups in your CodeArtifact
- your team can share and use the same versions of packages 

Domains manage multiple repositories by housing all of their permission and security settings

Our upstream repository allows us to have a backup library that our primary repo can access to get packages and download them into local storage. 

We get access to all the public libraries with the benefits of caching, control, and consistency

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codeartifact-updated_n4o5p6q7)

---

## CodeArtifact Security

### Issue

To access CodeArtifact, we need a CodeArtifact authorization token to connect to our artifact repo from the linux terminal

I ran into an error when retrieving a token because we have not setup permissions for EC2 to access our CodeArtifact repo 

### Resolution

To resolve the error with my security token, we created an IAM policy for CodeArtifact to get our auth token and assigned it to our IAM role connected with out EC2 instance

It's security best practice to use IAM roles because it provides separation of permissions that we define for very specific purposes, such as for the particular AWS service that we use 

---

## The JSON policy attached to my role

- allow retrieval of authorization token for codeartifact
- allow retrieval of endpoint for codeartifact repository
- allow package reading from repo

- allow AWS Security Token Service to get service bearer token if it's only for CodeArtifact

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codeartifact-updated_23rp7q8r9)

---

## Maven and CodeArtifact

### To test the connection between Maven and CodeArtifact, I compiled my web app using settings.xml

The settings.xml file configures Maven with our CodeArtifact setup, creating a seamless connection that ensures that our builds automatically authenticate and pull dependencies from the right place. This is a one-time only setup

Compiling means maven is downloading dependencies from your CodeArtifact repository..

- it looks at your project's dependencies in pom.xml then checks the codeartifact repository.
- if the dependencies aren't in codeartifact, it will fetch upstream

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codeartifact-updated_c17eace8)

---

## Verify Connection

//checked the codeartifact repo for dependencies from our pom.xml. 

- for our first time, codeartifact doesn't have them so it goes to maven central (upstream) to download and store them 

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codeartifact-updated_1d79e699)





