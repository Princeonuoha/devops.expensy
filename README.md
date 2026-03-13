🚀 Expensy DevOps Platform

A production-style cloud-native DevOps project demonstrating modern infrastructure practices including Kubernetes, CI/CD automation, observability, security, and cloud networking.

The platform deploys a full-stack application on Azure Kubernetes Service (AKS) using containerized microservices, automated pipelines, and production-grade monitoring.

This project is designed as a real-world DevOps portfolio demonstrating modern platform engineering skills.

🧠 Architecture Overview

The platform follows a cloud-native microservices architecture deployed on Kubernetes.

User
  ↓
Azure Load Balancer
  ↓
NGINX Ingress Controller
  ↓
Kubernetes Services
  ↓
Application Pods
Application Stack
Layer	Technology
Frontend	Next.js / React
Backend	Node.js API
Database	MongoDB
Cache	Redis
Container Runtime	Docker
Orchestration	Kubernetes (AKS)
🏗 Infrastructure Architecture

The platform is deployed on Azure Kubernetes Service (AKS) and exposes the application via an NGINX Ingress Controller.

🌍 User
   ↓
☁️ Azure Load Balancer
   ↓
🌐 NGINX Ingress Controller
   ↓
📦 Kubernetes Services (ClusterIP)
   ↓
🐳 Application Pods

Running services:

frontend
backend
mongo
redis
prometheus
grafana

All services are internal ClusterIP services, exposed externally via Ingress routing.

⚙️ DevOps Tooling
🐳 Containerization

All services are containerized using Docker.

Example images:

princeonuoha/expensy-frontend
princeonuoha/expensy-backend

Benefits:

portable deployments

immutable infrastructure

reproducible environments

🔄 CI/CD Pipeline

The platform uses GitHub Actions to automate builds and deployments.

CI/CD Flow
Developer Push
     ↓
GitHub Actions
     ↓
Build Docker Images
     ↓
Push to Docker Hub
     ↓
Deploy to AKS
     ↓
Restart Kubernetes Deployments
Pipeline Responsibilities

✔ install dependencies
✔ build frontend & backend
✔ build Docker images
✔ push images to Docker Hub
✔ deploy to AKS cluster
✔ verify deployment health

Benefits:

⚡ fast automated deployments
🔐 secure secret handling
♻ immutable container releases

☸ Kubernetes Resources

The application is deployed using Kubernetes manifests.

k8s/
├── backend-deployment.yaml
├── frontend-deployment.yaml
├── mongo-deployment.yaml
├── redis-deployment.yaml
├── frontend-service.yaml
├── backend-service.yaml
├── ingress.yaml
├── configmap.yaml
├── secrets.yaml
├── network-policy.yaml
└── issuer.yaml

Resources include:

Deployments

Services

ConfigMaps

Secrets

Ingress

Network Policies

TLS Issuer

🌐 Ingress & DNS

External access is provided via the NGINX Ingress Controller.

DNS is temporarily managed using nip.io.

Example:

expensy.<external-ip>.nip.io

Traffic Flow:

User
 ↓
Cloudflare / DNS
 ↓
Azure Load Balancer
 ↓
NGINX Ingress
 ↓
Kubernetes Services
 ↓
Application Pods
🔐 TLS Certificates

HTTPS is automated using cert-manager and Let's Encrypt.

Benefits:

✔ automatic certificate provisioning
✔ automatic renewal
✔ secure HTTPS endpoints

📊 Observability Stack

The platform includes metrics, dashboards, and centralized logging.

Monitoring
Prometheus
Grafana

Prometheus scrapes metrics from the backend:

/metrics

Metrics include:

request counts

response status codes

service health

latency

Grafana Dashboards

Grafana visualizes system health including:

📈 API request volume
📉 latency metrics
💻 service health
🚦 error rates

📜 Logging

Centralized logging is implemented with Azure Monitor.

Example query:

ContainerLogV2
| where PodNamespace == "student-prince"
| project TimeGenerated, ContainerName, LogMessage
| order by TimeGenerated desc

Error detection:

ContainerLogV2
| extend LogString = tostring(LogMessage)
| where LogString has_any ("error","failed","exception","500")

Benefits:

✔ centralized debugging
✔ production observability
✔ incident analysis

🛡 Security

The platform follows several Kubernetes security best practices.

Implemented Controls

🔐 Azure RBAC for cluster access
🔐 Kubernetes Secrets for credentials
🔐 NetworkPolicies restricting pod communication
🔐 TLS encryption via cert-manager

Secrets are never committed to GitHub.

Instead they are injected through:

GitHub Secrets
Kubernetes Secrets
Runtime environment variables

Examples:

database credentials

Redis connection strings

API configuration

🧪 Health Probes

Kubernetes health checks ensure service reliability.

livenessProbe
readinessProbe

Example:

livenessProbe:
  httpGet:
    path: /health
    port: 3000

This ensures:

automatic container restart

only healthy pods receive traffic

⚠️ AKS Challenge Resolved

During deployment, an AKS Load Balancer health probe issue occurred.

Problem

Azure Load Balancer probes default to:

/

However, NGINX ingress exposes health checks at

/healthz

This caused Azure to mark nodes as unhealthy, dropping traffic.

Fix

Configured the correct probe path:

service.beta.kubernetes.io/azure-load-balancer-health-probe-request-path: /healthz

Result:

✔ nodes marked healthy
✔ traffic correctly routed
✔ application accessible externally

📂 Repository Structure
.
├── backend
├── frontend
├── k8s
├── .github/workflows
├── docker
└── README.md
🎯 Project Goals

This project demonstrates real DevOps engineering capabilities including:

✔ Kubernetes operations
✔ CI/CD automation
✔ containerized applications
✔ cloud infrastructure debugging
✔ observability systems
✔ production networking
✔ infrastructure security

👨‍💻 Author

Prince Onuoha

DevOps Engineer focused on building cloud-native platforms and scalable infrastructure.

Portfolio

👉 https://princeonuoha.vercel.app

⭐ DevOps Skills Demonstrated

Kubernetes (AKS)

Docker

CI/CD (GitHub Actions)

Cloud Networking

Observability

Infrastructure Debugging

DevOps Security

TLS Automation

Platform Engineering