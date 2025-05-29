Here are some **realistic follow-up interview questions** based on your Expedia GenAI project deep dive, along with **sample answers** tailored to your experience:

---

### ✅ **1. How did you decide when to use LLM vs static responses in DialogFlow CX?**

**Sample Answer:**
Great question. We followed a simple rule: if the query could be resolved with deterministic backend logic—like checking if a listing was inactive or an image was missing—we used static or webhook-generated responses. But when the query was vague, context-dependent, or required understanding policies or documents, we routed it to our LangChain + LLM pipeline. We also logged fallback or low-confidence cases from DialogFlow to continuously refine our LLM triggers.

---

### ✅ **2. Can you explain why you used LangChain instead of directly calling OpenAI or Gemini APIs?**

**Sample Answer:**
Absolutely. LangChain gave us a modular way to manage the full LLM pipeline. It handled document retrieval, prompt construction, tool chaining, and memory, all within a structured agent setup. For example, in our `listing_not_found` scenario, LangChain retrieved help articles, combined them with backend data, and built prompts dynamically. Doing all that manually with raw OpenAI calls would’ve been much harder to manage and scale.

---

### ✅ **3. How did you evaluate and improve the accuracy of the bot responses over time?**

**Sample Answer:**
We logged all queries, responses, and confidence scores into BigQuery and reviewed high-volume intents weekly. We built Tableau dashboards showing metrics like fallback rate, response time, and escalation triggers. We also ran human-in-the-loop evaluations for LLM responses—sampling outputs and comparing them to ideal answers. If responses were vague or incorrect, we updated our RAG retriever, refined prompts, or added fallback logic.

---

### ✅ **4. How did you prevent hallucination or incorrect answers from the LLM?**

**Sample Answer:**
We used a combination of techniques. First, RAG helped ground the LLM by injecting relevant documents directly into the prompt. Second, our instructional prompts clearly told the LLM to only use provided content. Third, we added guardrail instructions like: “If unsure, recommend contacting support.” We also did prompt testing in staging and used strict filters before moving new prompts to production.

---

### ✅ **5. What challenges did you face while using Playbooks, and how are they different from DialogFlow CX flows?**

**Sample Answer:**
Playbooks allowed us to build agentic workflows—multi-step tasks like check status → validate images → recommend fix. Unlike DialogFlow CX, which is great for structured conversations, Playbooks let us define decision logic and tool usage declaratively in YAML. The main challenge was debugging intermediate steps and ensuring safe fallbacks when an action failed. We built test harnesses and logging checkpoints to monitor this in real time.

---

### ✅ **6. What happens when the bot can’t resolve a query? Do you escalate?**

**Sample Answer:**
Yes, we built escalation logic into both DialogFlow and the LangChain agent. If the webhook or LLM response confidence was low, or if the intent had an explicit escalation path, the bot would log the conversation context and hand off to a human agent, sometimes creating a support ticket automatically. We also added a clear message saying, “Let me connect you to support for further help.”

---

### ✅ **7. How did you handle updates to DialogFlow agents across environments?**

**Sample Answer:**
Since we used Google’s ADK, we defined agents and flows as YAML configs. These were stored in Git, and deployments were handled using the ADK CLI. We had separate branches for dev, staging, and prod. CI/CD workflows validated schema, ran unit tests on the flows, and then deployed to the right DialogFlow CX project using service accounts.

---

### ✅ **8. Why did you choose GKE over Cloud Run for webhook and LangChain service hosting?**

**Sample Answer:**
Initially, we tried Cloud Run for quick deployments. But as our LangChain agents got heavier—with multiple tools, memory, and document retrievers—we needed more control over CPU/memory tuning, auto-scaling, and networking. **GKE** with **HPA (Horizontal Pod Autoscaler)** gave us fine-grained scaling and observability, which was critical during partner traffic spikes.

---

### ✅ **9. How did you test LLM behavior before deploying changes to production?**

**Sample Answer:**
We had a dedicated staging environment where we tested new prompts, document changes, and LangChain logic. We used mock user queries based on real production logs, and validated responses manually and using test scripts. For critical intents, we ran A/B tests—comparing existing prompts with improved ones—and only deployed updates after seeing better quality and fallback rates.

---

### ✅ **10. What would you do differently if you rebuilt this project from scratch?**

**Sample Answer:**
I’d probably invest earlier in a more centralized feedback loop for prompt performance—like having UI buttons for users to rate answers or flag confusion. Also, I’d explore using vector databases like **Pinecone or Weaviate** instead of relying only on BigQuery for embeddings, since those offer faster semantic search at scale. Otherwise, I think the stack we chose—ADK, DialogFlow CX, LangChain, GKE—was solid and flexible.

---
