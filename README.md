# 2.-Deploy-Apache-Web-Server-using-Terraform-IaC--project-2


## Table of Contents

    1. Goal
    2. Pre-Requisites
    3. Deployment
    4. Validation
    5. Destroy

![aws-02](https://user-images.githubusercontent.com/47071968/228747422-e4edf512-e756-479f-9c39-0e60b291c046.png)

## Goal

Goal of this project to write Terraform IaC to deploy Apache Webserver in AWS cloud.

## Pre-Requisites

    1. Create below resources using  Terraform IaC
        a. Create S3 Bucket to store the terraform statefiles
        b. Create DynamoDB
    2. Deploy VPC Network using Terrafom IaC and keep the state file in S3 backend.
    3. Create below resources using Terraform IaC and keep the state file in S3 backend
        a. S3 Bucket to store the webserver configuration and PUT index.html and Ansible Playbook
        b. SNS topic for notifications
        c. IAM Role
    4. Golden AMI
    5. Keep the Ansible Playbook to configure Apache webserver


## Deployment

   1. Write Terraform IaC to deploy below resources in the VPC that was created in the Pre-Requisites step and keep the state file in S3 backend with state locking support.
        
        a. Create  IAM Role granting PUT/GET  access to S3 Bucket and Session Manager access.
        
        b. Create Launch Configuration with userdata script to pull the index.html file from S3 and attach IAM role and configure the webserver (May run Ansible Playbook to configure webserver)
        
        c. Create Auto Scaling Group with Min:1 Max: 1 Des: 1  in private subnet
        
        d. Create Target Group with health checks to and attach with Auto Scaling Group
        
        e. Create Application Load balancer in public subnet and configure Listener Port to route the traffic to the Target Group
        
        f. Create alias record in Hosted Zone to route the traffic to the Load balancer from public network.
        
        g. Create Cloudwatch Alarms to send notification when ASG state changes.
        
        h. Create Scaling Policies to scale out/Scale In when average CPU utilization is > 80%
        
    2 Deploy Terraform IaC to create the resources

## Validation

    1. Login to AWS Console and verify all the resources are deployed
    2. Access the web application from public internet browser using the domain nam
    
    
## Destroy

    1. Destroy the resources once the testing is over to save the billing.

If not confident, Repeat the steps again. Good Luck.  Comment here with your Bitbucket repo link to review the code.
