# ☁️ **Google Cloud Platform (GCP) Overview**

🔹 **Project**

  A project in GCP is a logical container for resources (like APIs, storage, databases).

  All billing, access control, and API usage are tied to a specific project.


## 🔐 **Access Control in GCP**

### 🔹 **IAM** (Identity and Access Management)

Manages who can do what on which resources.

### **Roles**:

  **Primitive roles**: Basic access (Owner, Editor, Viewer).
  
  **Predefined roles**: Granular, service-specific roles (e.g., BigQuery Data Viewer, Dialogflow Admin).
  
  **Custom roles**: You define specific permissions for custom needs.

### **Service Account**:

  A special Google account used by apps or VMs to call GCP services.
  
  Attach to APIs, run services like Cloud Run, or authenticate with Dialogflow.

### 🔌 **API Services and Usage**

🔹 **Billing Based on Usage**

  GCP APIs and services charge based on actual use:
  
  E.g., number of queries, storage used, compute time, etc.
  
  Each project must be linked to a Billing Account to use paid services.



### **API Services**

  | API / Service      | Purpose                                                                 |
  | ------------------ | ----------------------------------------------------------------------- |
  | **Dialogflow API** | Build conversational agents (chatbots, voicebots) using NLP             |
  | **Cloud SQL API**  | Manage relational databases like MySQL/PostgreSQL in the cloud          |
  | **BigQuery API**   | Run fast SQL queries on large-scale datasets (data warehouse)           |
  | **Vertex AI API**  | Train, deploy, and manage machine learning models                       |
  | **Cloud Run API**  | Deploy and scale containerized apps with HTTP endpoints automatically   |
  | **Connectors API** | Connect GCP services to external systems (e.g., Salesforce, MySQL, etc) |


Required:

🤖 What is **Dialogflow** API?

  Dialogflow is Google’s Natural Language Understanding (NLU) platform for building conversational interfaces like chatbots, voice assistants, or IVR systems.
  
  Dialogflow **ES** (Essentials): Simple agents, easy to use, ideal for basic use cases.
  
  Dialogflow **CX** (Customer Experience): Advanced agents, suitable for large, complex, multi-turn conversations.
  
  The Dialogflow API allows developers to manage agents, intents, sessions, training data, and detect intent programmatically.

### 📌 **Reasons to Use Dialogflow API in GCP**

| Feature                       | Benefit                                                        |
| ----------------------------- | -------------------------------------------------------------- |
| 🤖 **Conversational AI**      | Build chatbots and voice bots for customer service, FAQs, apps |
| 🔁 **Multi-Platform Support** | Easily deploy on websites, apps, Google Assistant, IVR         |
| 🧠 **NLU + ML**               | Understand user intent and respond intelligently               |
| 🛠️ **Programmable**          | Automate training, deployments, and analysis via API           |
| 📈 **Scalable**               | Support thousands of conversations in parallel                 |
| 🔐 **GCP Integration**        | Use with Cloud Functions, Cloud Run, BigQuery, etc.            |



### 📌 **Reasons to Use Cloud SQL in GCP**

| Benefit                        | Explanation                                                      |
| ------------------------------ | ---------------------------------------------------------------- |
| ✅ **Managed Database Service** | Google handles patching, backups, and replication.               |
| ✅ **High Availability**        | Supports failover and multi-zone replication.                    |
| ✅ **Scalability**              | You can vertically scale compute/storage easily.                 |
| ✅ **Security**                 | IAM integration, SSL, private IPs, and encryption at rest.       |
| ✅ **Integration with GCP**     | Works seamlessly with App Engine, Cloud Run, GKE, BigQuery, etc. |
| ✅ **Automated Backups**        | You can recover your database from a backup anytime.             |
| ✅ **Performance Insights**     | See slow queries, connections, and tuning suggestions.           |


### 🔧 **Use Cases**

  Web or mobile apps that need a backend relational DB
  
  Migration of legacy MySQL/PostgreSQL/SQL Server databases
  
  Internal apps and dashboards
  
  Apps requiring structured data with ACID properties
  

### 📌 **Reasons to Use BigQuery in GCP**

| Feature                            | Benefit                                                  |
| ---------------------------------- | -------------------------------------------------------- |
| ✅ **Serverless Data Warehouse**    | No need to manage infrastructure or clusters.            |
| ✅ **Real-time & Batch Analysis**   | Analyze streaming or batch data quickly.                 |
| ✅ **Massive Scalability**          | Can handle petabytes of data with high-speed processing. |
| ✅ **SQL Interface**                | Familiar SQL for querying data.                          |
| ✅ **Machine Learning Integration** | Build and run ML models directly in SQL using BQML.      |
| ✅ **Pay-as-you-go Pricing**        | You only pay for the queries and storage you use.        |
| ✅ **Secure & Compliant**           | IAM, encryption, and audit logs built-in.                |


🔧 **Use Cases**

  Analyzing large datasets (e.g., sales, web traffic, logs)
  
  Building real-time dashboards and reports
  
  Integrating with AI/ML workflows
  
  Data lakehouse architecture
  
  Cloud-native ETL/ELT pipelines
  

### 📌 **Reasons to Use Vertex AI in GCP**

| Feature                              | Benefit                                                            |
| ------------------------------------ | ------------------------------------------------------------------ |
| ✅ **End-to-End ML Platform**         | Covers everything: data prep, training, deployment, and monitoring |
| ✅ **AutoML + Custom Training**       | Easy for beginners, powerful for experts                           |
| ✅ **Scalable Infrastructure**        | Train models on distributed GPUs or TPUs with minimal config       |
| ✅ **Integrated with BigQuery & GCS** | Easily move data across services                                   |
| ✅ **Built-in MLOps Tools**           | Pipelines, model registry, monitoring, explainability              |
| ✅ **Pre-trained Models & APIs**      | Use ready-made models for vision, text, translation, etc.          |
| ✅ **Secure & Compliant**             | Role-based access with IAM, logging, and encryption                |


🔧 **Example Use Cases**

  Predictive analytics for business metrics
  
  Image classification or object detection
  
  Natural Language Processing (chatbots, summarization)
  
  Time series forecasting
  
  Fraud detection and anomaly detection

### 📌 **Reasons to Use Cloud Run in GCP**

| Feature                 | Description                                           |
| ----------------------- | ----------------------------------------------------- |
| ✅ **Fully Managed**     | No servers to manage — just deploy and go             |
| ✅ **Container Native**  | Supports any language or framework via containers     |
| ✅ **Auto-Scaling**      | Instantly scales to 0 when idle, and up during spikes |
| ✅ **Pay per Use**       | Only pay while your code runs                         |
| ✅ **Fast Deployment**   | Deploy production APIs in minutes                     |
| ✅ **Easy Integration**  | Works with GCS, Pub/Sub, Firestore, Vertex AI, etc.   |
| ✅ **Secure by Default** | HTTPS endpoints, IAM integration, secrets management  |


🔧 **Example Use Cases**

  RESTful APIs
  
  Microservices
  
  Webhooks
  
  Background tasks
  
  ML model inference (paired with Vertex AI or TensorFlow)

### 📌 **Reasons to Use Connectors API in GCP**

| Benefit                      | Explanation                                                                   |
| ---------------------------- | ----------------------------------------------------------------------------- |
| 🔄 **Integration Made Easy** | Seamlessly connect to hundreds of third-party services                        |
| 🧩 **Reusable**              | Create and reuse connectors across multiple workflows or apps                 |
| 🔐 **Secure**                | Supports IAM, VPC Service Controls, encrypted credentials                     |
| ⚡ **Scalable & Managed**     | GCP handles scaling, auth, and maintenance                                    |
| 🔁 **Use Across GCP**        | Connect to connectors from Workflows, Apigee, AppSheet, Cloud Functions, etc. |
| 🧠 **Low/No Code**           | Ideal for both developers and citizen developers (via AppSheet)               |


🔧**Common Use Cases**
  
  Sync Salesforce contacts into BigQuery
  
  Fetch order status from SAP in Workflows
  
  Trigger workflows from ServiceNow
  
  Connect on-prem APIs to GCP using the HTTP connector




---

## 🌐 **Networking Concepts (Cloud)**

### 🔹 1. **Virtual Private Cloud (VPC)**

A **VPC** is a private, isolated section of the cloud where you deploy and manage your resources (VMs, databases, etc.). It includes:

* Subnets
* Routing
* Firewalls
* IP ranges

---

### 🔹 2. **Deployment Modes**

| Mode             | Description                                                                                  |
| ---------------- | -------------------------------------------------------------------------------------------- |
| **Default Mode** | The cloud provider automatically configures networking, firewall, etc.                       |
| **Custom Mode**  | You manually configure settings like IP ranges, subnets, firewall rules. Gives more control. |

---

### 🔹 3. **Subnets**

Subnets divide a VPC into smaller parts:

* **Public Subnet** – has access to the internet.
* **Private Subnet** – used for internal-only services.

---

### 🔹 4. **Port Numbers & Domain/IP Ranges**

* **Port Numbers**: Identify network services (e.g., 80 = HTTP, 443 = HTTPS).
* **Domain Range**: A group of websites (like `*.example.com`).
* **IP Range**: A block of IPs (e.g., `192.168.1.0/24`).

---

### 🔹 5. **Firewall Rules**

Control what traffic is allowed into or out of your VPC:

* **Ingress**: Traffic coming in.
* **Egress**: Traffic going out.
* **Config Rules**: Define which IPs and ports are allowed/denied.
* **Exclusion/Extension Access**: Limit access to specific users/services.

---

### 🔹 6. **Session-Based Login**

Uses login sessions to control user access (via cookies, tokens). Often used in web apps and dashboards.

---

### 🔹 7. **IP Address**

Every device/service in the network gets an IP (static or dynamic).

---

## 💾 **Cloud Storage Options**

### 🔹 8. **Types of Storage**

| Type               | Use Case                                                              |
| ------------------ | --------------------------------------------------------------------- |
| **Block Storage**  | Like a hard disk for VMs or DBs (e.g., GCP Persistent Disk, AWS EBS). |
| **Object Storage** | For files, images, backups (e.g., AWS S3, GCP Cloud Storage).         |
| **File Storage**   | Shared filesystem (e.g., NFS, Azure File Storage).                    |

---

### 🔹 9. **Service Account**

A special identity (not a user) used by apps to interact with cloud services securely.

* Used in automation, data pipelines, APIs.

---

### 🔹 10. **Content Account** (Likely Storage Account)

A container for your storage resources, like:

* Buckets
* Disks
* Filesystems

---

### 🔹 11. **Integrating Storage**

| Location          | How to Integrate                                                                |
| ----------------- | ------------------------------------------------------------------------------- |
| **Inside Cloud**  | Mount storage to VMs or connect via internal API. Use service accounts.         |
| **Outside Cloud** | Use signed URLs, public access, or VPN + firewall rules. Secure with IAM roles. |

---

## 🔄 **Pipeline Mechanisms**

### 🔹 12. **What Pipelines to Use**

Depends on your need:

| Goal                | Tools                                    |
| ------------------- | ---------------------------------------- |
| Data movement (ETL) | Apache Airflow, GCP Dataflow, AWS Glue   |
| CI/CD (deployment)  | GitHub Actions, GitLab CI, Jenkins       |
| ML pipeline         | Vertex AI Pipelines, SageMaker Pipelines |
| Custom processing   | Cloud Functions, Step Functions          |

Pipelines automate:

* Data extraction
* Transforming data
* Loading to storage or database
* Deploying code or models

---










### 📊 **GCP Pipelines for External ("Outside") Integration**

| **Use Case**                            | **Pipeline Mechanism**                           | **Why Use It**                                                                | **Example**                                  |
| --------------------------------------- | ------------------------------------------------ | ----------------------------------------------------------------------------- | -------------------------------------------- |
| Webhooks, third-party API triggers      | **Cloud Functions + Pub/Sub**                    | Lightweight, event-driven, easy to connect external systems                   | Receive external JSON and store in BigQuery  |
| API sequencing or multi-step workflows  | **Workflows**                                    | Securely calls APIs in sequence, with conditions and retries                  | Call external API → enrich data → send email |
| Scheduled external jobs (FTP/API)       | **Cloud Composer (Airflow)**                     | Python-based orchestration of complex workflows with retries and dependencies | Pull data from FTP → process → upload to GCS |
| Long-running or scalable API tasks      | **Cloud Run**                                    | Stateless, containerized, good for handling batch jobs or large external data | Fetch API data hourly → write to BigQuery    |
| Streaming data from external sources    | **Cloud Dataflow + Apache Beam**                 | Real-time data ingestion and transformation                                   | Read from Kafka topic → Transform → BigQuery |
| Connect SaaS (Salesforce, Shopify, etc) | **Fivetran / Stitch (3rd-party)**                | Prebuilt connectors for fast ELT into BigQuery                                | Sync data from Salesforce to BigQuery daily  |
| Access on-premises or other clouds      | **Cloud VPN / Interconnect + Composer/Dataflow** | Secure hybrid access to internal databases or servers                         | Fetch data from on-prem Oracle DB to GCS     |





