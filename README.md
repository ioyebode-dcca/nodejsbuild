# nodejs build 
# jenkins build

# this is poc for nodejs build
# Devops

You need to build a Jenkins pipeline that pulls its configuration from another git repository that can be centrally managed by the whole devOps team.
This pipeline should support running a Node.JS applications coverage tests and report back to a tool such as github the build status.
This should all be written in IaC and CM code of your choice.


You need to build a ECS cluster in AWS using Terraform.
Using a CI/CD tool such a Jenkins or CodeBuild, build a CI/CD flow that will monitor your git repository for changes to a docker file, build and push the dockerfile to ECR and deploy it to ECS for testing.
This should all be written in IaC and CM code of your choice.
