# Day 52: Kubernetes Namespaces and Deployments

## 1. Namespaces Overview
Namespaces provide logical isolation for resources within the same physical cluster. They prevent naming collisions, allow scoped Role-Based Access Control (RBAC), and support resource quota boundaries between environments (e.g., `dev`, `staging`, `prod`) or multiple teams.

## 2. Deployment Manifest
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  namespace: dev
  labels:
    app: nginx
spec:
  replicas: 3
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
        image: nginx:1.24
        ports:
        - containerPort: 80
