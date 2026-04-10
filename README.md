# 🚀 Banking Microservices Platform on Kubernetes

A production-style cloud-native banking system deployed on Kubernetes (Minikube), demonstrating real-world DevOps practices including scalability, resilience, observability, and database persistence.

---

## 📌 Project Overview

This project simulates a modern banking backend system built with microservices architecture and deployed using Kubernetes.

It includes:

- Banking API (Node.js)
- PostgreSQL Database (StatefulSet)
- Dashboard Service
- Load Generator
- Monitoring via Kubernetes probes
- Auto-scaling using HPA

---

## ⚙️ Technologies Used

- Kubernetes (Minikube)
- Docker
- Node.js
- PostgreSQL
- Horizontal Pod Autoscaler (HPA)
- ConfigMap & Secrets
- Liveness & Readiness Probes
- Rolling Updates Strategy
- Persistent Volumes (PVC)

---

## 🏗️ Architecture


User → Service → Banking API → PostgreSQL
↓
Dashboard


---

## 📦 Kubernetes Components

### 1️⃣ Namespace
Isolated environment for all banking services.

---

### 2️⃣ ConfigMap & Secrets
- ConfigMap: non-sensitive configuration (DB host, ports)
- Secrets: sensitive data (DB password, JWT secret)

---

### 3️⃣ Banking API (Deployment)
- Node.js backend service
- Exposed via ClusterIP Service
- Uses ConfigMap & Secrets

---

### 4️⃣ PostgreSQL (StatefulSet)
- Persistent database layer
- Uses PVC to ensure data persistence
- Headless Service for stable network identity

✔ Data survives pod deletion and restarts

---

### 5️⃣ Horizontal Pod Autoscaler (HPA)
- Min replicas: 1–2
- Max replicas: 5
- CPU target: 50%

✔ Automatically scales based on CPU load

---

### 6️⃣ Liveness & Readiness Probes

- Readiness: `/api/ready`
- Liveness: `/api/health`

✔ Ensures:
- Self-healing
- Traffic routing only to healthy pods

---

### 7️⃣ Rolling Update Strategy

```yaml
strategy:
  type: RollingUpdate
  rollingUpdate:
    maxUnavailable: 0
    maxSurge: 1

✔ Zero downtime deployments

8️⃣ Persistent Storage (PVC)

PostgreSQL uses Persistent Volume Claims:

✔ Data is not lost after pod restart or deletion

9️⃣ Services
ClusterIP → internal communication
NodePort → external dashboard access
🔥 Key Features
Microservices architecture
Kubernetes orchestration
Auto-scaling (HPA)
Self-healing system
Persistent database storage
Secure configuration management
Zero-downtime deployments
🧪 Testing Scenarios
1️⃣ HPA Load Test

Simulated traffic → CPU increased → pods scaled automatically

2️⃣ Database Persistence Test
kubectl delete pod postgres-db-0

✔ Data remains safe

3️⃣ Rolling Update Test

New image deployed → pods updated gradually → no downtime

4️⃣ Health Checks
/api/health → Liveness
/api/ready → Readiness
🚀 Future Improvements
Add Prometheus & Grafana monitoring
CI/CD pipeline (GitHub Actions)
Ingress Controller
Cloud deployment (AWS EKS)
👩‍💻 Author
Menna-Elyamany
DevOps Engineer | Cloud & Kubernetes Enthusiast 

📌 GitHub: https://github.com/mennaelyamany2
📌 LinkedIn: https://linkedin.com/in/menna-elyamany

Built as a DevOps learning project to simulate real-world Kubernetes infrastructure.