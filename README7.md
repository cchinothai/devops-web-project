<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a CI/CD Pipeline with AWS

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-codepipeline-updated)

**Author:** Cody Chinothai  
**Email:** cchinothai@gmail.com

---

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codepipeline-updated_fbdetger)

---

## Introducing Today's Project!

In this project, I will automate our CI/CD pipeline using AWS CodePipeline in order to 
- automatically detect code changes in our github repository
- automatically trigger CodeBuild to build a new project
- automatically start CodeDeploy with new build artifacts
- automatically roll back a change if something fails. 

### Key tools and concepts

Services I used were
- AWS CodePipeline, integrating our Github Repo, AWSCodeBuild, and AWSCodeDeploy

### Project reflection

This project took me approximately 3 hours.

---

## Starting a CI/CD Pipeline

AWS CodePipeline is a service that let's you create a workflow to automatically move code changes through the build and deployment stage. 
- A push to the github repository will initiate codebuild (CI) and codedeploy (CD)

Execution Mode:
- superceded: if a new pipeline execution is triggered, any execution already in progress will get canceled and the new one will take over. 
- queued: executions are processed in order by when they were initiated
- parallel: multiple executions will run independently of each other, speeds up processing time if you have multiple branches or code changes that can be deployed concurrently. 

A service role for CodePipeline gives it permission to access your AWS resources (ex. S3 for storing artifacts, CodeBuild for building your code)

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codepipeline-updated_gdnhtm)

---

## CI/CD Stages

The three stages I've set up in my CI/CD pipeline are
- Source
- Build
- Deploy

CodePipeline organizes the three stages into source, build, and deploy

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codepipeline-updated_fbdetger)

---

## Source Stage

In the Source stage, the default branch tells CodePipeline to monitor this branch for changes and trigger the pipeline if so 

Webhook events are digital notifications that are setup to listen for specific events such as code pushes to our main branch. This notification needs to be sent to CodePIpeline to start the execution in our CI/CD process.

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codepipeline-updated_sergt)

---

## Build Stage

The Build stage sets up compiling and packaging for our code before it becomes a deployable build artifact. I configured the bulid provider to connect to AWS Codebuild. The input artifact for the build stage is our source artifact - the ZIP file containing our source code that was outputted by the source stage. 

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codepipeline-updated_j1k2l3m4)

---

## Deploy Stage

The Deploy stage is where we integrate AWS CodeDeploy with CodePipeline I configured this by including the application that we have included in our CodeDeploy console along with the associated deployment group. 

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codepipeline-updated_m4n5o6p7)

---

## Success!

Test pipeline by pushing new code to our github branch and see how CodePipeline reacts. 

The moment I pushed the code change, the source stage kicked in progress and generated a commit ID with a link to the new changes in our repo. 

Once my pipeline executed successfully, I checked our production EC2 instance via it's public DNS to see our deployed website and confirmed that we now see our changes that were pushed. 

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codepipeline-updated_e1f2g3h4)

---

## Testing the Pipeline

---

---
