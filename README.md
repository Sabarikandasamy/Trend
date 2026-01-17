# 🚀 Trend Store – End-to-End DevOps CI/CD on AWS

A **production-style DevOps project** demonstrating how a frontend application is containerized, automated, deployed, and monitored using **AWS, Docker, Kubernetes (EKS), and Jenkins**.

---

## 🔥 Project Highlights

* ✅ Dockerized React static application
* ✅ CI/CD pipeline using Jenkins
* ✅ Deployed on AWS EKS (Kubernetes)
* ✅ Publicly accessible via LoadBalancer
* ✅ Monitoring enabled using Metrics Server
* ✅ IAM best practices with EC2 Roles

---

## 🏗 Architecture Overview

```
GitHub
  ↓
Jenkins (CI/CD)
  ↓
Docker Hub
  ↓
AWS EKS (Kubernetes)
  ↓
AWS LoadBalancer
  ↓
Browser
```

---

## 🛠 Tech Stack

| Category      | Tools                    |
| ------------- | ------------------------ |
| Cloud         | AWS (EC2, EKS, IAM, ELB) |
| CI/CD         | Jenkins                  |
| Containers    | Docker                   |
| Orchestration | Kubernetes (EKS)         |
| Registry      | Docker Hub               |
| Monitoring    | Metrics Server           |
| SCM           | GitHub                   |

---

## 📦 Application Details

* **Type:** Static Frontend App
* **Server:** NGINX
* **Container Port:** 80
* **Service Port:** 3000

---

## 📂 Repository Structure

```
Trend/
├── Dockerfile
├── Jenkinsfile
├── k8s/
│   ├── deployment.yaml
│   └── service.yaml
├── screenshots/
└── README.md
```

---

## 🚀 Implementation Steps (High Level)

### 1️⃣ Dockerization

* Created Dockerfile using `nginx:alpine`
* Copied build files into NGINX html directory
* Tested application locally using Docker

---

### 2️⃣ Docker Hub

* Built image for `linux/amd64`
* Tagged and pushed image to Docker Hub

---

### 3️⃣ Kubernetes (EKS)

* Created EKS cluster
* Deployed application using Kubernetes manifests
* Exposed app using LoadBalancer service

---

### 4️⃣ Jenkins CI/CD

* Jenkins installed on EC2
* Configured Docker, kubectl, AWS CLI
* IAM Role attached to Jenkins EC2
* Pipeline stages:

  * Checkout
  * Build image
  * Push image
  * Deploy to EKS

---

### 5️⃣ Monitoring

* Installed Kubernetes Metrics Server
* Verified node and pod resource usage

---

## 🌐 Application Access

The application is publicly accessible via AWS LoadBalancer.

```
http://<EKS-LoadBalancer-DNS>:3000
```

(Screenshot attached in `screenshots/aws_app_running.png`)

---

## 📸 Screenshots Included

* ✅ Application running in browser
* ✅ Jenkins pipeline success
* ✅ Docker image pushed to Docker Hub
* ✅ EKS nodes & pods running
* ✅ Kubernetes services & LoadBalancer
* ✅ Metrics Server output

---

## ⚠️ Challenges Faced & Solutions

| Issue                            | Solution                                |
| -------------------------------- | --------------------------------------- |
| Docker image pull failed         | Built image for `linux/amd64`           |
| Jenkins Docker permission denied | Added Jenkins user to Docker group      |
| EKS access denied                | Fixed IAM role & aws-auth mapping       |
| Metrics not available            | Installed Metrics Server with EKS flags |

---

## 🎯 Outcome

✔ Fully automated CI/CD pipeline
✔ Application running on AWS EKS
✔ Public access via LoadBalancer
✔ Monitoring enabled
✔ Real-world DevOps troubleshooting experience

---

## 👤 Author

**Sabari Kandasamy**
DevOps | Cloud | Kubernetes | CI/CD

---

⭐ *This project reflects real production challenges and solutions, not just theory.*

---
