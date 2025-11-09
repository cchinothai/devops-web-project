<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Secure Packages with CodeArtifact

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-codeartifact-updated)

**Author:** Cody Chinothai  
**Email:** cchinothai@gmail.com

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

---

## Uploading My Own Packages

---

---
