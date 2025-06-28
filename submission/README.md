

```markdown
# 🚀 Kubernetes Microservices Deployment – Skill Test

This project demonstrates the deployment of a Node.js-based microservices application on **Kubernetes using Minikube**. It includes four services:

- 🧑‍💼 **User Service** (Port: 3000)
- 📦 **Product Service** (Port: 3001)
- 🛒 **Order Service** (Port: 3002)
- 🌐 **Gateway Service** (Port: 3003 → replaced with `nginxdemos/hello` for testing)

---

## 📁 Folder Structure

```
submission/
├── deployments/
│   ├── user-service.yaml
│   ├── product-service.yaml
│   ├── order-service.yaml
│   └── gateway-service.yaml
├── services/
│   ├── user-service.yaml
│   ├── product-service.yaml
│   ├── order-service.yaml
│   └── gateway-service.yaml
├── screenshots/
│   ├── pods.png
│   ├── logs.png
│   └── service-test.png
└── README.md
```

---

## 🧰 Prerequisites

- ✅ [Minikube](https://minikube.sigs.k8s.io/)
- ✅ [kubectl](https://kubernetes.io/docs/tasks/tools/)
- ✅ Docker Hub images (pulled from `vignesh342` account)
- ✅ VS Code or text editor for YAML

---

## ⚙️ Step-by-Step Instructions

### 🔹 1. Start Minikube

```bash
minikube start
```

### 🔹 2. Clone This Project (if needed)

```bash
git clone https://github.com/Sadanki/microservices-k8s-minikube.git
cd microservices-k8s-deployment/submission
```

---

## 🚀 Deployment

### Apply All Deployment & Service Files

```bash
kubectl apply -f deployments/
kubectl apply -f services/
```

---

## ✅ Verify Everything is Running

```bash
kubectl get pods
kubectl get svc
```

Make sure all pods have `STATUS: Running`.

---

## 🌐 Testing the Application

### Step 1: Port-Forward the Gateway

```bash
kubectl port-forward svc/gateway-service 8080:80
```

Keep this terminal open.

### Step 2: In another terminal, test services

```bash
curl http://localhost:8080
curl http://localhost:8080/api/users
curl http://localhost:8080/api/products
curl http://localhost:8080/api/orders
```

Or simply open your browser and visit:

- `http://localhost:8080`
- `http://localhost:8080/api/users`
- `http://localhost:8080/api/products`
- `http://localhost:8080/api/orders`

You should see NGINX Hello responses from `nginxdemos/hello`.

---

## 🧪 Screenshots Included

| Screenshot            | Description                          |
|-----------------------|--------------------------------------|
| `pods.png`            | Output of `kubectl get pods`         |
| `logs.png`            | Output of `kubectl logs`             |
| `service-test.png`    | Browser or curl response from gateway|

---

## 🛠️ Troubleshooting Tips

- ❌ **ImagePullBackOff**:
  - Make sure images are correctly pushed to Docker Hub: `vignesh342/user-service`, etc.
  - Use `kubectl describe pod <pod-name>` for details.
- ❌ **Port-forward failed**:
  - Ensure your service exposes the correct `targetPort` that matches container `containerPort`.
- ❌ **Gateway connection refused**:
  - Double check `gateway-service.yaml` has correct `containerPort: 80`.

---

## 🧾 Docker Images Used

| Service        | Docker Image                              |
|----------------|--------------------------------------------|
| User Service   | `vignesh342/user-service:latest`          |
| Product Service| `vignesh342/product-service:latest`       |
| Order Service  | `vignesh342/order-service:latest`         |
| Gateway Service| `nginxdemos/hello` (for testing gateway)  |

---

## ✅ Skill Test Goals Achieved

- ✅ All microservices deployed to Minikube
- ✅ Verified inter-service connectivity
- ✅ Included resource limits, env vars, probes
- ✅ Services exposed and reachable via ClusterIP
- ✅ Test verified using port-forward and curl
- ✅ Screenshots included
- ✅ Documentation complete

---

Good luck! 🎯
```
