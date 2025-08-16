# 🚀 Task 5: Build a Kubernetes Cluster Locally with Minikube

## 🎯 Objective
Deploy and manage apps in Kubernetes using Minikube, `kubectl`, and Docker.

---

## 🧰 Tools Required
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- Docker

---

## 📦 Project Structure

```
task-5-kubernetes-cluster/
├── deployment.yaml
├── service.yaml
├── screenshots/
│   ├── pods.png
│   ├── services.png
│   └── scale.png
└── README.md
```

---

## ⚙️ Step-by-Step Workflow

### 1️⃣ Start Minikube Cluster

```bash
minikube start
```

---

### 2️⃣ Create a Kubernetes Deployment

**File:** `deployment.yaml`

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
```

**Apply the Deployment:**
```bash
kubectl apply -f deployment.yaml
```

---

### 3️⃣ Expose the Deployment Using a Service

**File:** `service.yaml`

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  type: NodePort
  selector:
    app: nginx
  ports:
  - port: 80
    targetPort: 80
    nodePort: 30008
```

**Apply the Service:**
```bash
kubectl apply -f service.yaml
```

---

### 4️⃣ Verify Deployment and Services

```bash
kubectl get pods
kubectl get services
```

📸 _Screenshot: `pods.png`, `services.png`_

---

### 5️⃣ Scale the Deployment

```bash
kubectl scale deployment nginx-deployment --replicas=4
```

📸 _Screenshot: `scale.png`_

---

### 6️⃣ Describe the Deployment and Service

```bash
kubectl describe deployment nginx-deployment
kubectl describe service nginx-service
```

---

### 7️⃣ Access the Application

```bash
minikube ip
```

Open the following in your browser:
```
http://<minikube-ip>:30008
```

---

## 🧾 Outcome
You now understand:
- How to set up a local Kubernetes cluster
- How to deploy and scale applications using YAML files and `kubectl`
- How to expose services using NodePort

---

## 🖼️ Screenshots

| Description     | File             |
|----------------|------------------|
| Pod List        | screenshots/pods.png     |
| Services List   | screenshots/services.png |
| After Scaling   | screenshots/scale.png    |

---

## ✅ Author
**Madhukar Sammeta** – DevOps Engineer 
[LinkedIn](https://linkedin.com/madhukarsammeta) | [GitHub](https://github.com/iammadhukar177)

---
