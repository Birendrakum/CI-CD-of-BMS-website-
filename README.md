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



---

# 🎬 DevOps CI/CD Pipeline – BookMyShow App

## 📖 Overview
This repository contains a **Jenkins Declarative Pipeline** for automating the build, test, security scanning, containerization, and deployment of the **BookMyShow application** onto an **AWS EKS cluster**.  

The pipeline integrates **SonarQube, OWASP Dependency Check, Trivy, Terraform, Docker, and Kubernetes** to ensure code quality, security, and scalability.

---

## ⚙️ Pipeline Workflow

### 🔹 Stages
1. **Clean Workspace** – Ensures a fresh build environment.  
2. **Checkout from Git** – Clones the repository from GitHub.  
3. **SonarQube Analysis** – Performs static code analysis.  
4. **Quality Gate** – Validates SonarQube results before proceeding.  
5. **Install Dependencies** – Installs Node.js dependencies for the app.  
6. **OWASP FS Scan** – Runs OWASP Dependency Check for vulnerabilities.  
7. **Trivy FS Scan** – Scans filesystem for vulnerabilities.  
8. **Terraform Apply EKS** – Provisions AWS EKS cluster using Terraform.  
9. **Docker Build & Push** – Builds and pushes Docker image to DockerHub.  
10. **Deploy to EKS Cluster** – Deploys application using Kubernetes manifests.  

---

## 🛠️ Tools & Technologies

| **Category**            | **Tools Used** |
|--------------------------|----------------|
| **CI/CD**               | Jenkins |
| **Code Quality**        | SonarQube |
| **Security Scanning**   | OWASP Dependency Check, Trivy |
| **Infrastructure as Code** | Terraform |
| **Containerization**    | Docker |
| **Orchestration**       | Kubernetes (EKS) |
| **Cloud Provider**      | AWS |
| **Languages**           | Node.js, Java (JDK 17) |

---

