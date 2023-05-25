
- [AWS Organizations](#aws-organizations)


# AWS Organizations
- to manage mulitple accounts
- <img alt="picture 1" src="image/25-IAM-Advanced/1-AWS-Organizations.png" width="800" />  
- <img alt="picture 2" src="image/25-IAM-Advanced/1-AWS-Organization-arch.png" width="800" />  
- <img alt="picture 3" src="image/25-IAM-Advanced/1-AWS-Organization-Examples.png" width="800" />  
- <img alt="picture 4" src="image/25-IAM-Advanced/1-AWS-Organizations-Advantages.png" width="800" />  
- <img alt="picture 5" src="image/25-IAM-Advanced/1-AWS-Organizations-SCP.png" width="800" />  
- <img alt="picture 6" src="image/25-IAM-Advanced/1-AWS-Organizations-SCP-Examples.png" width="800" />  
- <img alt="picture 7" src="image/25-IAM-Advanced/1-AWS-Organizations-Policies.png" width="800" />  


# IAM - Advanced Polices

- IAM Conditions
  - <img alt="picture 8" src="image/25-IAM-Advanced/2-IAM-Conditions-Examples.png" width="800" />  

- Resource Policies & aws:PrincipalOrgID
  - <img alt="picture 9" src="image/25-IAM-Advanced/2-IAM-Policies-By-Organization-ID.png" width="800" />  



# IAM - Resource-based Policies vs IAM Roles
- 2 way to apply policies
  - <img alt="picture 10" src="image/25-IAM-Advanced/3-Roles-vs-Resource-Polices.png" width="800" />  
  - <img alt="picture 11" src="image/25-IAM-Advanced/3-Roles-vs-Resource-Policies-1.png" width="800" />  
- EventBridge - Security
  - Resource-based policy: Lambda, SNS, SQS, CloudWatch Logs, API Gateway...
  - IAM Role: Kinesis Stream, Systems Manager Run Command, ECS task...
  - <img alt="picture 12" src="image/25-IAM-Advanced/3-Role-vs-Resource-Policy.png" width="800" />  


# IAM - Policy Evaluation Logic
- IAM Permission Boundaries
  - <img alt="picture 13" src="image/25-IAM-Advanced/4-Policy-Evaluation-Permission-Boundaries.png" width="800" />  
- Example: 
  - <img alt="picture 14" src="image/25-IAM-Advanced/4-Permission-Boundaries-Examples.png" width="800" />  
  - User `john`:
    - Permission policies: `AdministratorAccess` -> can access all
    - Permission boundary: `AmazonS3FullAccess` -> s3 full access
    - -> He can access only S3 (intersection of 2 set above)
- IAM Policy Evaluation Logic
  - <img alt="picture 15" src="image/25-IAM-Advanced/4-IAM-Policy-Evaluation-Logic.png" width="800" />  
- Example:
  - 3 questions -> Answers: **NO**
  - <img alt="picture 16" src="image/25-IAM-Advanced/4-Policy-Examples.png" width="800" />  


# IAM Identity Center
- successor to AWS Single Sign-On
  - <img alt="picture 17" src="image/25-IAM-Advanced/5-Identity-Center.png" width="800" />  
- Login Flow
  - <img alt="picture 18" src="image/25-IAM-Advanced/5-Identity-Center-Login-Flow.png" width="800" />  
  - <img alt="picture 19" src="image/25-IAM-Advanced/5-Identity-Center-Login-Flow-2.png" width="800" />  
- Permission Set
  - <img alt="picture 20" src="image/25-IAM-Advanced/5-Identity-Center-Permission-Set.png" width="800" />  
- Fine-grained Permissions and Assignments
  - <img alt="picture 21" src="image/25-IAM-Advanced/5-Identity-Center-Fine-grained.png" width="800" />  


# AWS Directory Services
- **Active Directory (AD)**: Centralized security management, create account, assign permissions...
  - <img alt="picture 22" src="image/25-IAM-Advanced/6-Microsoft-Active-Directory.png" width="800" />  

- AWS Directory Services
  - <img alt="picture 23" src="image/25-IAM-Advanced/6-Directory-Services.png" width="800" />  
  - AWS Managed Microsoft AD: 2 direction query
  - AD Connector: only on premise AD using connector
  - Simple AD: use only AWS (on EC2 instance)

- AD setup
  - <img alt="picture 24" src="image/25-IAM-Advanced/6-Active-Directory-Setup.png" width="800" />  


# AWS Control Tower
- Overview
  - <img alt="picture 25" src="image/25-IAM-Advanced/7-AWS-Control-Tower.png" width="800" />  
- Guardrails
  - <img alt="picture 26" src="image/25-IAM-Advanced/7-Guardrails.png" width="800" />  


# Quiz
- You have strong regulatory requirements to only allow fully internally audited AWS services in production. You still want to allow your teams to experiment in a development environment while services are being audited. How can you best set this up?
  - Create an **AWS Organization** and create 2 Prod and Dev **OUs**, then Apply an **SCP(Service Control Provider)** on the Prod **OU**


- You are managing the AWS account for your company, and you want to give one of the developers access to read files from an S3 bucket. You have updated the bucket policy to this, but he still can't access the files in the bucket. What is the problem?
    ```
    {

        "Version": "2012-10-17",

        "Statement": [{

            "Sid": "AllowsRead",

            "Effect": "Allow",

            "Principal": {

                "AWS": "arn:aws:iam::123456789012:user/Dave"

            },

            "Action": "s3:GetObject",

            "Resource": "arn:aws:s3:::static-files-bucket-xxx"

        }]

    }
    ```
    - You should change the resource to `arn:aws:s3:::static-files-bucket-xxx/*`, because this is an **object-level permission**


- You have 5 AWS Accounts that you manage using AWS Organizations. You want to restrict access to certain AWS services in each account. How should you do that?
  - Using **AWS Organization SCP**


- Which of the following IAM condition key you can use only to allow API calls from a specified AWS region?
    - <img alt="picture 27" src="image/25-IAM-Advanced/8-Quiz-question-4.png" />  


- When configuring permissions for EventBridge to configure a Lambda function as a target you should use ………………….. but when you want to configure a Kinesis Data Streams as a target you should use …………………..
    - <img alt="picture 28" src="image/25-IAM-Advanced/8-Quiz-question-5.png" width="800" />  
    - Resource-based policy: Lambda, SNS, SQS, CloudWatch Logs, API Gateway...
    - IAM Role: Kinesis Stream, Systems Manager Run Command, ECS task...
