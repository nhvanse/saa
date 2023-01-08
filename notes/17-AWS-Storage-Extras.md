# AWS Snow Family

- High secure portable devices to collect and process data at the edge and migrate data into and out of AWS
- Data migration: Snowcone, SnowBall, SnowMobile
- Edge computing: SnowCone, Snowball Edge

# Data migration with AWS Snow family

- Challenges when you transfer data over the network:
  - Limited conectivity
  - Limited bandwidth
  - High network cost
  - Shared bandwidth (can NOT maximize the line)
  - Connection stability
- AWS Snow Family: offline devices to perform data migrations
- If it take more than a week to transfer over the network, use Snowball device
- ![img](image/17-AWS-Storage-Extras/1673141643829.png)

# Solution Achitecture: Snowball into Glacier

![img](image/17-AWS-Storage-Extras/1673190981466.png)

# Amazon FSx

- Launch 3rd party high performance file systems on AWS
- Fully managed service
  - FSx for Lustre
    - is a type of parallel distributed file system, for large scale computing
    - Lustre = Linux + Cluster
    - Options:
      - Scratch File System: temporary, not replicated, high burst, short-term, optimize costs
      - Persistent File System: long-term, replicated within same AZ, replace failed files with minutes, sensitive data
  - FSx for NetApp ONTAP
    - Managed NetApp ONTAP on AWS
    - **supports NFS, SMB, iSCSI protocol**
    - Works with linux, windows, macos, vmware cloud on aws, amz workspace and appstream 2.0, EC2, ECS, EKS
    - **Point in time instantaneous cloning( helpful for testing new workloads)**
  - FSx for Windows File Server
    - support SMB protocol and Windows NTFS
    - **can be mounted on Linux EC2 instances**
    - supports **Microsoft's Distributed File System (DFS) Namespaces** (group files across multiple FS)
  - FSx for OpenZFS
    - Managed OpenZFS file system on AWS
    - supports NFS v3, v4, v4.1, v4.1
    - works with linux, windows, macos, vmware cloud, amz workspace, appstream 2.0, ec2, ecs, eks
    - **Point in time instantaneous cloning( helpful for testing new workloads)**
- 

# Storage gateway

- combine on-premises and cloud storage

  - ![img](image/17-AWS-Storage-Extras/1673196421064.png)
  - ![1673196475515](image/17-AWS-Storage-Extras/1673196475515.png)
  - ![1673196545944](image/17-AWS-Storage-Extras/1673196545944.png)
- types:

  - S3 File gateway
    - ![img](blob:https://web.telegram.org/d8e55873-8273-4491-b419-a0f3e95b8340)![1673196720006](image/17-AWS-Storage-Extras/1673196720006.png)
  - FSx File gateway
    - ![1673196741587](image/17-AWS-Storage-Extras/1673196741587.png)
  - Volume gateway
    - ![1673196825867](image/17-AWS-Storage-Extras/1673196825867.png)
  - Tape gateway
    - ![1673196843903](image/17-AWS-Storage-Extras/1673196843903.png)
- Storage gateway - Hardware appliance

  ![1673197171332](image/17-AWS-Storage-Extras/1673197171332.png)
- Summary
- ![1673197171332](https://file+.vscode-resource.vscode-cdn.net/Users/van/Desktop/1_LEARN/aws/saa/notes/image/17-AWS-Storage-Extras/1673197171332.png)



# AWS Transfer Family

![1673197634392](image/17-AWS-Storage-Extras/1673197634392.png)

![1673197667188](image/17-AWS-Storage-Extras/1673197667188.png)


# Data Sync

- sync data between on-premises and AWS, or between AWS services
- ![1673198026170](image/17-AWS-Storage-Extras/1673198026170.png)
- ![1673198045839](image/17-AWS-Storage-Extras/1673198045839.png)
- ![1673198062524](image/17-AWS-Storage-Extras/1673198062524.png)


# All AWS storage options compared

![1673198492177](image/17-AWS-Storage-Extras/1673198492177.png)
