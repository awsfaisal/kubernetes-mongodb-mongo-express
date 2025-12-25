# MongoDB and Mongo Express on Kubernetes

## 📌 Project Overview
This project demonstrates how to deploy MongoDB and Mongo Express on a Kubernetes cluster using best practices such as Secrets, ConfigMaps, Deployments, and Services. MongoDB runs as a backend database, while Mongo Express provides a web-based UI to manage the database.

---

## 🛠️ Prerequisites
- Kubernetes cluster (Minikube / Kind / EKS)
- kubectl configured
- Docker images from Docker Hub

---

## 🗂️ Project Components

### 🔐 Secrets
- Created Kubernetes Secret to store MongoDB root username and password
- Credentials are base64 encoded and injected into pods securely

**File:** `mongodb-secret.yml`

---

### ⚙️ MongoDB Deployment & Service
- MongoDB deployed as a single replica
- Credentials passed using Kubernetes Secrets
- Exposed internally using a ClusterIP Service

**File:** `mongo.yml`
- Deployment
- Service

---

### 🧩 ConfigMap
- Created ConfigMap to store MongoDB service name as database URL
- Used by Mongo Express for backend connectivity

**File:** `mongo-configmap.yaml`

---

### 🖥️ Mongo Express Deployment & Service
- Mongo Express deployed as frontend UI
- Connected to MongoDB using Secrets and ConfigMap
- Exposed externally using LoadBalancer / NodePort service

**File:** `mongo-express.yaml`
- Deployment
- Service

---

## 🔁 Application Flow
1. MongoDB pod starts with credentials from Secrets
2. MongoDB Service exposes database internally
3. ConfigMap provides database service name
4. Mongo Express connects securely to MongoDB
5. Mongo Express UI is accessed via Service endpoint

---

## 🚀 Deployment Steps

```bash
kubectl apply -f mongodb-secret.yml
kubectl apply -f mongo.yml
kubectl apply -f mongo-configmap.yaml
kubectl apply -f mongo-express.yaml
## 🌐 Access Mongo Express
- URL: `http://<LoadBalancer-IP>:8081`
- Username: `admin`
- Password: `pass`

Note: If you want to expose Mongo Express on port 80, update the service port from 8081 to 80.
## 🧰 Technologies Used
- Kubernetes
- MongoDB
- Mongo Express
- Docker
- Kubernetes Secrets
- ConfigMaps
- Deployments
- Services

