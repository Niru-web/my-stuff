# ⚙️ MLOps — ML in Production

#mlops #deployment #docker #pipelines #monitoring #advanced

> 📖 **What is this?**
> MLOps (Machine Learning + DevOps) is the practice of deploying, monitoring, and maintaining ML models in production. A model that isn't deployed is just a Jupyter notebook — MLOps makes it real.

---

## 🎯 Why MLOps Matters

- 90% of ML projects never reach production — MLOps bridges that gap
- Models drift over time and need versioning, monitoring, and retraining
- Companies need reproducible, automated, scalable ML pipelines
- MLOps engineers are among the highest-paid ML professionals

---

## 📦 Key Concepts

### 1. The ML Lifecycle

```
Data Collection → Data Prep → Feature Engineering
        ↓
Model Training → Evaluation → Deployment
        ↓
Monitoring → Retraining → CI/CD loop (repeat)
```

### 2. Experiment Tracking

> Never lose track of what you tried and what worked.

- **MLflow** — log parameters, metrics, artifacts; compare runs
- **Weights & Biases** — real-time training visualization
- **DVC (Data Version Control)** — version control for datasets and models
- **Neptune.ai** — lightweight alternative to MLflow

```python
import mlflow

with mlflow.start_run():
    mlflow.log_param("n_estimators", 100)
    mlflow.log_param("max_depth", 5)
    mlflow.log_metric("accuracy", 0.923)
    mlflow.log_metric("f1_score", 0.891)
    mlflow.sklearn.log_model(model, "random_forest_model")
```

### 3. Model Packaging & Serving

| Method | Use Case |
|--------|----------|
| Pickle / Joblib | Simple Python model serialization |
| Docker Container | Package model + full environment |
| FastAPI | Lightweight REST API for predictions |
| Flask | Alternative to FastAPI |
| ONNX | Framework-agnostic model format |
| TF Serving / TorchServe | Production model servers |
| BentoML | Easy model serving framework |

```python
# FastAPI model serving
from fastapi import FastAPI
import joblib
import numpy as np

app = FastAPI()
model = joblib.load("model.pkl")

@app.post("/predict")
def predict(features: list):
    X = np.array(features).reshape(1, -1)
    prediction = model.predict(X)[0]
    probability = model.predict_proba(X)[0].max()
    return {"prediction": int(prediction), "confidence": float(probability)}
```

### 4. Docker & Containers

```dockerfile
# Dockerfile for a ML API
FROM python:3.11-slim

WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt

COPY model.pkl .
COPY app.py .

EXPOSE 8000
CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "8000"]
```

```bash
docker build -t ml-api .
docker run -p 8000:8000 ml-api
```

### 5. CI/CD for ML

- **CI (Continuous Integration)** — auto-test code on every commit
- **CD (Continuous Delivery)** — auto-deploy approved model versions
- **GitHub Actions** — automate testing and deployment pipelines
- **Tests to write for ML:**
  - Data schema validation (correct column types and ranges)
  - Model input/output shape tests
  - Model performance threshold tests (reject if accuracy < baseline)

### 6. ML Pipelines & Orchestration

- **Apache Airflow** — schedule and monitor complex workflows (DAGs)
- **Prefect** — modern Python-native pipeline orchestration
- **Dagster** — data-aware orchestration with asset tracking
- **Kubeflow** — ML pipelines on Kubernetes
- **ZenML** — MLOps framework designed for portability

```python
# Simple Airflow DAG
from airflow import DAG
from airflow.operators.python import PythonOperator
from datetime import datetime

def train_model(): ...
def evaluate_model(): ...
def deploy_model(): ...

with DAG("ml_pipeline", start_date=datetime(2024, 1, 1), schedule="@daily") as dag:
    t1 = PythonOperator(task_id="train", python_callable=train_model)
    t2 = PythonOperator(task_id="evaluate", python_callable=evaluate_model)
    t3 = PythonOperator(task_id="deploy", python_callable=deploy_model)
    t1 >> t2 >> t3
```

### 7. Model Monitoring

> Models degrade silently in production. You must monitor them!

| Issue | What It Means | How to Detect |
|-------|---------------|---------------|
| Data Drift | Input distribution changed | Statistical tests (KS test, PSI) |
| Concept Drift | X→Y relationship changed | Monitor prediction accuracy |
| Performance Degradation | Accuracy drops over time | Track metrics in production |

- **Evidently AI** — open-source ML monitoring dashboards
- **Whylogs** — lightweight data logging for ML
- **Prometheus + Grafana** — infrastructure monitoring + alerting

### 8. Cloud MLOps Platforms

| Platform | Provider | Key Feature |
|----------|----------|-------------|
| SageMaker | AWS | End-to-end ML — notebooks to deployment |
| Vertex AI | Google Cloud | Managed pipelines + AutoML |
| Azure ML | Microsoft | ML workspace + model registry |
| Databricks | Multi-cloud | Spark + MLflow + model serving |

---

## 🌍 Real-World Examples

- **Uber's Michelangelo** handles 1M+ ML predictions per second in production
- **Netflix** A/B tests new recommendation models before any global rollout
- **Airbnb** automatically retrains its pricing model every night with fresh data
- **Fraud detection** systems retrain weekly as new fraud patterns emerge

---

## 🛠️ Tools Summary

- **Experiment Tracking:** MLflow, Weights & Biases, DVC
- **Model Serving:** FastAPI, Docker, BentoML, ONNX
- **CI/CD:** GitHub Actions, Jenkins
- **Orchestration:** Airflow, Prefect, Dagster
- **Monitoring:** Evidently AI, Whylogs, Prometheus
- **Cloud:** AWS SageMaker, GCP Vertex AI, Azure ML

---

## ✅ Mini Practice Tasks

1. Train a model → log experiment to MLflow (parameters + metrics + model artifact)
2. Wrap the model in a FastAPI endpoint → test with `curl` or Postman
3. Dockerize your FastAPI API → build and run it locally
4. Set up DVC in a Git repo → version a small dataset
5. Create an Airflow DAG: data cleaning → training → evaluation → save report
6. Simulate data drift: retrain on a shifted dataset → compare metrics with Evidently AI

---

## 🔗 Internal Links

- [[07_Machine_Learning|→ Machine Learning]]
- [[08_Deep_Learning|→ Deep Learning]]
- [[03_Python_Programming|→ Python Programming]]
- [[04_SQL_for_Data_Analysis|→ SQL for Data Analysis]]
- [[00_MAIN_ROADMAP|← Back to Roadmap]]

---

## ➡️ Next Step

🎉 **You've completed the full roadmap!**

Now it's time to build end-to-end projects and start applying for roles.

**→ [[00_MAIN_ROADMAP|Back to Roadmap — Plan Your Next Steps]]**

> 🎯 **Final Goal:** Build 2–3 end-to-end projects with MLOps pipelines. Deploy them publicly (Hugging Face Spaces, AWS, GCP Free Tier). Push code to GitHub. Add to your resume.
>
> 💡 **Career Tip:** Knowing MLOps separates junior from mid-level data scientists. A *deployed* model is worth 10 Jupyter notebooks to a hiring manager.
