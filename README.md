Architectural Diagram

![image](https://github.com/Reshmarathod/Stock-Market-Kafka-Real-Time-Data-Engineering-Project/assets/146751905/eb613283-c050-4a81-bd88-1eba5bf57880)

Overview

In this project, I have executed an End-To-End Data Engineering Project on Real-Time Stock Market Data using Kafka.

I utilize Apache Kafka, a distributed streaming platform, to handle the real-time ingestion and processing of stock market data. The project involves setting up an EC2 instance to host the Kafka server, creating a producer to fetch stock market data, and developing a consumer to process and send the data to an S3 bucket.

To enhance the data processing capabilities, I incorporate AWS Glue, a fully managed extract-transform-load (ETL) service. By utilizing the AWS Glue crawler, I automate the discovery and cataloging of the data in the S3 bucket. This allows for seamless integration with AWS Athena, a serverless interactive query service, enabling us to run complex queries and gain valuable insights from the stock market data.

I have used different technologies such as Python, Amazon Web Services (AWS), Apache Kafka, Glue, Athena, and SQL.


Tech Stack
AWS Services : S3, Lambda, Glue, Athena, EC2
Python Libraries : boto3, s3fs, pandas, kafka-python, json, dumps
Data Processing : kafka
Analytics and Visualization : Athena

Setup and Configuration

To get started with the Stock Market Kafka Real Time Data Engineering Project, follow the setup and configuration instructions provided below. These instructions will guide you through the installation and configuration of the necessary components, as well as the deployment of the data pipeline on AWS.
