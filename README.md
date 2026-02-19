Serverless CSV Processing Pipeline (AWS)
🚀 Project Overview

This project implements a fully serverless data processing pipeline using AWS services.

When a CSV file is uploaded to the input/ folder in S3, the system:

Automatically triggers AWS Lambda

Processes and transforms CSV data

Writes processed output to output/ folder

Sends notification to Amazon SQS

Logs execution details in CloudWatch

🏗 Architecture
S3 (input/)
      ↓
AWS Lambda (Python CSV processing)
      ↓
S3 (output/)
      ↓
Amazon SQS
      ↓
CloudWatch Logs

🛠 AWS Services Used

Amazon S3

AWS Lambda

Amazon SQS

Amazon CloudWatch

IAM (Execution Roles & Policies)

⚙ Features Implemented

Automatic S3 trigger

CSV transformation using Python

Date format conversion (MM/DD/YYYY → YYYY-MM-DD)

Volume validation (Low volume → N/A)

Percentage change recalculation

Automatic timestamp column (created_at)

Error handling and logging

Timeout and memory optimization

📂 Folder Structure (S3)
input/        → Raw uploaded CSV files
output/       → Processed CSV files

🔐 IAM Permissions

Lambda execution role includes:

s3:GetObject

s3:PutObject

sqs:SendMessage

CloudWatch logging permissions

🧠 Key Learning Outcomes

Event-driven architecture

Serverless computing

AWS IAM role management

Debugging Lambda timeouts

Understanding S3 key structure

Production-safe error handling

📦 Example Workflow

Upload file to:

input/sample.csv


Output automatically generated:

output/sample.csv


SQS receives notification message.

🔧 Tech Stack

Python

AWS Lambda

Amazon S3

Amazon SQS

CloudWatch

📌 Future Improvements

Dead Letter Queue (DLQ)

Step Functions integration

Data validation layer

Athena querying

CI/CD with GitHub Actions

👨‍💻 Author

Muhammad Zaid
Cloud & Data Engineering Enthusiast
