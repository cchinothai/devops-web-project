<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Continuous Integration with CodeBuild

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-codebuild-updated)

**Author:** Cody Chinothai  
**Email:** cchinothai@gmail.com

---

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codebuild-updated_35588a47)

---

## Introducing Today's Project!

Use AWS CodeBuild to automate our web app's build process

### Key tools and concepts

Services I used were
- Codebuild
    - setup Github App 
    - setup buildspec.yml
- CodeArtifact

### Project reflection

This project took me approximately 2 hours

Continue to Day 5 of DevOps series...

---

## Setting up a CodeBuild Project

CodeBuild is a continuous integration service to compile, run and package code without having to manage your own server build

specify source code location within github
- choose GitHub as source provider

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codebuild-updated_fewgrhte)

---

## Connecting CodeBuild with GitHub

Would normally thing to use a personal access token since we set it up for Github, but this may have some security leaks by granting access to tokens directly. Setup with Github App instead

AWS CodeConnections as a secure bridge between AWS and external repositories
- no need to use github tokens or manage api keys


![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codebuild-updated_a7c98e2d)

---

## CodeBuild Configurations

### Environment

- use On-demand to only provision build resources when needed
- use AWS created image
- use EC2 for flexible and powerful compute (don't need fast startup times)

### Artifacts

Build artifacts are the outputs of our build processes that allow our server to run. 

We will produce the WAR (web application resource) file and store in S3 so that our server can unpackage and use for web hosting

### Packaging

- compressed zip for size efficiency and faster s3 upload/downlaod

- better organization within zip file 

- single zip makes it simple when deploying app or sharing

### Monitoring

Use cloudwatch logs for monitoring our build process. keep track of 
  - commands ran 
  - potential errors

use to debug any future build failures

---

## buildspec.yml

My first build failed because... we are missing the buildspec.yml file that is needed to detail the build steps

Phases: 
install - install java8
prebuild: grab security token
build: use maven to compile code
postbuild: package artifact (create WAR file)

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codebuild-updated_35588a47)

---

## Success!

We need to setup permission to connect CodeBuild with CodeArtifact

//created access to codeartifact by going to codebuild service role and applying permission for the codeartifact consumer policy

check s3 for published artifact

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-codebuild-updated_d9cc6191)

---

## Automating Testing

---

---
