# 🚀 Banking Microservices Platform on Kubernetes

![Kubernetes](https://img.shields.io/badge/Kubernetes-1.28-blue?logo=kubernetes)
![Docker](https://img.shields.io/badge/Docker-Enabled-blue?logo=docker)
![Node.js](https://img.shields.io/badge/Node.js-Backend-green?logo=node.js)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-blue?logo=postgresql)
![DevOps](https://img.shields.io/badge/DevOps-Kubernetes-orange)

---

## 📌 Overview

This project is a production-style **Banking Microservices System** deployed on Kubernetes (Minikube).

It demonstrates real DevOps practices:

- Microservices architecture
- Kubernetes orchestration
- Horizontal Pod Autoscaling (HPA)
- Stateful database (PostgreSQL)
- Persistent storage (PVC)
- Health checks (Liveness & Readiness)
- Rolling updates (Zero downtime)
- ConfigMaps & Secrets

---

## 🏗️ Architecture

```mermaid
flowchart TD

USER[User] --> API[Banking API Service]

API --> PODS[API Pods - Deployment]
API --> DB[(PostgreSQL StatefulSet)]
DB --> PVC[Persistent Volume]

API --> HPA[Horizontal Pod Autoscaler]

API --> PROBES[Health Probes]
📸 Screenshots

Add your real cluster screenshots inside a folder named screenshots/

🧩 Pods Running

🚀 Deployments

⚖️ HPA Scaling

🗄️ PostgreSQL StatefulSet

🔄 Rolling Update

❤️ Health Checks

🌐 Services

⚙️ Tech Stack
Kubernetes (Minikube)
Docker
Node.js (Express API)
PostgreSQL
HPA (CPU-based autoscaling)
ConfigMap & Secrets
StatefulSets + PVC
🧪 Testing Scenarios
🔥 HPA Test
Load traffic generated
CPU usage increases
Kubernetes automatically scales pods (1 → 5)
💾 Database Persistence Test
kubectl delete pod postgres-db-0

Data remains safe due to PVC.

🔄 Rolling Update Test
New image deployed
Pods updated gradually
Zero downtime achieved
📂 Project Structure
k8s/
│
├── 00-namespace.yaml
├── 01-configmap.yaml
├── 02-secret.yaml
├── 03-postgres-statefulset.yaml
├── 04-api-deployment.yaml
├── 05-dashboard-deployment.yaml
├── 06-services.yaml
├── 07-ingress.yaml
├── 08-hpa.yaml
├── 09-rbac.yaml
├── 10-networkpolicy.yaml
├── 11-daemonset.yaml
👨‍💻 Author

DevOps Hands-on Project built to simulate real production Kubernetes environment.

🚀 Features Implemented

✔ Microservices architecture
✔ Kubernetes orchestration
✔ Auto scaling (HPA)
✔ Persistent database storage
✔ Self-healing system
✔ Secure configuration (Secrets + ConfigMap)
✔ Zero downtime deployments