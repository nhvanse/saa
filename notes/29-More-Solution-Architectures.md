- [Event Processing in AWS](#event-processing-in-aws)
- [Caching Strategies](#caching-strategies)
- [Blocking an IP Address in AWS](#blocking-an-ip-address-in-aws)
- [High Performance Computing HPC on AWS](#high-performance-computing-hpc-on-aws)
- [EC2 Instance High Availability](#ec2-instance-high-availability)
- [Quiz](#quiz)



# Event Processing in AWS
- Event SQS, SNS, Lambda
  - DLQ: Dead Letter Queue -> to send messages OFF to SQS queue
  - <img alt="picture 1" src="image/29-More-Solution-Architectures/1-Event-SQS-Lambda-SNS.png" width="800" />  
- Fan out Pattern
  - Option 1 not reliable
  - Fan out: higher guarantee
  - <img alt="picture 2" src="image/29-More-Solution-Architectures/1-Event-Fan-Out-Pattern.png" width="800" />  
- S3 Event Notification
  - use case: generate thumbnails
  - <img alt="picture 3" src="image/29-More-Solution-Architectures/1-Event-S3-Notification.png" width="800" />  
- S3 Event Notification with EventBridge
  - <img alt="picture 4" src="image/29-More-Solution-Architectures/Event-S3-with-EventBridge.png" width="800" />  
- EventBridge Intercept API Calls
  - <img alt="picture 5" src="image/29-More-Solution-Architectures/1-Event-EventBridge-Intercept-API-Calls.png" width="800" />  
- API Gateway with Kinesis Streams
  - <img alt="picture 6" src="image/29-More-Solution-Architectures/1-Event-API-Gateway-Kinesis-Streams.png" width="800" />  



# Caching Strategies
- Caching
  - CloudFront: Need to setup TTL to often renew data, prevent outdated data
  - API Gateway: a Regional Service
  - Cache in Redis, Memcached, DAX
  - Flexible to choose 1 or some ways (depend on the scenarios)
  - <img alt="picture 7" src="image/29-More-Solution-Architectures/2-Caching.png" width="800" />  



# Blocking an IP Address in AWS
- Block an IP Address
  - NACL: Can create deny rule in NACL (VPC level)
  - Security Group: NOT very helpful in this situation
  - can run optional firewall software on EC2
  - <img alt="picture 8" src="image/29-More-Solution-Architectures/2-Block-an-IP-Address.png" width="800" />  
- With ALB
  - connection termination
  - EC2 can only see ALB's IP
  - <img alt="picture 9" src="image/29-More-Solution-Architectures/2-Block-IP-with-ALB.png" width="800" />  

- With NLB
  - **NO security group** on NLB, traffics can pass through and EC2 can see the Client's IPs
  - <img alt="picture 10" src="image/29-More-Solution-Architectures/2-Block-IP-with-NLB.png" width="800" />  

- With ALB and WAF
  - more expensive
  - WAF - a service we can install to the ALB , create bunch of rules
  - <img alt="picture 11" src="image/29-More-Solution-Architectures/2-Block-IP-with-ALB-and-WAF.png" width="800" />  

- ALB and CloudFront AWF
  - ALB can NOT see client's IPs
  - NACL is not helpful -> can NOT block IP
  - Can use CloudFront Geo Restriction to block IPs from a country
  - Block 1 IP -> use WAF into CloudFront
  - <img alt="picture 12" src="image/29-More-Solution-Architectures/2-Block-IP-ALB-and-CloudFront-WAF.png" width="800" />  


# High Performance Computing HPC on AWS
- HPC
  - common in the exam
  - create a lot of resources, pay only for what you used
  - <img alt="picture 13" src="image/29-More-Solution-Architectures/3-HPC-1.png" width="800" />  
- Services help perform HPC?
  - 1 **Data Management and Transfer**
    - Direct Connect
    - Snowball and Snowmobile
    - DataSync
    - <img alt="picture 14" src="image/29-More-Solution-Architectures/3-HPC-Data-Management-and-Transfer.png" width="800" />  
  
  - 2 **Compute and Networking**
    - EC2 Intances
    - EC2 Placement Groups -> Cluster for good  network performance
    - <img alt="picture 15" src="image/29-More-Solution-Architectures/3-HPC-Compute-EC2.png" width="800" />  
    - EC2 Enhanced Networking (SR-IOV)
      - Option 1: **Elastic Network Adapter** (**ENA**) upto 100Gbps
      - Option 2: Intel 82599 VF upto 10Gbps - LEGACY
      - -> Enhance network: low latency, higher packet per second, higher bandwidth
    - using **Elastic Fabric Adapter (EFA)**
      - only for Linux
      - improved ENA for HPC
      - <img alt="picture 16" src="image/29-More-Solution-Architectures/3-HPC-ENA-and-EFA.png" width="800" />  
  
  - 3 **Storage**
    - EBS
    - Instance Store
    - S3
    - EFS
    - Fsx for Lustre
    - <img alt="picture 17" src="image/29-More-Solution-Architectures/3-HPC-Storage.png" width="800" />  

  - 4 **Automation and Orchestration**
    - AWS Batch
    - AWS ParallelCluster
    - <img alt="picture 18" src="image/29-More-Solution-Architectures/3-HPC-Automation-and-Orchestration.png" width="800" />  



# EC2 Instance High Availability
- Create a highly available EC2 instance
  - <img alt="picture 19" src="image/29-More-Solution-Architectures/4-EC2-Available.png" width="800" />  
- With ASG
  - EC2 instance **role** to Allow API calls to attach The Elastic IP
  - <img alt="picture 20" src="image/29-More-Solution-Architectures/4-EC2-With-ASG.png" width="800" />  
- With ASG and EBS
  - ASG -> LifeCycle Hook -> create Snapshot -> restore
  - <img alt="picture 21" src="image/29-More-Solution-Architectures/4-EC2-with-ASG-EBS.png" width="800" /> 



# Quiz
- 1
  - <img alt="picture 22" src="image/29-More-Solution-Architectures/5-Quiz-1.png" width="800" />  
- 2
  - <img alt="picture 23" src="image/29-More-Solution-Architectures/5-Quiz-2.png" width="800" />  

- 3
  - <img alt="picture 24" src="image/29-More-Solution-Architectures/5-Quiz-3.png" width="800" />  


