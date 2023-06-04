
- [Overview](#overview)


# Overview
- very important
- [paper link](../udemy/disaster-recovery-workloads-on-aws.pdf)
- Overview
  - <img alt="picture 1" src="image/28-Disaster-Recovery/1-DR-Overview.png" width="800" />  
- RPO and RTO
  - RPO: Recovery Point Objective - backup point
  - RTO: Recovery Time Objective - recovery point
  - optimize Data Loss and Downtime
  - <img alt="picture 2" src="image/28-Disaster-Recovery/1-RPO-and-RTO.png" width="800" />  
- Disaster Recovery Strategies
  - <img alt="picture 3" src="image/28-Disaster-Recovery/2-Strategies.png" width="800" />  
  - Backup and Restore (high RPO)
    - cheap
    - high RPO and RTO: ex: create Snowball to AWS 1 time per week, or create snapshot ~ 24h...
    - <img alt="picture 4" src="image/28-Disaster-Recovery/1-Backup-And-Restore.png" width="800" />  

  - Pilot Light
    - Popular choice
    - ONLY for critical core assistance
    - lower RTO and RPO
    - also cheap (focus on running RDS)
    - <img alt="picture 5" src="image/28-Disaster-Recovery/1-Pilot-Light.png" width="800" />  
  - Warm Standby
    - lower RTO and RPO
    - minimum size
    - more expensive (run EC2 and RDS)
    - <img alt="picture 6" src="image/28-Disaster-Recovery/1-Warm-StandBy.png" width="800" />  
  - Multi Site / Hot Site Approach
    - Very low RTO (minutes or seconds) - very expensive
    - full production size
    - <img alt="picture 7" src="image/28-Disaster-Recovery/1-Multi-Site-Hot-Site.png" width="800" />  
  - AWS Multi Region
    - <img alt="picture 8" src="image/28-Disaster-Recovery/1-All-AWS-Multi-Region.png" width="800" />  
- Disaster Recovery Tips
  - <img alt="picture 9" src="image/28-Disaster-Recovery/1-Tips.png" width="800" />  


# Database Migration Service (DMS)
- Overview
  - Note: CDC - Change Data Capture
  - Must create EC2 instance and run DMS on it
  - <img alt="picture 10" src="image/28-Disaster-Recovery/2-DMS.png" width="800" />  
  - <img alt="picture 11" src="image/28-Disaster-Recovery/2-DMS-2.png" width="800" />  
- SCT
  - ~ Schema Conversion Tool
  - <img alt="picture 12" src="image/28-Disaster-Recovery/2-SCT.png" width="800" />  
- Continuous Replication
  - <img alt="picture 13" src="image/28-Disaster-Recovery/2-Continuous-Replication.png" width="800" />  
  - <img alt="picture 14" src="image/28-Disaster-Recovery/2-Multi-AZ-Deployment.png" width="800" />  
  - (choose option Multi AZ)

- Hands on:
  - Acccess Service DMS
  - Create Replication instances
    - Name, instance class, engine version, VPC, MultiAZ option, publicly accessible,...
  - Create target and source DB Endpoints
    - engine, server, port, username, password, KMS,...
  - Create Database Migration Tasks
    - Name, choose instance, source and target DB Endpoints, migration type (existing data, existing data and ongoing changes, data changes only), ....


# RDS and Aurora Migrations
- <img alt="picture 15" src="image/28-Disaster-Recovery/3-MySQL-Migrations.png" width="800" />  
- <img alt="picture 16" src="image/28-Disaster-Recovery/3-Postgres-Migrations.png" width="800" />  


# On-Premise strategy with AWS
- <img alt="picture 17" src="image/28-Disaster-Recovery/4-On-Premise-strategy.png" width="800" />  


# AWS Backup
- <img alt="picture 18" src="image/28-Disaster-Recovery/5-AWS-Backup.png" width="800" />  
- PITR: Point in time recovery
- <img alt="picture 19" src="image/28-Disaster-Recovery/5-AWS-Backup-2.png" width="800" />  
- <img alt="picture 20" src="image/28-Disaster-Recovery/AWS-Backup-3.png" width="800" />  
- Vault Lock
- <img alt="picture 21" src="image/28-Disaster-Recovery/5-AWS-Backup-4.png" width="800" />  

- Hands on
  - Create backup plan
  - Assign Resources (use automatic role or existing IAM role)
    - can specify tags to filter resources
    - 

# Application Migration Service (MGN)
- AWS Application Discovery Service
  - <img alt="picture 22" src="image/28-Disaster-Recovery/6-Application-Discovery-Service.png" width="800" />  
- Application Migration Service
  - <img alt="picture 23" src="image/28-Disaster-Recovery/6-Application-Migration-Service.png" width="800" />  


# Transfering Large Datasets into AWS
- <img alt="picture 24" src="image/28-Disaster-Recovery/7-Transfer-Datasets.png" width="800" />  


# VMWare Cloud on AWS
- <img alt="picture 25" src="image/28-Disaster-Recovery/8-VMWare-Cloud.png" width="800" />  


# Quiz

1. As part of your Disaster Recovery plan, you would like to have only the critical infrastructure up and running in AWS. You don't mind a longer Recovery Time Objective (RTO). Which DR strategy do you recommend?
   1. <img alt="picture 26" src="image/28-Disaster-Recovery/9-Quiz-1.png" width="800" />  
2. DR
   1. <img alt="picture 27" src="image/28-Disaster-Recovery/9-Quiz-2.png" width="800" />  
3. Backup and Restore
   1. <img alt="picture 28" src="image/28-Disaster-Recovery/9-Quiz-3.png" width="800" />  
4. Warm StandBy
   1. <img alt="picture 29" src="image/28-Disaster-Recovery/9-Quiz-4.png" width="800" />  
5. Migrate Oracle
   1. <img alt="picture 30" src="image/28-Disaster-Recovery/9-Quiz-5.png" width="800" />  
6. DataSync
   1. <img alt="picture 31" src="image/28-Disaster-Recovery/9-Quiz-6.png" width="800" />  
7. AWS backup
   1. <img alt="picture 32" src="image/28-Disaster-Recovery/9-Quiz-7.png" width="800" />  
8. Application Migration Service
   1. <img alt="picture 33" src="image/28-Disaster-Recovery/9-Quiz-8.png" width="800" />  
9. VMWare
   1.  <img alt="picture 34" src="image/28-Disaster-Recovery/9-Quiz-9.png" width="800" />  
10. RDS Migration
    1.  <img alt="picture 35" src="image/28-Disaster-Recovery/9-Quiz-10.png" width="800" />  
11. AWS Backup
    1.  <img alt="picture 36" src="image/28-Disaster-Recovery/9-Quiz-11.png" width="800" />  


