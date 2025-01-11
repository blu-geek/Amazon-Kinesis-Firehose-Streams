

# Data Transfer to S3 Bucket with Amazon Kinesis Data Firehose 

Amazon Kinesis Data Firehose is a fully managed service that delivers real-time streaming data to destinations such as Amazon Simple Storage Service (Amazon S3), Amazon Redshift, Amazon OpenSearch Service, Amazon OpenSearch Serverless, Splunk, and any custom HTTP endpoint.It can capture, transform, and load streaming data into data lakes, data stores, and analytics services. It is a reliable and scalable service that can handle high volumes of data.

As a Data Scientist, part of your role is streaming real-time sales data from POS systems across multiple retail stores to an S3 bucket for analytics. You decide to use Amazon Kinesis Firehose to capture this data continuously. The data, once transformed and enriched through Firehose, is stored in S3, enabling your analytics team to perform near-real-time analysis to optimize inventory and sales strategies.

# Amazon Kinesis Data Firehose

<img width="692" alt="Screenshot 2025-01-10 at 18 57 38" src="https://github.com/user-attachments/assets/3873eebf-0524-4f67-ac8d-39cd02458642" />

<img width="584" alt="Screenshot 2025-01-10 at 18 57 57" src="https://github.com/user-attachments/assets/13d3e7b8-3e51-427f-9f6a-5d49cb7c1449" />


# Activity Guide: Creating an S3 Bucket, Setting Up Kinesis Data Firehose, and Streaming Data with EC2

1. Set Up an S3 Bucket for Data Storage (Amazon S3)
Create an S3 Bucket:
Go to the Amazon S3 Console and create a bucket with a unique name.
Choose the appropriate region to minimize latency for your application.
Configure Permissions:
Set bucket policies to allow access from Amazon Kinesis Data Firehose and other AWS services.
Enable versioning and server-side encryption for secure data storage.
Configure Lifecycle Rules:
Set up lifecycle policies to automatically archive or delete data after a specific duration.

3. Set Up a Kinesis Data Firehose Delivery Stream (Amazon Kinesis)
Create a Delivery Stream:
Go to the Kinesis Console and select "Data Firehose" to create a new delivery stream.
Choose the destination as the S3 bucket created earlier.
Configure the Delivery Stream:
Enable compression (e.g., GZIP or Parquet) to optimize storage usage.
Set up data transformation if preprocessing is required using AWS Lambda.
Set IAM Permissions:
Attach an IAM role to the Firehose delivery stream, granting access to the S3 bucket.

3. Set Up Monitoring with CloudWatch Logs (Amazon CloudWatch)
Enable Logs for Firehose:
Configure Kinesis Firehose to send error logs and delivery logs to CloudWatch Logs.
Set Up CloudWatch Alarms:
Create alarms for monitoring metrics like delivery success, error rates, and data throughput.
Visualize Metrics:
Use CloudWatch dashboards to create visualizations for key performance indicators.

4. Configure VPC Components for Networking (Amazon VPC)
Create a VPC:
Set up a VPC with public and private subnets to host EC2 and related components.
Configure Security Groups:
Create security groups to control traffic between EC2, Kinesis, and the S3 bucket.
Set Up Routing:
Use NAT Gateways or Internet Gateways for internet access, as needed.

5. Launch an EC2 Instance to Generate Traffic (Amazon EC2)
Create an EC2 Instance:
Launch an EC2 instance in the VPC, using an Amazon Linux or Ubuntu AMI.
Assign an IAM role with permissions to write logs to Kinesis.
Install and Configure Tools:
Install software for log generation (e.g., Apache web server or custom scripts).
Set up scripts to generate log events and push them to Kinesis Data Firehose.

6. Monitor and Stream Log Events to S3 (Kinesis, CloudWatch, S3)
Send Logs to Kinesis:
Configure the EC2 instance to stream log events to the Kinesis Data Firehose delivery stream.
Verify Data Flow:
Ensure that log data is successfully written to the S3 bucket by Kinesis.
Analyze Logs:
Use S3 analytics tools or AWS Athena to analyze and query the stored logs.

7. Clean Up Resources (S3, Kinesis, EC2, CloudWatch)
Stop and Terminate EC2 Instances:
Shut down the EC2 instance after completing the tests to avoid incurring charges.
Delete Kinesis Delivery Stream:
Remove the Kinesis Firehose delivery stream and associated CloudWatch logs.
Clean Up S3 Bucket:
Delete the bucket or archive its contents if no longer needed.
Remove VPC Components:
Delete the VPC, security groups, and other networking resources.

