🚀 Banking Microservices Platform on Kubernetes

A production-style cloud-native banking system deployed on Kubernetes (Minikube) demonstrating real-world DevOps practices including scalability, resilience, observability, and database persistence.

📌 Project Overview

This project simulates a modern banking backend system built with microservices architecture and deployed using Kubernetes.

It includes:

Banking API (Node.js)
PostgreSQL Database (StatefulSet)
Dashboard Service
Load Generator
Monitoring via Kubernetes probes
Auto-scaling using HPA
⚙️ Technologies Used
Kubernetes (Minikube)
Docker
Node.js
PostgreSQL
Horizontal Pod Autoscaler (HPA)
ConfigMap & Secrets
Liveness & Readiness Probes
Rolling Updates Strategy
Persistent Volumes (PVC)
🏗️ Architecture
User → Ingress/Service → Banking API → PostgreSQL
                           ↓
                      Dashboard
📦 Kubernetes Components
1️⃣ Namespace

Isolated environment for all banking services.

2️⃣ ConfigMap & Secrets
ConfigMap: non-sensitive configuration (DB host, ports)
Secrets: sensitive data (DB password, JWT secret)
3️⃣ Banking API (Deployment)
Node.js backend service
Exposed via ClusterIP Service
Uses environment variables from ConfigMap & Secret
4️⃣ PostgreSQL (StatefulSet)
Persistent database layer
Uses PVC to ensure data persistence
Headless Service for stable network identity
✔ Key Feature:

Data survives pod deletion and restarts

5️⃣ Horizontal Pod Autoscaler (HPA)
✔ Configuration:
minReplicas: 1–2
maxReplicas: 5
target CPU utilization: 50%
✔ Behavior:
Automatically scales pods based on CPU usage
Demonstrated scaling from 2 → 5 pods under load
6️⃣ Liveness & Readiness Probes
Readiness Probe:
Path: /api/ready
Ensures service is ready to receive traffic
Liveness Probe:
Path: /api/health
Restarts container if unhealthy
✔ Result:

Improved system reliability and self-healing behavior

7️⃣ Rolling Update Strategy
strategy:
  type: RollingUpdate
  rollingUpdate:
    maxUnavailable: 0
    maxSurge: 1
✔ Benefit:
Zero downtime deployment
Gradual replacement of old pods
8️⃣ Persistent Storage (PVC)
PostgreSQL uses Persistent Volume Claims
Ensures data is not lost when pods restart or are deleted
9️⃣ Services
ClusterIP for internal communication
NodePort for external dashboard access
🔥 Key Features Implemented

✔ Microservices architecture
✔ Kubernetes Deployment orchestration
✔ Auto-scaling with HPA (CPU-based scaling)
✔ Self-healing system (liveness probes)
✔ Service readiness control (readiness probes)
✔ Rolling updates without downtime
✔ Persistent database storage using StatefulSet + PVC
✔ Secure configuration using ConfigMaps & Secrets

🧪 Testing Scenarios
1️⃣ HPA Load Test
Simulated traffic using while true curl
CPU increased → pods scaled automatically
2️⃣ Database Persistence Test
kubectl delete pod postgres-db-0

✔ Result: Data remained intact

3️⃣ Rolling Update Test
Updated Docker image version
Pods updated gradually without downtime
4️⃣ Health Check Validation
/api/health → Liveness probe
/api/ready → Readiness probe

✔ Ensures system stability

📊 Observations
System automatically reacts to load
No downtime during updates
Database remains stable across restarts
Kubernetes ensures full lifecycle management
💡 What I Learned
Kubernetes core concepts (Pods, Deployments, Services)
Auto-scaling with HPA
Stateful applications in Kubernetes
Production-level deployment strategies
Real-world DevOps troubleshooting
Monitoring & health checks design
🚀 Future Improvements
Add Prometheus & Grafana monitoring
Implement CI/CD pipeline (GitHub Actions)
Add Ingress Controller for routing
Deploy to cloud (AWS EKS)
👩‍💻 Author

Built as a DevOps learning project demonstrating real-world Kubernetes infrastructure design and operations.