Churn Risk Prediction Service
(DevOps + MLOps Project)
This project implements a customer churn prediction service using FastAPI, integrated with a complete DevOps pipeline including CI/CD, Docker, and monitoring.
The system estimates churn risk based on contract type and customer support activity.

---

Objective
The goal is to demonstrate how a prediction service can be deployed and managed using DevOps practices.
Features
REST API for churn prediction
Rule-based logic
Docker containerization
CI/CD (GitHub Actions)
Monitoring with Prometheus & Grafana
Automated testing

---
Project Structure
├── src
│   ├── app.py
│   ├── rule_engine.py
│   └── feature_pipeline.py
│
├── data
├── scripts
├── tests
├── monitoring
├── grafana
├── docs
│
├── Dockerfile
├── requirements.txt
└── README.md

---
DevOps Workflow
flowchart TD
Developer --> GitHub --> CI
CI --> Test --> Build --> Deploy --> FastAPI
FastAPI --> Metrics --> Prometheus --> Grafana

---
CI Pipeline
On every push:
Install dependencies
Run tests
Build Docker image

---
Monitoring
Metrics available at /metrics
Includes:
API request count
Prediction count
Response latency

flowchart LR
API --> Metrics --> Prometheus --> Grafana

---
MLOps Overview
flowchart LR
Data --> Processing --> Features --> Model --> API --> Predictions

---
Features Used
contract_type
tickets_last_30_days
complaint_ticket
negative_ratio

---
Risk Logic
| Condition                        | Risk |
| -------------------------------- | ---- |
| High complaints + short contract | HIGH |
| Moderate activity                | MED  |
| Stable usage                     | LOW  |

---
API Endpoints
/ → Health check
/predict-risk → Predict churn
/metrics → Metrics
Docs: http://localhost:8000/docs

---
Run the Service
Local
uvicorn src.app:app --host 0.0.0.0 --port 8000

Docker
docker build -t churn-risk-service .
docker run -p 8000:8000 churn-risk-service

Monitoring Setup
cd monitoring
docker compose up

Prometheus → http://localhost:9090
Grafana → http://localhost:3000

---
Testing
pytest

---
Tech Stack
FastAPI
Python
Docker
GitHub Actions
Prometheus
Grafana

---
Future Improvements
Replace rules with ML model
Add automated pipelines
Deploy using Kubernetes
