### GENAI PROJECT DESCRIPTION BREAKDOWN AND POSSIBLE INTERVIEW QUESTIONS

---

### ✅ **1. Enhanced Project Breakdown (for Follow-Up Interview Questions)**

> As a mid-level ML Engineer at Expedia Group, I was part of a cross-functional team that built conversational AI agents called *Help Me Bots* for the Partner Central portal. Our goal was to reduce partner support ticket load and improve issue resolution time through AI-powered automation. The bots were built using **DialogFlow CX**, integrated with **LangChain** and **LLMs** like **GPT-4** and **Gemini** for intelligent responses. I handled the ML pipeline implementation using **Vertex AI**, developed classification models for routing and triaging partner queries, and worked on integrating GCP APIs for data handling and real-time analytics with **BigQuery**. My work directly contributed to improving the accuracy and responsiveness of the bots while ensuring scalability and reliability through CI/CD and version-controlled deployments.
>
> One key challenge was ensuring the bots handled diverse partner queries with context-aware and compliant responses. To address this, I used **retrieval-augmented generation (RAG)** to provide LLMs with relevant document snippets, improving both factuality and context. I also used **BigQuery** to evaluate bot interactions and refine ML features used in training classification models. My contributions helped cut partner support resolution times by approximately 20%.

---

### ✅ **2. Refined & Expanded Interview Q\&A Set**

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
