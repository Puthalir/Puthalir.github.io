
---

### 🖥️ Virtual Machine (VM)

* Think of a **virtual machine** as a computer inside a computer.
* You create a VM in GCP using **Compute Engine**. You can choose the CPU, memory, disk, OS, and more.
* Example: If your app needs full control over OS-level details or to run a legacy system, a VM is the right fit.
* It’s part of **IaaS** (Infrastructure as a Service).

---

### ☁️ IaaS (Infrastructure as a Service)

* This is the **foundation layer** of cloud computing.
* You rent basic infrastructure (like VMs, storage, networks) and **you manage everything on top**.
* Example: Using Compute Engine to install and configure your own web server.

---

### 🔧 Modularization

* Breaking an application into **independent services or modules**.
* Example: Instead of one big app, you might have:

  * One service for authentication
  * One for payments
  * One for user profiles
* This makes it **easier to update**, **scale**, and **manage** different parts independently.

---

### 🔐 Service Account (Admin Role)

* A **service account** is like a robot user that your app or tool uses to talk to GCP.
* If you're deploying apps or accessing APIs from inside GCP (like from a Cloud Function), you need this.
* Giving it an **Admin role** means it can do anything — which is powerful but risky. Use least privilege when possible.

---

### ⚙️ Spin Up

* "Spinning up" a resource means **starting a cloud resource**, like a VM or a container.
* GCP allows you to spin up VMs, containers, databases, and more, often in seconds.

---

### 🖱️ GUI (Graphical User Interface)

* This refers to the **visual dashboard** — the GCP Console where you click buttons and fill out forms.
* You can do the same things using **CLI** (`gcloud`) or **Terraform** — much better for automation.

---

### 🐳 GKE (Google Kubernetes Engine)

* GKE is GCP’s **managed Kubernetes service**.
* Kubernetes helps you run **many containers** (mini applications) across **many machines** without having to manage them one by one.
* GKE makes it easier: it handles updates, monitoring, scaling, and networking for you.

---

### ⚙️ How to Configure GKE

1. **You choose a region and cluster settings**.
2. GCP sets up **master nodes** (control plane) and **worker nodes** (VMs that run your app).
3. You **deploy your app** using `kubectl`, a Kubernetes tool.
4. You **expose your app** to the internet using Services or Ingress.

---

### 🧰 Kubernetes & Multiple Containers

* Kubernetes uses **Pods**.
* A Pod can run **one or more containers**.
* Example use case:

  * One container runs your app.
  * Another container in the same Pod handles logging or monitoring.

---

### 🚀 How to Use Kubernetes (Overview)

* Write config files (YAML) that describe your app, how many copies (replicas), and how it should be exposed.
* Use `kubectl` to send those configs to Kubernetes.
* Kubernetes **makes sure** your app runs exactly the way you described — even if some parts fail.

---

### 📈 Autoscaling

* **Horizontal Autoscaling**:

  * Increases or decreases the number of Pods (instances of your app).
  * Example: If your app gets 1000 users suddenly, Kubernetes adds more Pods to handle the load.
* **Vertical Autoscaling**:

  * Gives more **CPU or memory** to the existing Pods, rather than adding more of them.

---

### 🔁 Round Robin Load Balancing

* This is a **simple way to distribute incoming requests** evenly across all running Pods.
* Kubernetes does this automatically using **Services**.
* This improves **availability** and **performance**.

---

### 🌐 Ingress (Kubernetes Load Balancer)

* Ingress is like a **traffic controller** for HTTP/S.
* It routes requests to the right service or app based on the URL path or hostname.
* Example:

  * `yourdomain.com/api` → goes to API service
  * `yourdomain.com/login` → goes to Auth service

---

### 🚀 Cloud Run (Serverless Platform)

* Cloud Run is for **deploying containers without worrying about infrastructure**.
* No VMs, no Kubernetes — just give it a Docker image, and GCP handles the rest.
* It **scales to zero** when no traffic, which saves money.
* Great for APIs, webhooks, small services.

---

### ✅ Recap

| Term            | What it Means                         | Use Case                            |
| --------------- | ------------------------------------- | ----------------------------------- |
| VM              | A cloud-hosted computer               | Full control apps or legacy systems |
| GKE             | Managed Kubernetes                    | Scalable containerized apps         |
| Service Account | Identity for automated access         | Let your app talk to GCP            |
| Ingress         | Routes web traffic to correct backend | Multi-service routing               |
| Cloud Run       | Serverless container hosting          | Simple, low-maintenance APIs        |
| Autoscaling     | Add/remove resources automatically    | Handle traffic spikes               |
| Modularization  | Split app into services               | Easier to maintain and scale        |

---
