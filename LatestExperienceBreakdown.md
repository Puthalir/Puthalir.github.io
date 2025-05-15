### GENAI PROJECT DESCRIPTION BREAKDOWN AND POSSIBLE INTERVIEW QUESTIONS

---

### ✅ **1. PROJECT BREAKDOWN**

> As a ML Engineer at Expedia Group, I was part of a cross-functional team that built conversational AI agents called *Help Me Bots* for the Partner Central portal. Our goal was to reduce partner support ticket load and improve issue resolution time through AI-powered automation. The bots were built using **DialogFlow CX**, integrated with **LangChain** and **LLMs** like **GPT-4** and **Gemini** for intelligent responses. I handled the ML pipeline implementation using **Vertex AI**, developed classification models for routing and triaging partner queries, and worked on integrating GCP APIs for data handling and real-time analytics with **BigQuery**. My work directly contributed to improving the accuracy and responsiveness of the bots while ensuring scalability and reliability through CI/CD and version-controlled deployments.
>
> One key challenge was ensuring the bots handled diverse partner queries with context-aware and compliant responses. To address this, I used **retrieval-augmented generation (RAG)** to provide LLMs with relevant document snippets, improving both factuality and context. I also used **BigQuery** to evaluate bot interactions and refine ML features used in training classification models. My contributions helped cut partner support resolution times by approximately 20%.

---

### ✅ **2. INTERVIEW Q\&A**

---

**Q1: What is DialogFlow CX and how is it different from DialogFlow ES?**

**A:** DialogFlow CX is an advanced version of DialogFlow ES that offers a visual, flow-based interface for designing complex conversations. Unlike ES, which is state-less and intent-centric, CX supports multi-turn conversations using state machines and flow-based design, making it better for large-scale virtual agents with multiple conversation paths. In our project, we used DialogFlow CX to manage complex partner interaction flows, handle contextual handovers between topics, and integrate webhooks for real-time data retrieval.

---

**Q2: How did you integrate LLMs into the system?**

**A:** I integrated **LLMs like GPT-4 and Gemini** using a **retrieval-augmented generation (RAG)** approach. First, relevant partner documentation (FAQs, policy manuals, support articles) was indexed using vector embeddings. When a partner query came in, a retrieval pipeline (built with LangChain) fetched relevant documents and passed them along with the query to the LLM through an API. This ensured that the LLM’s responses were grounded in authoritative Expedia documents, improving accuracy and reducing hallucinations. We deployed this pipeline on GCP services, ensuring secure handling of partner data and reliable inference times.

---

**Q3: What is the difference between Random Forests and Gradient Boosting Machines (GBMs)?**
**A:**

* **Random Forest** builds multiple decision trees in parallel using bootstrapped datasets and averages their predictions. It reduces variance and is robust to overfitting.
* **Gradient Boosting Machines (e.g., XGBoost)** build trees sequentially, with each tree correcting the previous one’s error. This typically leads to better accuracy but can be more prone to overfitting and is computationally more expensive.

In our project, I used **Random Forest** when performance and simplicity were key and **GBM** when we needed fine-grained prediction accuracy for complex query classification tasks.

---

**Q4: What were the main components of your ML pipeline on Vertex AI?**

**A:** The pipeline consisted of data ingestion from BigQuery, preprocessing using pandas and scikit-learn, model training (Random Forest or GBM), evaluation, and model deployment using Vertex AI’s managed endpoint services. We monitored performance using Vertex AI Model Monitoring, and periodically retrained the model based on bot feedback logs to improve classification performance.

---

**Q5: How did you use LangChain in this project?**

**A:** LangChain helped orchestrate prompt templates, memory management, and retrieval steps in our LLM-based assistant. Specifically, I used LangChain's document loaders and retrievers to fetch relevant partner documents, then chained them with prompt templates that were passed to LLMs like GPT-4 via API calls. It was crucial in setting up retrieval-augmented generation (RAG) and made our integration modular and testable.

---

**Q6: How did BigQuery support your work?**

**A:** BigQuery was central to our data analytics. I used it to analyze chat logs, extract frequent intents, identify low-confidence responses, and measure bot performance. These insights helped retrain ML models and refine conversation flows in DialogFlow CX. BigQuery’s scalability allowed us to handle millions of interaction records efficiently.

---

**Q7: How did you collaborate with others in this role?**

**A:** I worked closely with NLP engineers, product managers, and customer success teams. In our Agile sprints, I collaborated on DialogFlow agent design, ML model evaluation reviews, and deployed features via CI/CD pipelines. My role was hands-on and technical, contributing directly to backend services, bot enhancements, and data pipelines.

---

**Q8: What CI/CD practices did you follow for model and bot deployment?**

**A:** I followed Git-based versioning, containerized services with Docker, and used GCP’s Cloud Build for CI/CD. For ML models, we used Vertex AI Pipelines and registered models with model registries. For DialogFlow, we tested webhook services locally and deployed them to Cloud Run with versioned configurations.

---
### ✅ **3. ADDITIONAL QUESTIONS THAT CAN BE ASKED** 
---

### 1. **DialogFlow Specifics**

**Q: How do you handle context management and slot filling in DialogFlow CX?**

**A:**
In DialogFlow CX, context management is handled through state machines where each state represents a part of the conversation flow. Contexts are preserved across turns using session parameters and flow transitions, allowing the bot to maintain dialogue state. Slot filling is implemented using entity extraction with prompts to collect required parameters from users. In our Help Me Bots, this enabled smooth multi-turn conversations where missing info was dynamically requested and stored, improving query resolution accuracy.

---

**Q: What are webhooks in DialogFlow, and how did you use them in your bots?**

**A:**
Webhooks are HTTP callbacks that allow DialogFlow agents to invoke external services for fulfillment during conversation. We used webhooks to connect our DialogFlow CX agents with backend ML models and databases on GCP. This allowed dynamic retrieval of partner data and real-time intent classification, enabling responses based on live business logic rather than static intents.

---

**Q: How do you debug and test DialogFlow agents before deployment?**

**A:**
We use the DialogFlow CX simulator extensively for iterative testing of conversation flows and intents. Additionally, we test webhook endpoints locally with tools like ngrok and integrate unit tests on webhook handlers. After deployment, we monitor real user conversations via DialogFlow logs and BigQuery analytics to detect and fix issues quickly.

---

### 2. **GCP & Vertex AI**

**Q: Explain how you monitored and managed deployed ML models on Vertex AI.**

**A:**
Vertex AI provides model monitoring tools to track prediction drift and data quality. We set up alerts for changes in input data distributions and model performance metrics. Models were versioned, and retraining pipelines triggered based on monitoring signals or new labeled data from bot interactions, ensuring sustained accuracy.

---

**Q: How do you ensure security and compliance when handling sensitive partner data in GCP?**

**A:**
We followed the principle of least privilege using IAM roles, ensuring service accounts had only necessary permissions. Data at rest was encrypted in Cloud Storage and BigQuery. Sensitive data was anonymized where possible, and all API calls went through secured VPC Service Controls. Compliance audits and logging helped maintain transparency.

---

**Q: Describe the benefits and trade-offs of using Cloud Run vs GKE for your webhook services.**

**A:**
Cloud Run offers serverless deployment with automatic scaling and minimal infrastructure management, which is ideal for event-driven webhook services with variable load. GKE provides more control over the environment and is better for complex, stateful workloads but requires more DevOps overhead. For our project, we primarily used Cloud Run for rapid deployment and scalability.

---

### 3. **Machine Learning & Model Development**

**Q: What criteria do you use to select between different ML algorithms (Random Forest vs GBM)?**

**A:**
I choose Random Forest when the priority is robustness, interpretability, and faster training with less risk of overfitting. GBM is preferred for higher predictive accuracy when tuning is feasible, especially on imbalanced or complex datasets, but it requires more careful hyperparameter tuning to avoid overfitting.

---

**Q: How do you evaluate model performance and deal with imbalanced classes in classification?**

**A:**
I use metrics beyond accuracy, such as precision, recall, F1-score, and AUC-ROC, which better capture performance on imbalanced data. Techniques like SMOTE, class weighting, and stratified sampling help balance training. In the project, we monitored false negatives carefully to reduce missed partner queries.

---

**Q: Can you describe your feature engineering process for partner query classification?**

**A:**
Features included tokenized text embeddings, n-grams, part-of-speech tags, and metadata like query time and partner type. We used TF-IDF vectorization and experimented with pretrained embeddings. Feature importance analysis guided iterative refinement.

---

### 4. **Large Language Models and LangChain**

**Q: What challenges did you face when integrating LLMs into existing systems?**

**A:**
Main challenges were latency due to external API calls, cost of LLM usage, and ensuring responses stayed on-topic without hallucinations. We mitigated these by caching frequent queries, implementing retrieval-augmented generation to ground responses, and limiting token usage with prompt engineering.

---

**Q: How does LangChain simplify the development of complex LLM applications?**

**A:**
LangChain abstracts common LLM components like prompt templates, memory management, and document retrieval. This modularity speeds up development and testing of retrieval pipelines and chaining multiple LLM calls, making it easier to build scalable, maintainable GenAI workflows.

---

### 5. **Data Engineering & Analytics**

**Q: How did you leverage BigQuery for model improvement and bot performance analysis?**

**A:**
BigQuery enabled scalable querying of millions of chat logs to identify intent distribution, low-confidence responses, and user drop-offs. These insights informed retraining data selection and intent refinement, closing the feedback loop between analytics and ML development.

---

**Q: Explain your approach to building scalable data pipelines for ML workflows.**

**A:**
I designed pipelines to ingest data from Cloud Storage and BigQuery, apply preprocessing and feature extraction using Apache Beam or pandas, then feed cleaned data into Vertex AI pipelines. The modular design supported incremental updates and automated retraining triggered by new data.

---

### 6. **General and Behavioral**

**Q: Tell me about a challenging bug or issue you encountered during bot development and how you resolved it.**

**A:**
One issue was inconsistent context loss in multi-turn conversations leading to incorrect responses. I traced it to session parameter resets caused by webhook timeouts. The fix involved optimizing webhook response times and adding fallback intents to gracefully recover lost context, improving overall stability.

---

**Q: How do you prioritize feature requests and bug fixes in a team environment?**

**A:**
I prioritize based on impact to partner experience and business KPIs, coordinating with product and support teams. Bugs causing incorrect info or outages get highest priority, followed by features improving automation or reducing resolution time. Agile sprints and regular grooming help keep the backlog aligned.

---

