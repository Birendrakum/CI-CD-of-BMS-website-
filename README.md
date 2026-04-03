# 🚀 End-to-End DevOps Infrastructure & CI/CD Project

## 📖 Summary
This project demonstrates a **complete DevOps ecosystem** built on **AWS** using **Infrastructure-as-Code (IaC)**, **Terraform**, and a **Jenkins CI/CD pipeline**. It provisions a secure VPC, sets up EC2 servers for DevOps and monitoring, deploys an **Amazon EKS cluster**, and automates application delivery with integrated **code quality checks, security scans, containerization, and Kubernetes deployment**.  

The stack combines **AWS services, Terraform, Docker, Jenkins, SonarQube, OWASP, Trivy, Prometheus, and Grafana** to deliver a production-ready, scalable, and monitored application environment.

---

# 🏗️ Infrastructure Design using IaC

## 📖 Overview
This setup provisions a **VPC**, two servers (**Main** and **Monitoring**), and integrates DevOps tools for CI/CD, containerization, and monitoring.

### 🌐 Architecture
- **VPC** with subnets, routing, and security groups  
- **Main Server (EC2)** – Hosts DevOps tools and manages EKS cluster  
- **Monitoring Server (EC2)** – Hosts monitoring stack (Prometheus, Grafana, Blackbox Exporter)  

### 🔹 Main Server (EC2)
**IAM Roles:**
- `AmazonEKSClusterPolicy`, `AmazonEKSServicePolicy`  
- `AmazonVPCFullAccess`  
- `IAMFullAccess`  
- `AmazonEC2FullAccess`  

**Installed Tools:**
- Docker, Jenkins, Node.js, kubectl, Terraform, Git, Java (JDK)  
- Trivy, OWASP Dependency Check, SonarQube (via Docker)  

### 🔹 Monitoring Server (EC2)
**Installed Tools (via Docker):**
- Prometheus – Metrics collection  
- Grafana – Visualization dashboards  
- Blackbox Exporter – Endpoint monitoring  

---

# ☸️ AWS EKS Infrastructure with Terraform

## 🌐 Architecture
- **VPC**:
  - CIDR: `10.0.0.0/16`
  - AZs: `us-east-1a`, `us-east-1b`
  - Public subnets: `10.0.1.0/24`, `10.0.2.0/24`
  - Private subnets: `10.0.3.0/24`, `10.0.4.0/24`
  - NAT Gateway enabled (single NAT)

- **IAM Roles**:
  - Cluster Role → `AmazonEKSClusterPolicy`
  - Node Group Role → `AmazonEKSWorkerNodePolicy`, `AmazonEKS_CNI_Policy`, `AmazonEC2ContainerRegistryReadOnly`

- **EKS Cluster**:
  - Name: `my-eks-cluster`
  - Uses private subnets

- **Node Group**:
  - Name: `private-nodes`
  - Instance type: `t3.medium`
  - Scaling: min=1, desired=2, max=3
  - Runs inside private subnets

---

# 🎬 DevOps CI/CD Pipeline – BookMyShow App

## 📖 Overview
A **Jenkins Declarative Pipeline** automates build, test, security scanning, containerization, and deployment of the **BookMyShow application** onto AWS EKS.  

### ⚙️ Pipeline Workflow
1. Clean Workspace  
2. Checkout from GitHub  
3. SonarQube Analysis  
4. Quality Gate validation  
5. Install Node.js dependencies  
6. OWASP Dependency Check  
7. Trivy filesystem scan  
8. Terraform apply (EKS provisioning)  
9. Docker build & push to DockerHub  
10. Deploy to EKS via `kubectl`  

### 🛠️ Tools & Technologies
| **Category**            | **Tools Used** |
|--------------------------|----------------|
| CI/CD                   | Jenkins |
| Code Quality            | SonarQube |
| Security Scanning       | OWASP Dependency Check, Trivy |
| Infrastructure as Code  | Terraform |
| Containerization        | Docker |
| Orchestration           | Kubernetes (EKS) |
| Cloud Provider          | AWS |
| Languages               | Node.js, Java (JDK 17) |

---
## 🛠️ Key Tools & Services Used
- **AWS Services:** VPC, EC2, IAM, EKS, NAT Gateway, ECR  
- **DevOps Tools:** Jenkins, Docker, Terraform, kubectl, Git  
- **Code Quality & Security:** SonarQube, OWASP Dependency Check, Trivy  
- **Monitoring Tools:** Prometheus, Grafana, Blackbox Exporter  
- **Languages & Runtime:** Node.js, Java (JDK 17) 

---

## 👨‍💻 Author
**Birendra Kumar**  
- 🌐 [LinkedIn](https://www.linkedin.com/in/birendra-kumar-09580b173)  
- 📧 birendrakum.119@gmail.com  
