# 🚀 End-to-End DevOps CI/CD Pipeline on AWS EKS

## 📌 Project Overview

This project demonstrates a complete DevOps implementation for deploying a containerized web application on AWS EKS using modern DevOps tools and practices.

The solution automates infrastructure provisioning, configuration management, continuous integration, continuous deployment, security scanning, and monitoring.

---

## 🏗️ Architecture

```text
Developer
    │
    ▼
 GitHub Repository
    │
    ▼
 Jenkins CI/CD Pipeline
    │
 ┌──┴───────────────┐
 │                  │
 ▼                  ▼
SonarQube      OWASP Dependency Check
Code Analysis  Vulnerability Scan
 │
 ▼
Trivy Security Scan
 │
 ▼
Docker Build
 │
 ▼
Docker Hub / AWS ECR
 │
 ▼
AWS EKS Cluster
 │
 ▼
Kubernetes Deployment
 │
 ▼
Prometheus + Grafana Monitoring
```

---

# 🛠️ Tools & Technologies

| Category                 | Tools                  |
| ------------------------ | ---------------------- |
| Cloud Provider           | AWS                    |
| Infrastructure as Code   | Terraform              |
| Configuration Management | Ansible                |
| CI/CD                    | Jenkins                |
| Containerization         | Docker                 |
| Container Registry       | Docker Hub / AWS ECR   |
| Orchestration            | Kubernetes (EKS)       |
| Code Quality             | SonarQube              |
| Security Scan            | Trivy                  |
| Dependency Scan          | OWASP Dependency Check |
| Monitoring               | Prometheus             |
| Visualization            | Grafana                |
| Version Control          | Git & GitHub           |

---

# 📂 Project Structure

```text
project-root/
│
├── terraform/
│   ├── ec2.tf
│   ├── variables.tf
│   ├── outputs.tf
│   └── terraform.tf
│
├── ansible/
│   ├── hosts.ini
│   └── basic_setup.yml
│
├── kubernetes/
│   ├── deployment.yaml
│   ├── service.yaml
│   └── ingress.yaml
│
├── Jenkinsfile
│
├── Dockerfile
│
└── README.md
```

---

# 🎯 Project Objectives

✅ Automate AWS infrastructure provisioning using Terraform

✅ Configure servers automatically using Ansible

✅ Implement CI/CD pipeline using Jenkins

✅ Deploy application to AWS EKS

✅ Perform Security & Vulnerability Scanning

✅ Monitor application and infrastructure health

✅ Achieve Infrastructure as Code (IaC)

---

# ☁️ AWS Infrastructure

The following AWS resources are provisioned:

* VPC
* Subnets
* Security Groups
* EC2 Instance (Jenkins Master)
* EKS Cluster
* S3 Bucket (Terraform State)
* IAM Roles & Policies

---

# 🐳 Dockerization

Build Docker Image:

```bash
docker build -t my-app .
```

Run Container:

```bash
docker run -d -p 3000:3000 my-app
```

---

# ⚙️ Terraform Deployment

Initialize Terraform:

```bash
terraform init
```

Validate Configuration:

```bash
terraform validate
```

Review Changes:

```bash
terraform plan
```

Create Infrastructure:

```bash
terraform apply -auto-approve
```

Destroy Infrastructure:

```bash
terraform destroy -auto-approve
```

---

# 🤖 Ansible Configuration

Verify Connectivity:

```bash
ansible ubuntu_servers -i hosts.ini -m ping
```

Run Playbook:

```bash
ansible-playbook -i hosts.ini basic_setup.yml
```

The playbook installs:

* Docker
* Docker Compose
* Jenkins
* AWS CLI
* kubectl
* eksctl
* Trivy

---

# 🔧 Jenkins Setup

Access Jenkins:

```text
http://<EC2-PUBLIC-IP>:8080
```

Install Plugins:

* Docker
* Pipeline Stage View
* SonarQube Scanner
* OWASP Dependency Check
* GitHub Integration

---

# 🔍 SonarQube Integration

Run SonarQube:

```bash
docker run -d \
--name sonarqube \
-p 9000:9000 \
sonarqube:lts-community
```

Access:

```text
http://<EC2-PUBLIC-IP>:9000
```

Features:

* Static Code Analysis
* Code Smells Detection
* Bug Detection
* Quality Gates

---

# 🛡️ Security Scanning

## OWASP Dependency Check

Detect vulnerable dependencies before deployment.

## Trivy Scan

Filesystem Scan:

```bash
trivy fs .
```

Docker Image Scan:

```bash
trivy image my-image:latest
```

---

# ☸️ Kubernetes Deployment

Deploy Application:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

Check Pods:

```bash
kubectl get pods
```

Check Services:

```bash
kubectl get svc
```

---

# 📊 Monitoring

## Prometheus

Collects:

* Node Metrics
* Container Metrics
* Kubernetes Metrics

## Grafana

Provides dashboards for:

* CPU Usage
* Memory Usage
* Pod Health
* Cluster Performance

---

# 🚀 CI/CD Pipeline Stages

### Stage 1: Source Code Checkout

```text
GitHub → Jenkins
```

### Stage 2: Code Quality Analysis

```text
SonarQube Scan
```

### Stage 3: Dependency Vulnerability Scan

```text
OWASP Dependency Check
```

### Stage 4: Security Scan

```text
Trivy Scan
```

### Stage 5: Build Docker Image

```text
Docker Build
```

### Stage 6: Push Image

```text
Docker Hub / AWS ECR
```

### Stage 7: Deploy to EKS

```text
Kubernetes Deployment
```

### Stage 8: Monitoring

```text
Prometheus + Grafana
```

---

# 📸 Screenshots

Add screenshots here:

```text
screenshots/
├── architecture.png
├── jenkins-dashboard.png
├── sonarqube-report.png
├── trivy-scan.png
├── grafana-dashboard.png
└── eks-cluster.png
```

---

# 📈 Key Features

* Fully Automated CI/CD Pipeline
* Infrastructure as Code
* Security Scanning
* Code Quality Analysis
* Kubernetes Deployment
* AWS EKS Integration
* Monitoring & Alerting
* Production Ready Architecture

---

# 🏆 Learning Outcomes

Through this project I gained hands-on experience with:

* Terraform
* Ansible
* Jenkins
* Docker
* Kubernetes
* AWS EKS
* SonarQube
* Trivy
* Prometheus
* Grafana
* CI/CD Best Practices

---

# 👨‍💻 Author

**Ismail Saiyed**

DevOps Engineer | Cloud Enthusiast | Kubernetes Practitioner

GitHub: https://github.com/<your-github-username>

LinkedIn: https://linkedin.com/in/<your-profile>

---

# ⭐ Support

If you found this project helpful, please consider giving it a ⭐ on GitHub.






