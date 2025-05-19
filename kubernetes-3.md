
⸻

## 🚀 Kubernetes with Minikube on macOS: YAML + K9s Guide

### 🧱 Prerequisites

Make sure you have Homebrew installed first.

### ✅ Install Required Tools

  brew install minikube
  brew install kubectl
  brew install k9s


⸻

### 🌐 Start Minikube Cluster

    minikube start --driver=docker

You can use --driver=hyperkit or --driver=virtualbox if preferred.

Verify:

    kubectl get nodes

Expected:

    NAME       STATUS   ROLES           AGE   VERSION
    minikube   Ready    control-plane   Xs    v1.32.x


⸻

### 📁 Create YAML File

Create a working directory:

  mkdir -p ~/k8s-demo && cd ~/k8s-demo
  touch web-app.yaml

#### ✍️ Paste the following into web-app.yaml:

      apiVersion: v1
      kind: Service
      metadata:
        name: web-service
      spec:
        selector:
          app: web-app
        ports:
          - name: apache
            port: 8080
            targetPort: 80
          - name: python
            port: 8000
            targetPort: 8000
        type: ClusterIP
      
      ---
      apiVersion: apps/v1
      kind: Deployment
      metadata:
        name: web-app
      spec:
        replicas: 1
        selector:
          matchLabels:
            app: web-app
        template:
          metadata:
            labels:
              app: web-app
          spec:
            containers:
              - name: apache
                image: httpd:latest
                ports:
                  - containerPort: 80
              - name: python
                image: python:3.12-slim
                command: ["python"]
                args: ["-m", "http.server", "8000"]
                ports:
                  - containerPort: 8000


⸻

### 📦 Deploy the App

    kubectl apply -f web-app.yaml

Check status:

    kubectl get pods
    kubectl get svc


⸻

### 🧭 Use K9s to Explore

    k9s

	•	Use → or ↓ to navigate
	•	Press : then type pods or svc to jump
	•	Use d to describe, l to view logs
	•	Press q to quit current screen or K9s

⸻

### 🧪 Test Service Locally

You can forward ports to access services from localhost:

    kubectl port-forward svc/web-service 8080:8080 8000:8000

Then visit:
	•	Apache: http://localhost:8080
	•	Python HTTP server: http://localhost:8000

⸻

### Clean Up
    
    kubectl delete -f web-app.yaml
    minikube stop


⸻

### ✅ Summary

    Task	Command
    Start cluster	minikube start --driver=docker
    Deploy YAML	kubectl apply -f web-app.yaml
    Explore with K9s	k9s
    Port Forward	kubectl port-forward svc/web-service ...
    Clean up	kubectl delete -f web-app.yaml


⸻





