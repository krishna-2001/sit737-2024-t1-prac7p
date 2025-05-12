# sit737-2024-t1-prac7p
Great! Here's a complete, clear, and professional `README.md` tailored for your SIT737/SIT323 submission — using Docker Desktop, Node.js, MongoDB, and Kubernetes.

---

### 📄 `README.md`

```markdown
# SIT737 / SIT323 - Cloud Native Application Development  
## Week 9 - MongoDB Integration with Containerized Microservice

### 👨‍💻 Author
Krishna  
GitHub: [krishna820](https://github.com/krishna820)

---

## 🧩 Overview

This project demonstrates how to integrate MongoDB into a Node.js microservice deployed on a Kubernetes cluster using Docker Desktop. It features:

- A simple Express.js app performing CRUD operations on MongoDB
- Kubernetes configuration for deployments, services, secrets, and persistent storage
- Docker containerization of the backend application

---

## 📦 Project Structure

```

mongo-k8s-app/
│
├── backend/                  # Node.js application
│   ├── Dockerfile
│   ├── server.js
│   └── package.json
│
├── k8s/                      # Kubernetes configuration
│   ├── mongo-secret.yaml
│   ├── mongo-pv.yaml
│   ├── mongo-deployment.yaml
│   ├── app-deployment.yaml
│   └── app-service.yaml

````

---

## 🚀 Setup & Deployment

### ✅ Prerequisites
- Docker Desktop (with Kubernetes enabled)
- Node.js & npm (for local testing)
- `kubectl` CLI

### 🔨 Build and Run

1. **Clone this repository**
   ```bash
   git clone https://github.com/krishna820/sit323-737-2024-t1-prac7p.git
   cd sit323-737-2024-t1-prac7p
````

2. **Build and push Docker image**
   *(skip push if using local Docker Desktop image)*

   ```bash
   docker build -t krishna820/mongo-app:latest ./backend
   docker push krishna820/mongo-app:latest
   ```

3. **Deploy MongoDB and App to Kubernetes**

   ```bash
   kubectl apply -f k8s/
   ```

4. **(Optional) Port-forward app for local access**

   ```bash
   kubectl port-forward deployment/node-app-deployment 3000:3000
   ```

---

## 🌐 API Endpoints

### Base URL:

```
http://localhost:3000
```

### 📥 POST `/items`

Create a new item.

```bash
curl -X POST http://localhost:3000/items \
  -H "Content-Type: application/json" \
  -d '{"name":"Test Item"}'
```

### 📤 GET `/items`

Retrieve all items.

```bash
curl http://localhost:3000/items
```

---

## 🔐 Security

* MongoDB credentials are stored in a Kubernetes Secret (`mongo-secret.yaml`).
* App uses `MONGO_URI` environment variable from deployment manifest to securely connect.

---

## 💾 Persistent Storage

MongoDB data is persisted via a Kubernetes PersistentVolume and PersistentVolumeClaim (`mongo-pv.yaml`), using `hostPath` on the Docker Desktop VM.

---

## 📸 Screenshots

> *(Include these before submission)*

* `kubectl get pods`
* MongoDB and app logs showing successful connection
* CRUD operations via `curl`

---

## ✅ Checklist for Submission

* [x] App connects to MongoDB
* [x] Dockerfile and Kubernetes manifests provided
* [x] Environment variables secured using secrets
* [x] CRUD functionality working
* [x] README with setup instructions
* [ ] Screenshots or demo video included

---

## 🛑 Cleanup

To remove all Kubernetes resources:

```bash
kubectl delete -f k8s/
```

