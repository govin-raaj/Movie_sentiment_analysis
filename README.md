# 🚀 End-to-End MLOps Capstone Project

An end-to-end **MLOps pipeline** implementation that takes a machine learning model from development to production on **AWS EKS**, with **MLflow for experiment tracking**, **DVC for data versioning**, **Docker for containerization**, **CI/CD via GitHub Actions**, and **Prometheus + Grafana for monitoring**.

This project is designed to demonstrate modern **MLOps best practices**, focusing on scalability, reproducibility, and automation.

---

## 🛠️ Tech Stack & Tools

* **Experiment Tracking:** [MLflow](https://mlflow.org/) via [Dagshub](https://dagshub.com/)
* **Data Versioning & Pipelines:** [DVC](https://dvc.org/)
* **Containerization:** Docker
* **CI/CD:** GitHub Actions
* **Cloud Infrastructure:** AWS (ECR, S3, EKS, IAM)
* **Orchestration & Deployment:** Kubernetes (EKS + kubectl + eksctl)
* **Monitoring & Visualization:** Prometheus & Grafana
* **Web Framework:** Flask (REST API for ML model inference)

---

## 📂 Project Structure

```bash
📦 mlops-capstone
 ┣ 📂 src
 ┃ ┣ 📂 logger
 ┃ ┣ 📜 data_ingestion.py
 ┃ ┣ 📜 data_preprocessing.py
 ┃ ┣ 📜 feature_engineering.py
 ┃ ┣ 📜 model_building.py
 ┃ ┣ 📜 model_evaluation.py
 ┃ ┣ 📜 register_model.py
 ┃
 ┣ 📂 flask_app      # REST API for serving model
 ┣ 📂 tests          # Unit & integration tests
 ┣ 📂 scripts        # Utility scripts
 ┣ 📜 dvc.yaml       # DVC pipeline definition
 ┣ 📜 params.yaml    # Experiment configs
 ┣ 📜 requirements.txt
 ┣ 📜 Dockerfile
 ┣ 📜 ci.yaml        # GitHub Actions CI/CD pipeline
```

---

## ⚙️ Key Features

### 🔹 Reproducible ML Pipeline with DVC

* Modular pipeline with stages:

  * Data ingestion → preprocessing → feature engineering → model training → evaluation → registration
* Version-controlled data & models
* Pipeline orchestration with `dvc repro`

### 🔹 Experiment Tracking with MLflow (via Dagshub)

* Centralized tracking of metrics, parameters, and artifacts
* Model registry integration
* Easily compare experiments in UI

### 🔹 Model Serving with Flask

* REST API endpoint for predictions:

  ```
  POST http://<EXTERNAL-IP>:5000/predict
  ```

### 🔹 CI/CD with GitHub Actions

* Automated testing (`pytest`)
* Build & push Docker images to AWS ECR
* Deploy to AWS EKS cluster

### 🔹 Kubernetes Deployment on AWS EKS

* Fully automated cluster creation via `eksctl`
* `deployment.yaml` + `service.yaml` for app deployment
* LoadBalancer service exposing prediction endpoint

### 🔹 Monitoring & Visualization

* **Prometheus** scrapes application metrics
* **Grafana** dashboards for real-time insights

---

## 🚀 Deployment Workflow

1. **Local Development**

   * Setup environment (`conda`, `cookiecutter`, `pip install -r requirements.txt`)
   * Develop pipeline (`src/` modules) & test with DVC + MLflow

2. **Version Control & Experiment Tracking**

   * Push code & experiment metadata to GitHub + Dagshub

3. **CI/CD Pipeline**

   * Triggered on push/PR:

     * Run tests
     * Build Docker image
     * Push image to AWS ECR
     * Deploy to EKS cluster

4. **Production Monitoring**

   * Prometheus scrapes metrics
   * Grafana dashboards visualize app performance & health

---

## 🌐 Live Demo (Sample Endpoint)

```
http://<LoadBalancer-External-IP>:5000/predict
```

Example request:

```bash
curl -X POST http://<LoadBalancer-External-IP>:5000/predict \
     -H "Content-Type: application/json" \
     -d '{"text": "This movie was fantastic!"}'
```

---

## 📊 Monitoring Dashboard

* **Prometheus UI:** `http://<ec2-public-ip>:9090`
* **Grafana Dashboard:** `http://<ec2-public-ip>:3000` (default login: admin/admin)

---

## 🧹 AWS Resource Cleanup

To avoid unnecessary charges:

```bash
# Delete deployment & service
kubectl delete deployment flask-app
kubectl delete service flask-app-service

# Delete EKS Cluster
eksctl delete cluster --name flask-app-cluster --region us-east-1

# Delete S3 & ECR artifacts (optional)
```

---

## 🌟 Highlights for Recruiters

✅ Hands-on experience with **end-to-end MLOps pipeline**
✅ Implemented **CI/CD with GitHub Actions** and **AWS EKS deployment**
✅ Strong foundation in **experiment tracking, data versioning, and monitoring**
✅ Real-world production workflow with **Docker + Kubernetes**
✅ Cloud-native ML solution following **best practices**

---

✨ *This project showcases my ability to take a machine learning solution from research to production, ensuring scalability, reproducibility, and maintainability.*

---

