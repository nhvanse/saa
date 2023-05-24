- [Athena](#athena)
- [Redshift](#redshift)
- [OpenSearch](#opensearch)
- [EMR](#emr)
- [QuickSight](#quicksight)
- [Glue](#glue)
- [AWS Lake Formation](#aws-lake-formation)
- [Kinesis Data Analytics](#kinesis-data-analytics)
      - [Kinesis Data Analytics for SQL applications](#kinesis-data-analytics-for-sql-applications)
      - [Kinesis Data Analytics for Apache Flink](#kinesis-data-analytics-for-apache-flink)
- [MSK - Managed Streaming for Apache Kafka](#msk---managed-streaming-for-apache-kafka)
- [Big Data Ingestion Pipeline](#big-data-ingestion-pipeline)
- [Quiz](#quiz)



# Athena
- serverless query service to analyze S3 using SQL
- ![picture 1](image/22-Data-And-Analytics/1-Athena.png)  
- ![picture 2](image/22-Data-And-Analytics/1-Athena-improvement.png)  
- ![picture 3](image/22-Data-And-Analytics/1-Athena-Federated-Query.png)  


# Redshift
- for analytic purpose
- ![picture 4](image/22-Data-And-Analytics/2-Redshift-overview.png)  
- ![picture 5](image/22-Data-And-Analytics/2-Redshift-Cluster.png)  
- ![picture 6](image/22-Data-And-Analytics/2-Reddshift-snapshot.png)  
- ![picture 7](image/22-Data-And-Analytics/2-Redshift-load-data.png)
- <img alt="picture 10" src="image/22-Data-And-Analytics/2-Redshift-Spectrum.png" width="800" />  


# OpenSearch 
- (based on ElasticSearch)
- Overview
- <img alt="picture 11" src="image/22-Data-And-Analytics/3-OpenSearch-Overview.png" width="800" />  
- Patterns DynamoDB
- <img alt="picture 12" src="image/22-Data-And-Analytics/3-OpenSearch-patterns.png" width="800" />  
- Patterns CloudWatch
- <img alt="picture 13" src="image/22-Data-And-Analytics/3-OpenSearch-patterns-2.png" width="800" />  
- Patterns Kinesis
- <img alt="picture 14" src="image/22-Data-And-Analytics/3-OpenSearch-patterns-3.png" width="800" />  


# EMR
- Elastic MapReduce
- <img alt="picture 15" src="image/22-Data-And-Analytics/4-EMR.png" width="800" />  
- Node types and purchasing
- <img alt="picture 16" src="image/22-Data-And-Analytics/4-EMR-node-types.png" width="800" />  


# QuickSight
- to create dashboard
- <img alt="picture 17" src="image/22-Data-And-Analytics/5-QuickSight.png" width="800" />  
- Intergrations
- <img alt="picture 18" src="image/22-Data-And-Analytics/5-QuickSight-intergrations.png" width="800" />  
- dashboard and analysis
- <img alt="picture 19" src="image/22-Data-And-Analytics/5-QuickSight-dashboard-analysis.png" width="800" />  


# Glue
- ETL service
- Severless
- <img alt="picture 20" src="image/22-Data-And-Analytics/6-Glue.png" width="800" />  
- Covert data into Parquet format (can replace Lambda with Event Bridge)
- <img alt="picture 21" src="image/22-Data-And-Analytics/6-Glue-convert-data.png" width="800" />  
- Glue Data Catalog
- <img alt="picture 22" src="image/22-Data-And-Analytics/6-Glue-data-catalog.png" width="800" />  
- Things to know
- <img alt="picture 23" src="image/22-Data-And-Analytics/6-Glue-services.png" width="800" />  


# AWS Lake Formation
- Data Lake
- <img alt="picture 24" src="image/22-Data-And-Analytics/7-Lake-Formation.png" width="800" />  
- <img alt="picture 25" src="image/22-Data-And-Analytics/7-Lake-Formation-arch.png" width="800" />  
- Advantage: manage securities all at one
- <img alt="picture 26" src="image/22-Data-And-Analytics/7-Lake-Formation-manage-all-in-one.png" width="800" />  


# Kinesis Data Analytics
#### Kinesis Data Analytics for SQL applications
- <img alt="picture 27" src="image/22-Data-And-Analytics/8-Kinesis-Data-Analytics-for-SQL-app.png" width="800" />  
- <img alt="picture 28" src="image/22-Data-And-Analytics/8-Kinesis-Data-Analytics-SQL-app-advantages.png" width="800" />  

#### Kinesis Data Analytics for Apache Flink
- <img alt="picture 29" src="image/22-Data-And-Analytics/8-Kinesis-Data-Analytics-for-Apache-Flink.png" width="800" />  


# MSK - Managed Streaming for Apache Kafka
- <img alt="picture 30" src="image/22-Data-And-Analytics/9-MSK.png" width="800" />  
- <img alt="picture 31" src="image/22-Data-And-Analytics/9-MSK-Apache-Kafka.png" width="800" />  
- Compare Kinesis vs MSK
- <img alt="picture 32" src="image/22-Data-And-Analytics/9-MSK-vs-Kinesis-Data-Stream.png" width="800" />  
- MSK Consumers
- <img alt="picture 33" src="image/22-Data-And-Analytics/9-MSK-Consumers.png" width="800" />  


# Big Data Ingestion Pipeline
- fully serverless, colect realtime, transform, query using SQL, create report, load to a warehouse, create dashboard
- <img alt="picture 34" src="image/22-Data-And-Analytics/10-Big-Data-pipeline.png" width="800" />  
- <img alt="picture 35" src="image/22-Data-And-Analytics/10-Big-Data-pipeline-note.png" width="800" />  


# Quiz

- You would like to have a database that is efficient at performing analytical queries on large sets of columnar data. You would like to connect to this Data Warehouse using a reporting and dashboard tool such as Amazon QuickSight. Which AWS technology do you recommend?
  - **Redshift**


- You have a lot of log files stored in an S3 bucket that you want to perform a quick analysis, if possible Serverless, to filter the logs and find users that attempted to make an unauthorized action. Which AWS service allows you to do so?
  - **Athena**


- As a Solutions Architect, you have been instructed you to prepare a disaster recovery plan for a Redshift cluster. What should you do?
  - Enable Automated Snapshots, then configure your Redshift cluster to automatically copy snapshots to another AWS region


- Which feature in Redshift forces all COPY and UNLOAD traffic moving between your cluster and data repositories through your VPCs?
  - **Enhanced VPC Routing**
  - Improved VPC Routing
  - Redshift Spectrum


- You are running a gaming website that is using DynamoDB as its data store. Users have been asking for a search feature to find other gamers by name, with partial matches if possible. Which AWS technology do you recommend to implement this feature?
  - **OpenSearch**


- An AWS service allows you to create, run, and monitor ETL (extract, transform, and load) jobs in a few clicks.
  - **Glue**


- A company is using AWS to host its public websites and internal applications. Those different websites and applications generate a lot of logs and traces. There is a requirement to centrally store those logs and efficiently search and analyze those logs in real-time for detection of any errors and if there is a threat. Which AWS service can help them efficiently store and analyze logs?
  - **OpenSearch**


- ……………………….. makes it easy and cost-effective for data engineers and analysts to run applications built using open source big data frameworks such as Apache Spark, Hive, or Presto without having to operate or manage clusters.
  - **EMR**


- An e-commerce company has all its historical data such as orders, customers, revenues, and sales for the previous years hosted on a Redshift cluster. There is a requirement to generate some dashboards and reports indicating the revenues from the previous years and the total sales, so it will be easy to define the requirements for the next year. The DevOps team is assigned to find an AWS service that can help define those dashboards and have native integration with Redshift. Which AWS service is best suited?
    - **QuickSight**


- Which AWS Glue feature allows you to save and track the data that has already been processed during a previous run of a Glue ETL job?
    - **Glue Job Bookmarks**


- You are a DevOps engineer in a machine learning company which 3 TB of JSON files stored in an S3 bucket. There’s a requirement to do some analytics on those files using Amazon Athena and you have been tasked to find a way to convert those files’ format from JSON to Apache Parquet. Which AWS service is best suited?
  - **Glue**


- You have an on-premises application that is used together with an on-premises Apache Kafka to receive a stream of clickstream events from multiple websites. You have been tasked to migrate this application as soon as possible without any code changes. You decided to host the application on an EC2 instance. What is the best option you recommend to migrate Apache Kafka?
  - **MSK**


- You have data stored in RDS, S3 buckets and you are using AWS Lake Formation as a data lake to collect, move and catalog data so you can do some analytics. You have a lot of big data and ML engineers in the company and you want to control access to part of the data as it might contain sensitive information. What can you use?
  - **Lake Formation Fine-grained Access Control**


- Which AWS service is most appropriate when you want to perform real-time analytics on streams of data?
  - **Amazon Kinesis Data Analytics**
  - Kinesis Data Firehose
  - SNS
  - SQS