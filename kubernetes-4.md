
⸻

## ☁️ Create Kubernetes Cluster in Azure Portal (AKS) – Step-by-Step Guide

### 🔧 Prerequisites
	•	✅ An active Azure account
	•	✅ Subscription with resource permissions
	•	✅ Azure region quota for at least 2–4 vCPUs (e.g., East US 2, Central US)

⸻

### 🧭 Step-by-Step: Create AKS Cluster via Azure Portal

#### 🔹 1. Login to Azure Portal

Go to:
  👉 https://portal.azure.com

⸻

#### 🔹 2. Create a Resource Group
	1.	In the search bar, type “Resource Groups”
	2.	Click + Create
	3.	Fill in:
	•	Subscription: (your current subscription)
	•	Resource Group Name: myResourceGroup (or your choice)
	•	Region: East US 2 or Central US
	4.	Click Review + Create → Create

⸻

#### 🔹 3. Create a Kubernetes Service (AKS)
	1.	In the top search bar, type “Kubernetes services”
	2.	Click + Create > Create Kubernetes cluster

⸻

### ⚙️ Fill in Cluster Details (Wizard Tabs)

#### ✅ Basics
	•	Subscription: (your active subscription)
	•	Resource Group: myResourceGroup
	•	Cluster name: myAKSCluster
	•	Region: East US 2 or Central US
	•	Kubernetes version: Leave default
	•	Node size: Standard_D2s_v3 (recommended)
	•	Node count: 1

❗ Avoid B-series VMs unless your subscription allows them
❗ Don’t enable Availability Zones unless supported in your region

Click Next: Node pools

⸻

### ✅ Node Pools
	•	Leave defaults
	•	Ensure node count = 1+
	•	Leave scaling options default

Click Next: Access

⸻

### ✅ Access
	•	Authentication method : System-assigned managed identity (default)
	•	Leave other settings as-is

Click Next: Networking

⸻

### ✅ Networking
	•	Choose Kubenet for simple setup
	•	Leave DNS name prefix blank (optional)
	•	Leave network policies as default

Click Next: Monitoring

⸻

### ✅ Monitoring
	•	Enable Container insights (Azure Monitor)
	•	Leave defaults

Click Next: Tags → Skip tags

⸻

### ✅ Review + Create
	1.	Review all settings
	2.	Click Create

⏳ Wait 3–5 mins for the AKS cluster to be provisioned

⸻

### 📡 Access Your AKS Cluster

### ✅ Option 1: Azure Cloud Shell (Browser Terminal)
	1.	Open Azure Portal
	2.	Click >_ icon at the top (Cloud Shell)
	3.	Run:

    az aks get-credentials --resource-group myResourceGroup --name myAKSCluster
    kubectl get nodes

### ✅ Option 2: Local Terminal (macOS)

    az login
    az aks get-credentials --resource-group myResourceGroup --name myAKSCluster
    kubectl get nodes


⸻

### ✅ Test the Cluster

    kubectl create deployment nginx --image=nginx
    kubectl expose deployment nginx --port=80 --type=LoadBalancer
    kubectl get service

After a few minutes, get the EXTERNAL-IP and test it in your browser.

⸻

### 🧹 Clean Up

    az group delete --name myResourceGroup --yes --no-wait


⸻

### 📌 Summary

    Task	Description
    Azure Service	AKS (Azure Kubernetes Service)
    Cluster Name	myAKSCluster
    Node Size	Standard_D2s_v3
    Region	East US 2, Central US
    Test Deployment	kubectl create deployment nginx --image=nginx
    Access Tools	az, kubectl, Azure Portal, Cloud Shell


⸻
