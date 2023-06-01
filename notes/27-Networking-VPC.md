- [VPC Overview](#vpc-overview)
- [CIDR, Private vs Public IP](#cidr-private-vs-public-ip)
- [Deault VPC Oveview](#deault-vpc-oveview)
- [VPC Overview](#vpc-overview-1)
- [Subnet Overview](#subnet-overview)
- [Internet Gateway and Route Tables](#internet-gateway-and-route-tables)
- [Bastion Host](#bastion-host)
- [NAT Instance (Oudated, but still at the exam)](#nat-instance-oudated-but-still-at-the-exam)
- [NAT Gateways](#nat-gateways)
- [NACL and Security Groups](#nacl-and-security-groups)
- [VPC Peering](#vpc-peering)
- [VPC Endpoints](#vpc-endpoints)
- [VPC Flow Logs](#vpc-flow-logs)
- [Site to Site VPN, Virtual Private Gateway and Customer Gateway](#site-to-site-vpn-virtual-private-gateway-and-customer-gateway)
- [Direct Connect (DX)](#direct-connect-dx)
- [Direct Connect + Site to Site VPN](#direct-connect--site-to-site-vpn)
- [Transit Gateway](#transit-gateway)
- [VPC Traffic Mirroring](#vpc-traffic-mirroring)
- [IPv6 for VPC](#ipv6-for-vpc)
- [Egress-only Internet Gateway](#egress-only-internet-gateway)
- [VPC Summary](#vpc-summary)
- [Networking costs **per GB**](#networking-costs-per-gb)
- [AWS Network Firewall](#aws-network-firewall)



# VPC Overview
- <img alt="picture 1" src="image/27-Networking-VPC/1-VPC-Overview.png" width="800" />  
- take cost: NAT Gateway,..


# CIDR, Private vs Public IP
- CIDR
  - **Classless Inter-Domain Routing**
  - <img alt="picture 2" src="image/27-Networking-VPC/2-CIDR-1.png" width="800" />  
  - Components: Base IP and Subnet Mask
  - <img alt="picture 3" src="image/27-Networking-VPC/2-CIDR-Components.png" width="800" />
  - Subnet Mask
  - <img alt="picture 4" src="image/27-Networking-VPC/2-CIDR-Subnet-Mask.png" width="800" />  
  - 192.268.0.0/24 = 192.168.0.255
- Public vs. Private IP (IPv4)
  - <img alt="picture 5" src="image/27-Networking-VPC/2-Public-vs-Private-IP.png" width="800" />  


# Deault VPC Oveview
- <img alt="picture 6" src="image/27-Networking-VPC/3-Default-VPC.png" width="800" />  
- 1 subnet -> 1 availability zone
- has route tables, subnets,...


# VPC Overview
- VPC = Virtual Private Cloud
- <img alt="picture 7" src="image/27-Networking-VPC/4-VPC-Overview.png" width="800" />  
- Hands on
  - Create VPC 
    - IPv4 CIDR block
    - IPv6 -> Optional


# Subnet Overview
- <img alt="picture 8" src="image/27-Networking-VPC/5-Subnet-Overview.png" width="800" />  
- VPC Subnet IPv4
  - 5 IP in range can bot used for EC2
  - <img alt="picture 9" src="image/27-Networking-VPC/5-Subnet-IP-Range.png" width="800" />  


# Internet Gateway and Route Tables
- Internet Gateway (IGW)
  - <img alt="picture 10" src="image/27-Networking-VPC/6-Internet-Gateway.png" width="800" />
  - <img alt="picture 11" src="image/27-Networking-VPC/6-Internet-Gateway-2.png" width="800" />  
- Hands on:
  - Create VPC, create subnets
  - Edit a subnet, set auto assign public IP
  - Create an EC2 instance:
    - Choose VPC
    - Choose subnet
    - Enable ssh 
  - Try to ssh to the EC2 instance -> fail due to lack of internet connection to the instance
  - -> Create Internet Gateway
    - Choose VPC to attach
  - Try ssh -> fail again
  - -> Create Route Table
    - Choose VPC
    - Attach subnets to the route table in *subnet associations*
    - Edit the route in the public route table
      - any IPs route to IGW <img alt="picture 13" src="image/27-Networking-VPC/6-Internet-GateWay-Route-Table.png" width="800" />  
  - Try to ssh the instance -> ok
  - pin google.com -> ok
  - <img alt="picture 23" src="image/27-Networking-VPC/6-Internet-Gateway-Visualisation.png" width="800" />  



# Bastion Host
- Bridge to ssh to EC2 instances from the Internet
- <img alt="picture 14" src="image/27-Networking-VPC/7-Bastion-Host.png" width="800" />  
- Hands on:
  - Create new Key Pair and download
  - Create an EC2 instance
    - Choose VPC, choose private subnet
    - Choose key pair
    - Allow ssh from security group of Bastion instance that we created (can access bastion from internet)
  - ssh to the bastion instance
  - copy private ip address of the private instance
  - In Bastion:
    - Create a new .pem file and copy downloaded keypair to it
    - `chmod 0400 DemoKeyPair.pem`
    - `ssh ec2-user@{private-ip} -i DemoKeyPair.pem` -> OK
    - ping google.com -> NOT OK


# NAT Instance (Oudated, but still at the exam)
- NAT = Network Address Translation
- Allows EC2 instances in private subnets to connect to the Internet
- <img alt="picture 15" src="image/27-Networking-VPC/8-NAT-Instance.png" width="800" />  
- <img alt="picture 16" src="image/27-Networking-VPC/8-NAT-INstance-arch.png" width="800" />  
- Comments:
  - <img alt="picture 17" src="image/27-Networking-VPC/8-NAT-Instance-comments.png" width="800" />  
- Hands on
  - Create an EC2 instance
    - Image: ..nat..
    - choose vpc
    - add rule: allow HTTP and HTTPs from private subnet 
    - add 
  - Choose the EC2 instance and click edit network setting
  - Change source/destionation check
    - <img alt="picture 18" src="image/27-Networking-VPC/8-NAT-Instance-hands-on-1.png" width="800" />  
  - Add routes in the private subnet
    - Des: 0.0.0.0/0
    - target: NAT Instance
    - (If go to the internet, go through the NAT instance)
  - Add inbound rules of the NAT Instance
    - Type: All ICMP - IPv4
    - From: private subnet
  - You can ping goole.com from the Private EC2 Instance


# NAT Gateways
- <img alt="picture 19" src="image/27-Networking-VPC/9-NAT-Gateway.png" width="800" />  
- <img alt="picture 20" src="image/27-Networking-VPC/9-NAT-Gateway-arch.png" width="800" />  
- High avilability
  - single AZ
  - -> Multi NATGW in multiple AZs
  - <img alt="picture 21" src="image/27-Networking-VPC/9-NAT-Gateway-HA.png" width="800" />  
- Compare with NAT Instance
  - <img alt="picture 22" src="image/27-Networking-VPC/9-NAT-Gateway-Compare.png" width="800" />  
- Hands on:
  - VPC -> NATGateway -> Create
    - Choose subnet
    - Connect type: public/private
    - allocate Elastic IP
  - Edit Route table 
    - 0.0.0.0/0 -> the NAT Gateway
  - ping google.com -> OK


# NACL and Security Groups
- <img alt="picture 24" src="image/27-Networking-VPC/10-NACL-and-Security-Group.png" width="800" />  
- NACL = Network ACL 
  - **Stateless** -> outbound request need to be evaluated
  - control traffic to **subnets**
  - match rules with high score (precedence) first
  - <img alt="picture 25" src="image/27-Networking-VPC/10-NACL.png" width="800" /> 
  -  <img alt="picture 26" src="image/27-Networking-VPC/10-NACL-Diagram.png" width="800" />  
  -  Default NACL:
     -  accept everything in and out
     -  <img alt="picture 27" src="image/27-Networking-VPC/10-NACL-Default-NACL.png" width="800" />  
  - Ephemeral Ports (temp port)
    - clients open temp random ports to recieve responses from servers (servers send to these ports)
    - <img alt="picture 28" src="image/27-Networking-VPC/10-Ephemeral-Ports.png" width="800" />  
  - NACL with Ephemeral Ports
    - <img alt="picture 29" src="image/27-Networking-VPC/10-NACL-with-Ephemeral-Ports.png" width="800" />  

  - NACL rules for each target subnets CIDR
    - <img alt="picture 30" src="image/27-Networking-VPC/10-NACL-multi-subnets.png" width="800" />  

- Security Group
  - **Stateful** -> outbound request DONT need to be avaluated
  - Instance level

- Compare
  - <img alt="picture 31" src="image/27-Networking-VPC/10-NACL-vs-Security-Group-Comparision.png" width="800" />  



# VPC Peering
- can connect 2 VPC (different accounts or regions)
- must not have overlapping CIDRs
- A can not connect to C through B
- must update route tables in subnets
- <img alt="picture 32" src="image/27-Networking-VPC/11-VPC-Peering.png" width="800" />  
- <img alt="picture 33" src="image/27-Networking-VPC/11-VPC-Peering-2.png" width="800" />  
- <img alt="picture 34" src="image/27-Networking-VPC/11-VPC-Peering-Diagram.png" width="800" />  
- Hands on:
  - must be accept VPC Peering request (in my account or other account)
  - update route tables of subnets -> EC2 instance can connect to other VPCs

# VPC Endpoints
- default: DynomoDB, CloudWatch, S3 public to the Internet
- Use VPC Endpoint to prevent public -> connect through VPC endpoint
  - <img alt="picture 35" src="image/27-Networking-VPC/12-VPC-Endpoints.png" width="800" />  
- Compare
  - Option1: 
    - connect through NAT Gateway -> Internet Gateway
    - a lot of money because of NATGW, IGW 
  -  Option 2:
     -  Use VPC Endpoint 
     -  (using a private network)
     - <img alt="picture 36" src="image/27-Networking-VPC/12-VPC-Endpoints-2.png" width="800" />  

- 2 types of endpoints:
  - Interface Endpoints
    - cost
    - most AWS services
  - Gateway Endpoints:
    - free
    - only S3 and DynamoDB
    - preferred in the exam
  - <img alt="picture 37" src="image/27-Networking-VPC/12-VPC-Endpoints-Types.png" width="800" />  
  - <img alt="picture 38" src="image/27-Networking-VPC/12-VPC-Endpoints-Types-Compare.png" width="800" />  

- Hands on:
  - Create a role for the EC2 instance to have access to S3 (ReadOnly) (this instance can access internet through NATGateway and Internet Gateway)
  - ssh to EC2, run `aws s3 ls` -> ok
  - remove rows in route tables to prevent access to the Internet
  - run again -> NOT ok (can not connect)
  - Create VPC Endpoint from VPC to S3
  - run `aws s3 ls --region eu-central-1` (must be the region when create Endpoint - eu-central-1) -> OK


# VPC Flow Logs
- Overview
  - 3 kinds to capture info: **VPC Flow Logs**, Subnet Flow Logs, ENI Flow Logs
  - can send to S3, CloudWatch Logs, Kinesis Data Firehose
  - <img alt="picture 39" src="image/27-Networking-VPC/13-VPC-Flow-Logs-Overview.png" width="800" />  
- Logs Syntax
  - <img alt="picture 40" src="image/27-Networking-VPC/13-VPC-Flow-Logs-Syntax.png" width="800" />  
- Troubleshoot SG and NACL
  - <img alt="picture 41" src="image/27-Networking-VPC/13-VPC-Flow-Logs-Troubleshoot.png" width="800" />  
- Arch:
  - <img alt="picture 42" src="image/27-Networking-VPC/13-VPC-Flow-Logs-Architecture.png" width="800" />  

- Hands on
  - Create VPC Flow Logs
  - choose aggregation interval
  - choose destination: S3, CLoudwatch Logs, Kinesis in my account, Kinesis in another account
  - Default format or custom format
  - Use Athena to analyse logs from s3 (search VPC Flow Logs Athena on google)


# Site to Site VPN, Virtual Private Gateway and Customer Gateway
- connect to the company's Private Network through VPN
  - <img alt="picture 43" src="image/27-Networking-VPC/14-VPN-1.png" width="800" />  
- Site to Site VPN need to things:
  - Virtual Private Gateway (VGW)
  - Customer Gateway
  - <img alt="picture 44" src="image/27-Networking-VPC/14-VPN-2.png" width="800" />  
- Site to Site VPN Connections
  - **Important in the exam**
  - <img alt="picture 45" src="image/27-Networking-VPC/14-VPN-Connections.png" width="800" />  

- VPN CloudHub
    - <img alt="picture 46" src="image/27-Networking-VPC/14-VPN-CloudHub.png" width="800" />  

- Hands on:
  - Create CGW, VGW -> connect by  Site to Site VPN connection


# Direct Connect (DX)
- Direct Connect
  - <img alt="picture 47" src="image/27-Networking-VPC/15-Direct-Connect-Overview.png" width="800" />  
  - <img alt="picture 48" src="image/27-Networking-VPC/15-Direct-Connect-Diagram.png" width="800" />  

- Direct Connect Gateway
  - connect more VPC in many regions -> use DXG
  - <img alt="picture 49" src="image/27-Networking-VPC/15-Direct-Connect-Gateway.png" width="800" />  
- Direct-Connect - Connection types
  -  If want to transfer some data **within a week** (and want to fast), the answer is not Direct Connect. Because it take about **1 month to establish**
  -  <img alt="picture 50" src="image/27-Networking-VPC/15-Direct-Connect-Connection-types.png" width="800" />  

- Encryption
  - <img alt="picture 51" src="image/27-Networking-VPC/15-Direct-Connect-Encryption.png" width="800" />  

- Resiliency
  - <img alt="picture 52" src="image/27-Networking-VPC/15-Direct-Connect-Resiliency.png" width="800" />  


# Direct Connect + Site to Site VPN
- <img alt="picture 53" src="image/27-Networking-VPC/16-Direct-Connect-with-Site-to-Site-VPN.png" width="800" />  


# Transit Gateway
- network topologies can become complicated
  - <img alt="picture 54" src="image/27-Networking-VPC/17-Transit-Gateway-1.png" width="800" />  

- -> use transit gateway
  - merge them -> star connection
  - IP Multicast -> only Transit Gateway
  - <img alt="picture 55" src="image/27-Networking-VPC/17-Transite-Gateway-Overview.png" width="800" />  

- another use case: increase the bandwidth of your site-to-site VPN connection
  - using ECMP (Equal-cost multi-path routing)
  - <img alt="picture 56" src="image/27-Networking-VPC/17-Transit-Gateway-with-ECMP.png" width="800" />  
  - <img alt="picture 57" src="image/27-Networking-VPC/17-Transit-Gateway-ECMP-bandwidth-comparison.png" width="800" />  

- Share Direct Connect between multiple accounts
  - <img alt="picture 58" src="image/27-Networking-VPC/17-Transit-Gateway-multiple-accounts.png" width="800" />  


# VPC Traffic Mirroring
- <img alt="picture 59" src="image/27-Networking-VPC/18-VPC-Traffic-Mirroring.png" width="800" />  


# IPv6 for VPC
- <img alt="picture 60" src="image/27-Networking-VPC/19-IPv6.png" width="800" />  
- <img alt="picture 61" src="image/27-Networking-VPC/19-IPv6-in-VPC.png" width="800" />  
- IPv6 Troubleshooting
  - Can NOT launch EC2 instance in your subnet -> no available Ipv4 in the subnet
  - -> Create a new Ipv4 CIDR in the subnet
  - <img alt="picture 62" src="image/27-Networking-VPC/19-IPv6-Troubleshooting.png" width="800" />  
- Hands on
  - Edit CIDR of the VPC, add new Ipv6 CIDR
  - Edit subnet's IPv6 CIDR
  - Edit subnet settings, allow auto-assign IPv6 address (always public)
  - Assign new IPv6 for  old ec2 instances
  - Update Security Group, allow SSH from all IPv6



# Egress-only Internet Gateway
- Overview
  - only v6
  - only outbound, not inbound
  - must update route tables
  - <img alt="picture 63" src="image/27-Networking-VPC/20-Egress-only-Internet-Gateway.png" width="800" />  
- Routing
  - <img alt="picture 64" src="image/27-Networking-VPC/20-Ipv6-Routing.png" width="800" />  
- Hands on
  - Create 
    - choose vpc
    - edit route table ::/0 -> egress IGW
    - try ping google.com from ec2 instance in private network


# VPC Summary
- <img alt="picture 65" src="image/27-Networking-VPC/21-VPC-Summary.png" width="800" />  
- <img alt="picture 66" src="image/27-Networking-VPC/21-VPC-Summary-2.png" width="800" />  
- <img alt="picture 67" src="image/27-Networking-VPC/21-VPC-Summary-3.png" width="800" />  


# Networking costs **per GB**
- Prefer private IP, prefer same AZ
  - <img alt="picture 68" src="image/27-Networking-VPC/28-Cost-1.png" width="800" />  

- minimize egress(outbound) traffic
  - <img alt="picture 69" src="image/27-Networking-VPC/28-Cost-2.png" width="800" />  
 
- S3 Data Transfer Pricing - Analysis for USA
  - Using CloudFront is 7x cheaper than S3 only
  - <img alt="picture 71" src="image/27-Networking-VPC/28-Cost-3.png" width="800" />  

- NATGW vs GW VPC Endpoint
  - prefer VPC Endpoint if using S3
  - <img alt="picture 72" src="image/27-Networking-VPC/28-Cost-4.png" width="800" />  


# AWS Network Firewall
- Network Protection on AWS
  - <img alt="picture 73" src="image/27-Networking-VPC/28-Network-Protection.png" width="800" /> 
   
- Want to protect in a sophisticated way our entire VPC?
  - -> User AWS Network Firewall
  - <img alt="picture 74" src="image/27-Networking-VPC/28-Network-Firewall.png" width="800" />  

- Fine Grained Controls
  - <img alt="picture 75" src="image/27-Networking-VPC/28-Fine-Grained-Controls.png" width="800" />  

