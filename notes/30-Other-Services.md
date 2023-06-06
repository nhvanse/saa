
- [CloudFormation](#cloudformation)
- [Amazon SES](#amazon-ses)
- [PinPoint](#pinpoint)
- [SSM Session Manager](#ssm-session-manager)
- [SSM Other Services](#ssm-other-services)
- [Cost Explorer](#cost-explorer)
- [Elastic Transcoder](#elastic-transcoder)
- [AWS Batch](#aws-batch)
- [Amazon AppFlow](#amazon-appflow)


# CloudFormation
- create AWS Infra
  - <img alt="picture 1" src="image/30-Other-Services/1-CloudFormation-1.png" width="800" />  
- Benefits
  - Infra as code
    - no resources are manually created
    - infra changes are reviewed through code
  - Cost:
    - Easy to manage cost by tag
    - Estimate costs by template
    - Saving Strategies: can delete/recreate template periodically to save cost 
  - Productivity
    - easy to destroy and create
    - automated generation of Diagram
    - Declarative programming
  - Don't re-invent the wheel
  - Support almost all AWS resources
  - <img alt="picture 2" src="image/30-Other-Services/1-CloudFormation-Benefits-1.png" width="800" />  
  - <img alt="picture 3" src="image/30-Other-Services/1-CloudFormation-Benefits-2.png" width="800" />  
- Stack Deigner
  - <img alt="picture 4" src="image/30-Other-Services/1-Cloud-Formation-Stack-Designer.png" width="800" />  
- Hands on
  - Access CloudFormation
  - Create stack 
    - new template by code /use sample template/create in Designer
    - choose update code (yaml file)
    - choose view in Designer to see the diagram
    - tag
    - IAM role (optional)
    - Estimate the cost
    - Create
  - View events (Create in progress, cretae complete, update, cleanup...)
  - Update template
  - Example
    - [example](../udemy/code/cloudformation/1-ec2-with-sg-eip.yaml)
    - <img alt="picture 5" src="image/30-Other-Services/1-CloudFormation-Hands-on.png" width="800" />  
  - Delete stack


# Amazon SES
- SES
  - simple email service
  - <img alt="picture 6" src="image/30-Other-Services/2-SES.png" width="800" />  


# PinPoint
- Supports email, SMS, push, voice, and in-app messaging
- next evolution of SNS and SES
- <img alt="picture 7" src="image/30-Other-Services/3-Pinpoint.png" width="800" />  


# SSM Session Manager
- execute commands to EC2 instances through SSM Session Manager (instead of SSH)
- <img alt="picture 8" src="image/30-Other-Services/4-SSM-Session-Manager.png" width="800" />  
- Hands on
  - Create an EC2 instance
    - attach IAM role profile
    - <img alt="picture 9" src="image/30-Other-Services/4-IAM-Role.png" />  
  - Access Systems Manager
    - click Fleet Manager to view
    - click Session Manager
    - start a session
    - using secure shell in browser
- 3 ways to connect an Ec2 instance
  - 1 - open port 22 -> ssh
  - 2 - use EC2 Instance Connect (click Connect on EC2 Service) (require port 22)
  - 3 - Use Session Manager (use IAM role, NO port 22 open)


# SSM Other Services
- **Run Command**
  - execute a command/document/script on 1 or multiple instances
  - no need for SSH
  - Output ->logs in S3, CloudWatch
  - send noti to SNS
  - Integrated with IAM and CloudTrail
  - can be invoked using EventBridge
  - <img alt="picture 10" src="image/30-Other-Services/5-SSM-Run-Command.png" width="800" />  

- **Patch Manager**
  - automate patching managed instances
  - (OS updates, app update, security updates )
  - <img alt="picture 11" src="image/30-Other-Services/5-SSM-Patch-Manager.png" width="800" />  

- **Maintainance Windows**
  - Schedule for when perform actions on instances
  - <img alt="picture 12" src="image/30-Other-Services/5-SSM-Maintainance-Windows.png" width="800" />  

- **Automation**
  - ex: restart instances,  create an AMI, EBS snapshots
  - use document to define called `Automation Runbook`
  - <img alt="picture 13" src="image/30-Other-Services/5-SSM-Automation.png" width="800" />  


# Cost Explorer
- <img alt="picture 14" src="image/30-Other-Services/6-Cost-Explorer.png" width="800" />  
- By Service
  - <img alt="picture 15" src="image/30-Other-Services/6-Cost-by-service.png" width="800" />  
- By Hourly and Resource
  - <img alt="picture 16" src="image/30-Other-Services/6-Cost-By-Hourly-and-Resources.png" width="800" />  

- Saving Plans
  - recommend saving plans based on our usage
  - <img alt="picture 17" src="image/30-Other-Services/6-Cost-Saving-Plans.png" width="800" />  

- Forecast Usage
  - <img alt="picture 18" src="image/30-Other-Services/6-Cost-Forecast-Usage.png" width="800" />  


# Elastic Transcoder
- convert media files in S3 -> new format in clinet devices
- <img alt="picture 19" src="image/30-Other-Services/7-Elastic-Transcoder.png" width="800" />  


# AWS Batch
- any scale, fully managed
- has start time and end time
- launch  `EC2 instances` or `Spot Instances`
- Batch jobs are defined as **Docker Images** and **run on ECS**
- <img alt="picture 20" src="image/30-Other-Services/8-AWS-Batch.png" width="800" />  
- example
  - <img alt="picture 21" src="image/30-Other-Services/8-AWS-Batcj.png" width="800" />  
- Batch vs Lambda
  - Lambda (time limit, serverless, limited runtimes, disk space)
  - Batch (no time limit, any runtime, rely on EBS, and EC2 (not serverless))
  - <img alt="picture 22" src="image/30-Other-Services/8-AWS-Batch-vs-Lambda.png" width="800" />  


# Amazon AppFlow
- fully managed, securely transfer data between
  - SaaS (Software as a Service) application
  - and AWS
- <img alt="picture 23" src="image/30-Other-Services/9-AppFlow.png" width="800" />  
- <img alt="picture 24" src="image/30-Other-Services/9-AppFlow-2.png" width="800" />  