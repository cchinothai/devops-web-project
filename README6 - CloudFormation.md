# Infrastructure as Code with CloudFormation

**Author:** Cody Chinothai  
**Email:** cchinothai@gmail.com

---

## Introducing Today's Project!

In this part of the project, we'll generate an infrastructure as code template using CloudFormation to deploy our resources. 

### Key tools and concepts

Services I used were
- CloudFormation (Template Creation / IaC generator)

We focused on fixing our cloud formation template, specifically ensuring that we resolved dependency issues (list dependencies, resolve circular dependencies), and create parameters for reuse

### Project reflection

This part of the project took me approximately 3 hours to ensure proper IaC generator scan and cloudformation template creation, leading to successful stack creation. 

Next is the last part of the DevOps project where we complete our CI/CD pipeline!

---

## Generating a CloudFormation Template

The IaC Generator is a tool that scans our account resources and generates the cloudformation template for us . 

A CloudFormation template is used for group tracking of resources such that they can be updated and deleted together all at once. 

The resources I couldn’t add to my template were my CobdeBuild project and CodeDeploy deployment group since they have specific configuration details that can't be managed by IAC generator

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-cloudformation-updated_0495b046)

---

## Template Testing

Deleted existing resources...

The first test failed since we have to create the IAM role first before we start creating the policies

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-cloudformation-updated_f56730fd)

---

## DependsOn

To resolve the error, we specify a dependency - telling CodeArtifact to wait for the role that grants it access to your EC2 instance

We apply thiis DependsOn line to each of our EC2 instances. 

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-cloudformation-updated_f0df8018)

---

## Circular Dependencies

I gave my CloudFormation template another test! But this time we got an error stating that we have a circular dependency 

To fix this error, I remove the managedpolicyarns from the iam role for code build. we don't need these references when he we have DependsOn

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-cloudformation-updated_e6fd85ed)

---

## Manual Additions

We manually added the codebuild project and code deploy deployment group. 

I also had to make sure the references were consistent in this template, so I ensured that we were using the right 
- codebuild service role id
- s3 bucket id
- codedeploy role id
- codedeploy application id

I also introduced Parameters, which allow our cloudformation templates to be reusable and flexible by parameterizing values instead of hard coding them 
- allows you to use the same template for different environments  or repositories without modifying the template itself. 

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-cloudformation-updated_1cee0428)

---

## Success!

I could verify all the deployed resources by visiting the resources tab in the cloud formation stack. 
*note that this doesn't list some of our manually created resources

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-devops-cloudformation-updated_bd8b836b)

---

---
