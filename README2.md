
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


