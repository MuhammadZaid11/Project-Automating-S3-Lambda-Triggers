# 🚀 Serverless CSV Processing Pipeline on AWS

[![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white)](https://aws.amazon.com/)
[![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)](https://www.python.org/)
[![Serverless](https://img.shields.io/badge/Serverless-Actions-red?style=for-the-badge&logo=serverless)](https://aws.amazon.com/lambda/)

A fully automated, event-driven data pipeline that processes raw financial/stock data (CSV) using **AWS Lambda**, transforms it, and stores the results in **Amazon S3** while notifying downstream systems via **SQS**.

---

## 🏗 System Architecture

The pipeline follows a modern event-driven design:
1. **Trigger:** A CSV file is uploaded to the `input/` folder in an S3 Bucket.
2. **Compute:** S3 triggers an **AWS Lambda** function (Python).
3. **Processing:** Lambda performs data cleaning, date formatting, and volume validation.
4. **Storage:** Processed CSV is saved to the `output/` folder.
5. **Messaging:** An **Amazon SQS** message is sent upon successful completion.
6. **Monitoring:** All execution logs are captured in **Amazon CloudWatch**.



---

## 🛠 Tech Stack & Tools

| Service | Purpose |
| :--- | :--- |
| **Amazon S3** | Object storage for raw and processed data. |
| **AWS Lambda** | Serverless compute for CSV transformation. |
| **Amazon SQS** | Decoupling the pipeline and triggering notifications. |
| **CloudWatch** | Real-time monitoring and error logging. |
| **IAM** | Least-privilege access management for resources. |
| **Python (Pandas/CSV)** | Core logic for data manipulation. |

---

## ⚙️ Key Features

- ✅ **Automated Workflow:** No manual intervention needed after file upload.
- ✅ **Data Transformation:**
  - Standardizes date formats (`MM/DD/YYYY` → `YYYY-MM-DD`).
  - Validates stock volume (tags low volume as `N/A`).
  - Recalculates percentage changes.
  - Injects a `created_at` timestamp for audit trails.
- ✅ **Optimized Performance:** Tuned memory and timeout settings for efficient processing.
- ✅ **Robust Security:** IAM policies restricted to specific S3 prefixes and SQS ARNs.

---

## 📂 Project Structure

```text
.
├── s3-lambda-cloudwatch-stockprices/
│   ├── lambda_function.py     # Main Python logic
│   ├── requirements.txt       # Dependencies
│   └── sample_data.csv        # Test data
├── iam_policies/              # JSON permission files
└── README.md
