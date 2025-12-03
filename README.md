# Serverless ETL (Airflow -> Lambda -> S3)

This repo demonstrates a small ETL pipeline orchestrated by a locally-run Apache Airflow instance (via Docker Compose) which triggers an AWS Lambda function to fetch, clean, and save data to S3.

**Architecture**
- Airflow runs locally (Docker Compose) and schedules a DAG.
- The Airflow DAG invokes the AWS Lambda function (via boto3 `invoke`).
- The Lambda function fetches a public API, transforms data with pandas, and writes cleaned CSV file(s) to S3.

**Why this is resume-worthy**
- Shows orchestration (Airflow), serverless computing (Lambda), cloud storage (S3), Python ETL skills, and logging/retry patterns.

## Quick start (local Airflow + Lambda integration)

### Prereqs
- Docker & Docker Compose
- Python 3.10+ (for packaging Lambda locally if needed)
- AWS CLI configured with credentials for an account (create an IAM user with minimal permissions for Lambda + S3)

### 1) Start Airflow locally
```bash
# in repo root
docker-compose up -d
# Open Airflow UI: http://localhost:8080
# Default username/password: airflow / airflow