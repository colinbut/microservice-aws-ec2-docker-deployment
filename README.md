# Microservice AWS EC2 Docker Deployment

This is a deployment project which it used Ansible to deploy containerized microservices to AWS EC2 instances running Docker.

![microservice-aws-ec2-docker-deployment](https://images-for-github-colinbut.s3.eu-west-2.amazonaws.com/microservice-aws-demo/microservice-aws-ec2-docker-deployment.png)

- Assumes the AWS EC2 instances have pre-setup with Docker installed.
- Assumes microservices are packaged into Docker containers and their Docker images are available from ECR
- Ansible pulls those Docker images and runs them on the already provisioned EC2 instances

Support deploying currently 2 microservices:

1. [microservice-java](https://github.com/colinbut/microservice-java)
2. [microservice-nodejs](https://github.com/colinbut/microservice-nodejs)

## Examples

To deploy microservice-java microservice which is a Java 8 Spring Boot microservice running on default port 8080...

```bash
ansible-playbook deploy.yml --extra-vars "HOST_PORT=8080 CONTAINER_PORT=8080 MICROSERVICE_NAME=microservice-java"
```

Similarily, to deploy a microservice-nodejs microservice which runs on default port 3000...

```bash
ansible-playbook deploy.yml --extra-vars "HOST_PORT=3000 CONTAINER_PORT=3000 MICROSERVICE_NAME=microservice-nodejs"
```
