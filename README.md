# 🏗️ Infrastructure Design using IaC

## 📖 Overview
This project defines an **Infrastructure-as-Code (IaC)** setup for deploying applications on AWS. It provisions a **VPC**, two servers (**Main** and **Monitoring**), and integrates DevOps tools for CI/CD, containerization, and monitoring.

---

## 🌐 Architecture
- **VPC** with subnets, routing, and security groups  
- **Main Server (EC2)** – Hosts DevOps tools and manages EKS cluster  
- **Monitoring Server (EC2)** – Hosts monitoring stack (Prometheus, Grafana, Blackbox Exporter)  

---

## 🔹 Main Server (EC2)

### 📜 IAM Roles
- **EKS Management:** `AmazonEKSClusterPolicy`, `AmazonEKSServicePolicy`  
- **VPC & Networking:** `AmazonVPCFullAccess`  
- **IAM Role Creation:** `IAMFullAccess`  
- **EC2 & Node Groups:** `AmazonEC2FullAccess`  

### 🛠️ Installed Tools
- Docker  
- Jenkins  
- Node.js  
- kubectl  
- Terraform  
- Git  
- Java (JDK)  
- Trivy (security scanning)  
- OWASP Dependency Check  
- SonarQube (via Docker)  

---

## 🔹 Monitoring Server (EC2)

### 🛠️ Installed Tools (via Docker)
- **Prometheus** – Metrics collection  
- **Grafana** – Visualization dashboards  
- **Blackbox Exporter** – Endpoint monitoring  

---

## 📂 Project Structure
```plaintext
IaC-Infrastructure/
├── vpc/                # Terraform code for VPC setup
├── main-server/        # EC2 setup scripts & DevOps tools
├── monitoring-server/  # EC2 setup scripts & monitoring stack
├── deployment.yml      # Kubernetes Deployment manifest
├── service.yml         # Kubernetes Service manifest
├── dockerfile          # Docker build instructions
└── README.md           # Documentation
