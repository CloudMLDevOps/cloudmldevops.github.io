# cloudmldevops.github.io
This is Github Pages maintained for Cloud and DevOps Practices

# Docker-Basics
- Navigate to [Docker-Basics](docs/docker-basics.md)

# Cheatsheets

## Docker Cheatsheet
- Navigate to [Docker Cheatsheet](docs/docker-cheatsheet.md)

# Automation
## Python AWS Automation
- Navigate to [Python AWS Automation](docs/python-aws-automation.md)

# QnA
## Linux QnA
- Navigate to [Linux Question Answers](docs/linux-questions-answers.md)

## Git QnA
- Navigate to [Git Question Answers](docs/git-questions-answers.md)

## AWS QnA
- Navigate to [AWS Question Answers](docs/aws-questions-answers.md)

## Terraform QnA
- Navigate to [Terraform Question Answers](docs/terraform-questions-answers.md)

## Kubernetes QnA
- Navigate to [Kubernetes Question Answers](docs/kubernetes-questions-answers.md)

## DevOps QnA
- Navigate to [DevOps Question Answers](docs/devops-questions-answers.md)

## CloudOps QnA
- Navigate to [CloudOps Question Answers](docs/cloudops-questions-answers.md)



{::options parse_block_html="true" /}

## <a name="docker-tips">Docker Tips</a>

## <a name="docker-tips">Docker Tips</a>

# DevOps FAQs

<details><summary markdown="span"><b>How do Agile and DevOps Interrelate</b></summary>

Agile and DevOps both prioritize collaboration, continuous improvement, and delivering working software. They can be used together to create a more efficient software development process. Agile emphasizes iterative development and customer satisfaction, while DevOps emphasizes automating processes and integrating development and operations teams. When used together, Agile and DevOps can improve software development and delivery by streamlining processes and enhancing collaboration.

</details>

<details><summary markdown="span"><b>What are some misconceptions about DevOps</b></summary>

- **DevOps is just automation**: While automation is an important part of DevOps, it's not the only thing. DevOps is a culture that emphasizes collaboration, communication, and integration between development and operations teams to improve the quality and speed of software delivery.
- **DevOps is just a job title**: DevOps is a mindset and set of practices, not a specific job title. Anyone involved in the software development and delivery process can adopt a DevOps mindset and apply DevOps practices in their work, including developers, testers, operations engineers, and others.
- **DevOps eliminates the need for IT operations**: DevOps does not eliminate the need for IT operations. Instead, it changes the way that operations teams work by promoting collaboration with development teams and introducing new tools and processes for deployment, monitoring, and maintenance.

</details>

<details><summary markdown="span"><b>DevOps Engineer Must Have</b></summary>

- To become a DevOps Engineer, you need to have technical skills in areas such as **development, automation, containerization, cloud, CI/CD pipelines** etc.
- Some sample tools and technologies to know are any **Programming Language ( Python and Shell ), AWS, Terraform, Docker, Kubernetes, Jenkins, Git, Ansible and Logging/Monitoring** tools.
- Gain experience by working on Sample DevOps projects, develop a DevOps mindset, and apply for DevOps Engineer positions by highlighting your skills and experience in your resume.

</details>

Sources:

* [CodeFresh Everyday Hacks Docker](https://codefresh.io/blog/everyday-hacks-docker/)

<details><summary markdown="span"><b>Heredoc Docker Container</b></summary>

```sh
docker build -t htop - << EOF
FROM alpine
RUN apk --no-cache add htop
EOF
```

</details>