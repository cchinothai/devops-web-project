# Deploy a Web App with CodeDeploy

**Author:** Cody Chinothai  
**Email:** cchinothai@gmail.com

---

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codedeploy-updated_val-27)

---

## Introducing Today's Project!

In this part of the project, I will demonstratesimplified deployment using AWS CodeDeploy. 
- Deployments are automated to reduce manual steps
- Rollouts are consistent and downtime is minimized
- Rollback automaticallly upon failure

### Key tools and concepts

Services I used were
- AWS CloudFormation 
- AWS CodeDeploy

Wrote deployment scripts to automate deployment commands

Setup CodeDeploy deployment groups to deploy our web app

### Project reflection

This project took me approximately 2 hours

Continue to Day 6 of the DevOps challenge

---

## Deployment Environment

I created an EC2 instance along with our VPC within our cloudformation template to use specifically for our production server that hosts our web app.

We grouped the resourced into a CloudFormation stack which allows grouped deletion if we need to rollback. 

Other resources: 
VPC (Virtual Private Cloud): our virtual network in the cloud for our resources
Subnet: subdivision of the VPC where we place resources
Route Tables
Internet Gateway - Allows resources in VPC to connect to internet
Security group

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codedeploy-updated_val-5)

---

## Deployment Scripts

We use this script to setup the software and internet traffic used to host our web app 

The 'install_dependencies will utilize: 
- Tomcat: our java application server
- Apache (http server)

Allow Apache to act as a reverse proxy for Tomcat (redirect requests to Tomcat with ProxyPass and ProxyPassReverse)

The start_server.sh will fire up our java application server (Tomcat) and set auto-start whenever the server reboots. 
- Start Apache HTTP server for our web frontend
- Set apache to auto-start on reboot

The stop_server.sh will first check if our web server services are running, and if they are it will stop both Apache and Tomcat

---

## appspec.yml

The appspec.yml is the orchestration file outline the specific steps mapping what file goes where and what scripts to run 

Update buildspec.yml to produce artifacts for our appspec.yml and scripts, along with our WAR file

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codedeploy-updated_val-12)

---

## Setting Up CodeDeploy

A deployment group is a collection of grouped EC2 instaces working together under the same application, specifying what servers to deploy, what is the deployment pattern, other settings etc. 
A CodeDeploy app is the general namespace for that group

CodeDeploy needs IAM roles to get permissions to access and manage AWS resources on your behalf. 



We use tags so that our target EC2 instances can be identified by CodeDeploy

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codedeploy-updated_val-18)

---

## Deployment configurations

AllAtOnce: apply updates to all EC2 instances (fastest, error prone once scaled)
OneAtATime: update one instance then verify before moving onto the next
HalfAtATime: update half then verify before updating all

CodeDeployAgent allows our EC2 instnace to communicate with CodeDeploy. 

- During deployments, it acts as the. middleman, taking directions from CodeDeploy and carries it to EC2

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codedeploy-updated_val-20)

---

## Success!

A CodeDeploy deployment is a single update to your application with a unique ID and history. 
- specify version of application
- specify deployment group to deploy it
- specify deployment settings

A revision location is where CodeDeploy looks to find your application's build artifacts --> in our s3 bucket

Once deployment succeeded without error, click the instance ID and paste the public IPV4 into the search bar. **make sure to use http instead of https because the security group only allows connections on port 80 which is http only

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codedeploy-updated_val-27)

---

## Disaster Recovery

---

---
