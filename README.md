## **Architectural Diagram**


![image](https://github.com/Reshmarathod/Stock-Market-Kafka-Real-Time-Data-Engineering-Project/assets/146751905/a2ae0bbb-fd9e-420a-abde-36d16b7883ce)


## **Overview**


In this project, I have executed an End-To-End Data Engineering Project on Real-Time Stock Market Data using Kafka.

I utilize Apache Kafka, a distributed streaming platform, to handle the real-time ingestion and processing of stock market data. The project involves setting up an EC2 instance to host the Kafka server, creating a producer to fetch stock market data, and developing a consumer to process and send the data to an S3 bucket.

To enhance the data processing capabilities, I incorporate AWS Glue, a fully managed extract-transform-load (ETL) service. By utilizing the AWS Glue crawler, I automate the discovery and cataloging of the data in the S3 bucket. This allows for seamless integration with AWS Athena, a serverless interactive query service, enabling us to run complex queries and gain valuable insights from the stock market data.

I have used different technologies such as Python, Amazon Web Services (AWS), Apache Kafka, Glue, Athena, and SQL.


## **Tech Stack**

AWS Services : S3, Lambda, Glue, Athena, EC2
Python Libraries : boto3, s3fs, pandas, kafka-python, json, dumps
Data Processing : kafka
Analytics and Visualization : Athena

## **Setup and Configuration**


To get started with the Stock Market Kafka Real Time Data Engineering Project, follow the setup and configuration instructions provided below. These instructions will guide you through the installation and configuration of the necessary components, as well as the deployment of the data pipeline on AWS.

## **Step 1: Creating an EC2 Instance**

Login to your AWS account and search for "EC2". Click on "Launch an instance", The instance windows shows up. On the Name and tags give your instance a name < name of instance >. For the instance type, make it "t2.micro"

![image](https://github.com/Reshmarathod/Stock-Market-Kafka-Real-Time-Data-Engineering-Project/assets/146751905/71967eed-a4c8-46ba-88ab-e13f395d904e)

On the Key pair (login), click on create new key pair and give it a name < name of key pair > and finally click on create key pair, this would download the key pair to your local device, this is what would be used to connect to your created instance locally.


![image](https://github.com/Reshmarathod/Stock-Market-Kafka-Real-Time-Data-Engineering-Project/assets/146751905/6c0f1549-6f8d-49ba-b44d-6209332a1641)

Next, Edit the inbound security group rule settings:

![image](https://github.com/Reshmarathod/Stock-Market-Kafka-Real-Time-Data-Engineering-Project/assets/146751905/60cf34c9-3928-4d8c-9bf1-e3018cf778be)

These settings enables us to SSH into the EC2 instance and access kafka on port 9092.

## **Step 2: creating the kafka server by running the following command:**


![image](https://github.com/Reshmarathod/Stock-Market-Kafka-Real-Time-Data-Engineering-Project/assets/146751905/ae1fd634-905a-4c84-8ffc-48ac703c8e6b)


Before creating the server, locate the directory were the key pair downloaded and locate connect on your created EC2 instance. and copy the higlighted text on the image above. this would give access to the created instance.

Next run wget https://downloads.apache.org/kafka/3.3.1/kafka_2.12-3.3.1.tgz. kafka would be installed, next extract the file by running:

#### **tar -xvf kafka_2.12-3.3.1.tgz**

Next install jave on the instance by running the below command:

#### **sudo yum install java-1.8.0-openjdk**

ow kafka and java is installed. since kafka runs on java. you can verify your java version by running java -version

Next, Start Zoo-keeper by running the below command on your terminal: 
#### **cd kafka_2.12-3.3.1**

#### **bin/zookeeper-server-start.sh config/zookeeper.properties**

Open another window on your terminal to start kafka. but ssh to your ec2 machine as done above

Start kafka-server: Duplicate the session & enter in a new console -- Before starting it change change server.properties so that it can run in public IP (public IP of your instance) To do this , you can follow the approaches shared below -- Do a "sudo nano config/server.properties" - change ADVERTISED_LISTENERS to public ip of the EC2 instance

export KAFKA_HEAP_OPTS="-Xmx256M -Xms128M" this command increases the space of kafka server

#### **cd kafka_2.12-3.3.1**

#### **bin/kafka-server-start.sh config/server.properties**

Next, Create a topic: Duplicate the session & enter in a new console -- cd kafka_2.12-3.3.1

#### **bin/kafka-topics.sh --create --topic demo_testing2 --bootstrap-server {Put the Public IP of your EC2 Instance:9092} --replication-factor 1 --partitions 1**

### **Start Producer**:
bin/kafka-console-producer.sh --topic demo_testing2 --bootstrap-server {Put the Public IP of your EC2 Instance:9092} 

### **Start Consumer**:
Duplicate the session & enter in a new console --

#### **cd kafka_2.12-3.3.1**

bin/kafka-console-consumer.sh --topic demo_testing2 --bootstrap-server {Put the Public IP of your EC2 Instance:9092} The kafka server is fully established and running.


## **STEP 3: Create an S3 Bucket**


To create an s3 bucket, search for s3 and click on Create bucket to create your s3 bucket

## **Step 4: Create a AWS glue IAM role**

To do this, search for IAM and click on Roles and create a AWS Glue role and give it AmazonS3FullAccess permission policies

## **Step 5: Stream data to your s3 bucket**

To stream data into s3, first change the path inside kafkaProducer.ipynb to the path of your s3 bucket. in kafkaProducer.ipynb run the second to last code to start the producer and also on kafkaConsumer.ipynb run the last code to establish a consumer. Notice the data immediately starts populating on your created s3 bucket

<img width="391" alt="image" src="https://github.com/Reshmarathod/Stock-Market-Kafka-Real-Time-Data-Engineering-Project/assets/146751905/bbadf3af-7e98-4a29-bbb1-9391f75f2052">


## **Step 6: Catalogue the Data with AWS Athena**
Search for AWS Glue and create a crawler which automate the discovery and cataloging of the data in the S3 bucket. Next use AWS athena to quary the data for insights

# **Usage**
Once the project is set up and configured, you can execute the data pipeline to start ingesting and processing real-time stock market data. The project documentation provides detailed instructions on how to run the producer and consumer components, as well as how to utilize AWS Glue and Athena for data analysis.

# **Contributing**
Contributions to the Stock Market Kafka Real Time Data Engineering Project are welcome! If you encounter any issues, have ideas for improvements, or would like to contribute new features, please submit a pull request. We appreciate your input and collaboration in making this project even better.



