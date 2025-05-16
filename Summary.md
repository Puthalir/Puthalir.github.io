## 🔍 Web Scraping

**Definition:** Web scraping is the automated process of extracting content or data from websites. It typically involves sending HTTP requests to webpages, parsing the HTML or JavaScript responses, and extracting the needed information using tools like BeautifulSoup, Scrapy, or Selenium. This data can be stored or processed for various use cases such as price monitoring, training data collection for AI models, or news aggregation.

**Flashcard:**

**Q:** What is web scraping and when is it used?\
**A:** Web scraping automates data extraction from websites. It's used for gathering training datasets, competitor analysis, and aggregating public information.

---

## 🐍 Poetry

**Definition:** Poetry is a Python dependency and package management tool that simplifies the management of Python projects. It uses a standardized configuration file called `pyproject.toml` to declare dependencies, manage virtual environments, and publish packages. Poetry ensures deterministic builds, improves project structure, and enhances reproducibility.

**Flashcard:**

**Q:** What is Poetry in Python and why is it helpful?\
**A:** Poetry manages dependencies and packaging. It simplifies project setup and ensures consistent environments across machines.

---

## 🧪 Virtual Environment

**Definition:** A virtual environment is a self-contained directory that contains a Python installation and libraries specific to a project. It isolates project dependencies from the system-wide Python environment, preventing version conflicts and making development and deployment more predictable.

**Flashcard:**

**Q:** Why are virtual environments used in Python projects?\
**A:** They isolate dependencies per project, preventing conflicts and ensuring reproducibility.

---

## ☁️ Google Cloud Platform (GCP)

**Definition:** GCP is a suite of cloud computing services provided by Google that runs on the same infrastructure that Google uses internally. It offers a wide range of services for computing, data storage, data analytics, machine learning, and application development.

---

### 🛂 IAM (Identity and Access Management)

**Definition:** IAM allows administrators to manage who has what level of access to which GCP resources. It uses policies that combine roles (sets of permissions) with identities (users, groups, or service accounts).

**Flashcard:**

**Q:** What is IAM in GCP?\
**A:** IAM manages access control using roles to grant permissions to users or service accounts.

---

### 🔐 Access Control

**Definition:** Access control in GCP is implemented through IAM and defines which users or services have access to GCP resources and what actions they can perform. It uses roles (basic, predefined, custom) to control permissions.

**Flashcard:**

**Q:** How does access control work in GCP?\
**A:** Access control uses IAM to assign predefined/custom roles to identities like users or service accounts.

---

### 🤖 Service Account

**Definition:** Service accounts are special Google accounts that belong to applications or VMs instead of users. They provide identity to services for authentication and authorization when calling GCP APIs.

**Flashcard:**

**Q:** What are service accounts used for?\
**A:** For programmatic access to GCP services by apps or VMs without user intervention.

---

### 🧩 GCP APIs

**Definition:** GCP provides a range of RESTful APIs that allow developers to interact with and manage GCP services such as BigQuery, Cloud Run, and Vertex AI. These APIs support automation, integration, and advanced usage scenarios.

**Flashcards:**

* **Vertex AI API:** Manages ML workflows like training, deployment, and predictions.
* **Cloud SQL API:** Manages SQL instance lifecycle.
* **BigQuery API:** Used for querying and managing datasets.
* **Cloud Run API:** Deploys and manages containerized services.
* **Connectors API:** Connects workflows to third-party and GCP services.

---

## 📡 Networking Concepts

**Definition:** Networking in cloud computing involves configuring how resources communicate internally and externally using components like VPCs, subnets, IP addresses, firewalls, and routing rules.

---

### 🌐 VPC (Virtual Private Cloud)

**Definition:** A VPC is a logically isolated network in GCP where users can launch resources in a virtual network that they define and control. It includes IP ranges, subnets, and routes.

**Flashcard:**

**Q:** What is a VPC in GCP?\
**A:** A private, logically isolated network in the cloud that hosts your GCP resources.

---

### 🧱 Subnets

**Definition:** Subnets are subdivisions of a VPC that allocate IP address ranges to GCP resources in a specific region. They help organize resources and control traffic.

---

### 📍 Port Numbers, Domains & IP Ranges

**Definition:** Ports identify specific processes or services (e.g., HTTP = port 80), domains resolve to IP addresses, and IP ranges define blocks of network addresses for routing and security.

---

### 🔥 Firewall Rules

**Definition:** Firewall rules in GCP control network traffic to and from VM instances based on IP, port, and protocol. They can be ingress or egress rules and apply to specified targets.

---

### 🧭 Ingress/Egress

**Definition:** Ingress is traffic entering your cloud network from external sources. Egress is traffic exiting the network to external destinations. GCP firewall rules and routing govern both.

---

### 🌐 IP Address

**Definition:** An IP address is a unique identifier assigned to each device connected to a network, used for routing traffic.

---

## 💾 Cloud Storage Types

**Definition:** Cloud storage services offer different models for storing and accessing data: block, object, and file storage, each suitable for different use cases.

---

### 🧱 Block Storage

**Definition:** Block storage provides raw storage volumes (e.g., Persistent Disks) that are attached to VMs. Data is split into blocks and managed by the OS.

### 📦 Object Storage

**Definition:** Object storage, like GCP's Cloud Storage, stores data as objects with metadata and a unique identifier. Ideal for unstructured data like media files, logs, and backups.

### 📁 File Storage

**Definition:** File storage provides shared access to files using a file system interface, like GCP Filestore. Useful for applications requiring a shared filesystem.

---

## 🔁 Pipeline Mechanisms

**Definition:** Pipelines orchestrate a series of steps to automate data processing, ML training, or code deployment.

---

### ⛓️ Data Movement (ETL)

**Definition:** ETL stands for Extract, Transform, Load — a data integration process for moving data from source systems to data warehouses.

---

### 🚀 CI/CD

**Definition:** Continuous Integration and Continuous Deployment (CI/CD) automates the process of testing, building, and deploying code changes to production environments.

---

### 🤖 ML Pipeline

**Definition:** ML pipelines define the flow for machine learning projects from data ingestion, preprocessing, model training, evaluation, and deployment.

---

## 💻 Virtual Machines

**Definition:** Virtual machines are emulated physical machines that run on cloud infrastructure (e.g., Compute Engine). They offer flexibility for running traditional workloads.

---

## 🏗️ Infrastructure as Code (IaC)

**Definition:** IaC is the practice of managing and provisioning infrastructure through code (e.g., Terraform, Deployment Manager), allowing for repeatable and version-controlled deployments.

---

## ☸️ Google Kubernetes Engine (GKE)

**Definition:** GKE is a managed Kubernetes service that simplifies deploying, managing, and scaling containerized applications using Kubernetes.

---

## 🛠️ Cloud Run

**Definition:** Cloud Run is a fully managed, serverless platform to run stateless containers. It automatically scales based on incoming requests.

---

## 📊 BigQuery

**Definition:** BigQuery is GCP’s serverless, highly scalable data warehouse optimized for running fast SQL queries on large datasets.

---

## 🔄 Pub/Sub Pattern

**Definition:** Publish/Subscribe is an asynchronous messaging pattern where publishers send messages to a topic and subscribers independently receive them.

---

## 🗄️ Cloud SQL

**Definition:** Cloud SQL is a fully managed relational database service that supports MySQL, PostgreSQL, and SQL Server with built-in high availability and backups.

---

## 🧠 Vertex AI

**Definition:** Vertex AI is Google Cloud’s unified AI platform for building, training, deploying, and managing ML models, including foundation models like Gemini.

**Flashcards:**

* **Load & Analyze:** Prepare and explore datasets using BigQuery or Vertex AI Data Labeling.
* **Prepare & Train:** Use AutoML or custom training jobs with frameworks like TensorFlow or PyTorch.
* **Model Evaluation:** Assess performance using metrics like accuracy, precision, recall, and confusion matrix.
* **Prediction & Deployment:** Deploy models to endpoints or run batch predictions.
* **LLM (Gemini):** Use state-of-the-art large language models for summarization, code generation, and chat interfaces.

---

## 💬 Dialogflow

**Definition:** Dialogflow is a Google Cloud tool for building conversational interfaces, such as chatbots and voice apps. It supports natural language understanding (NLU) and can be integrated with multiple platforms.

**Flashcards:**

* **Intent:** Represents a mapping between what a user says and what action should be taken.
* **Entity:** Extracts structured data from user inputs (e.g., time, date, location).
* **Slot Filling:** Ensures all required parameters are collected before responding to the user.
* **Dialogflow ES vs CX:** ES is designed for simple bots; CX offers more robust, scalable, and version-controlled bot development with visual flow building.
* **Dialogflow ES (Essentials)**

  * Good for simpler bots and linear flows.
  * Uses **Intents**, **Entities**, and **Contexts**.

* **Dialogflow CX (Customer Experience)**

  * Best for complex, multi-turn conversations.
  * Uses **Flows**, **Pages**, **Intents**, **Entities**, and **State Machines**.


---

## 🐳 Docker and Kubernetes Concepts

**Flashcards:**

* **Docker:** A platform to package applications and their dependencies into containers for consistent development and deployment.
* **Container:** A lightweight, standalone unit that includes everything needed to run an application.
* **VM vs Container:** VMs emulate entire systems with their own OS; containers share the host OS but isolate app environments.
* **Kubernetes:** An open-source system for automating deployment, scaling, and management of containerized apps.
* **Cluster:** A group of machines (nodes) running Kubernetes.
* **Node:** A single machine (VM or physical) in the Kubernetes cluster that runs pods.
* **Pod:** The smallest deployable unit in Kubernetes, usually running one or more containers.
* **Service:** An abstraction that exposes a set of pods as a network service.
* **Deployment:** Manages a replica set of pods and handles rolling updates.
* **Ingress:** Manages external HTTP(S) traffic and routes it to services within the cluster.
* **Control Plane:** Maintains cluster state; **Worker Nodes:** Execute workloads (pods).
