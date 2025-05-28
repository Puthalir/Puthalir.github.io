## 🧠 What are Large Language Models (LLMs)?

**LLMs** are deep learning models trained on large corpora of text to perform tasks involving human language. They learn patterns, grammar, facts, reasoning, and task-solving capabilities by training on internet-scale data.

Key Concepts:

| Term                       | Definition                                                                                                                          |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| **Parameters**             | The weights learned during training. The number of parameters indicates the capacity of the model. E.g., GPT-3 has 175B parameters. |
| **Tokens**                 | Chunks of words (e.g., "partner support" → 3 tokens). Token limits impact the size of input/output text the model can handle.       |
| **Context Window**         | The maximum number of tokens a model can process at once. E.g., PaLM 2 has up to 8k–32k tokens depending on the variant.            |
| **Prompt**                 | The input given to an LLM to generate a response. Includes instruction + optional context or examples.                              |
| **Temperature**            | Controls randomness in generation. Lower = deterministic, higher = creative.                                                        |
| **Top-k / Top-p Sampling** | Methods for sampling likely outputs to make generation more diverse or focused.                                                     |

---

## 🧰 What is **Vertex AI**?

**Vertex AI** is Google Cloud’s unified platform for ML and GenAI. It provides tools to:

* Train and deploy ML models (including LLMs)
* Serve foundation models via API (PaLM 2, Gemini)
* Build GenAI apps using **Generative AI Studio**, **Model Garden**, **Embeddings**, and **Extensions**

---

## 🧠 LLMs in Vertex AI: Core Capabilities

### 1. **Pretrained Foundation Models**

Vertex AI offers **Google’s foundation models** like:

| Model      | Purpose                                            |
| ---------- | -------------------------------------------------- |
| **PaLM 2** | Text generation, summarization, question answering |
| **Codey**  | Code generation and understanding                  |
| **Imagen** | Text-to-image generation                           |
| **Gemini** | Multimodal reasoning (text, image, vision)         |

You can use them **without training**, or **fine-tune/customize** using your data.

---

### 2. **Prompt Design & Tuning**

In **Vertex AI Studio**, you can:

* Test prompts (zero-shot, few-shot, chain-of-thought, RAG-based)
* Add guardrails
* Integrate grounding with your **knowledge base**
* Set model **temperature**, **token limits**, **stop sequences**, etc.

---

### 3. **Embeddings API**

Convert text to numerical vectors using `textembedding-gecko`. You can:

* Store vectors in a vector DB (e.g., FAISS, Pinecone)
* Use them for **semantic search**, **RAG**, **clustering**, **document similarity**

---

### 4. **Extensions & Tools**

* **Grounding with Vertex Search or BigQuery**
* **Code snippets** for calling APIs using Python, Node.js, etc.
* Integration with **Cloud Functions, Cloud Run, GKE, or Playbooks**

---

## 📊 How to Evaluate LLMs in Vertex AI

When selecting or evaluating a model:

| Aspect                   | Evaluation Method                                                              |
| ------------------------ | ------------------------------------------------------------------------------ |
| **Accuracy**             | Use benchmarks or golden datasets to validate output correctness.              |
| **Latency**              | Measure response time under real-world loads.                                  |
| **Cost**                 | Check per-token pricing. PaLM/Gemini charges per 1,000 tokens.                 |
| **Context Window**       | Longer windows are useful for summarization, chat history, large document RAG. |
| **Temperature Settings** | Low temperature for factual output, high for brainstorming.                    |
| **Model Size**           | Balance between capability and cost (e.g., PaLM-2-Bison vs PaLM-2-Gecko).      |
| **Guardrails**           | Safety, profanity filters, output restrictions.                                |
| **Integration**          | Check ease of using APIs with GCP services like BigQuery, Cloud Run, etc.      |

---

## 🧪 Interview-Proof Questions & Answers

### ✅ Q1: What are LLMs and how do they work?

**A**: LLMs are deep learning models trained on large text datasets. They learn to predict the next token in a sequence and can generate coherent responses based on input prompts. They use transformer-based architectures and are optimized over billions of parameters.

---

### ✅ Q2: How do you evaluate an LLM’s suitability in Vertex AI?

**A**: I evaluate based on:

* Task accuracy and relevance using benchmark queries
* Token and context window size
* Latency and response time
* Integration support (BigQuery, APIs)
* Guardrails and safety settings
* Cost per token generation and usage scalability

---

### ✅ Q3: How is prompt engineering handled in Vertex AI?

**A**: Vertex AI Studio allows interactive prompt design. I test different styles (zero-shot, few-shot, CoT), refine based on output quality, and apply prompt chaining or RAG where grounding is needed. I adjust temperature and stop sequences for control.

---

### ✅ Q4: What’s the difference between PaLM, Gemini, and Codey?

**A**:

* **PaLM**: Optimized for text-based NLP tasks.
* **Gemini**: Multimodal (can handle text + images + video).
* **Codey**: Tailored for code generation, refactoring, and understanding.

---

### ✅ Q5: Can you fine-tune LLMs in Vertex AI?

**A**: Vertex AI supports **instruction tuning** and **adapter-based fine-tuning** on certain models. It’s more efficient than retraining and works well for domain-specific use cases like Expedia’s partner support bots.

---

### ✅ Q6: How would you use embeddings in your Expedia project?

**A**: I use `textembedding-gecko` to embed knowledge base articles. These embeddings are stored in FAISS and used in a RAG pipeline to retrieve the most relevant context for a partner’s query. That context is fed to the LLM for an accurate, grounded response.

---

Would you like a **visual diagram** of this architecture or a **Vertex AI Studio walkthrough** to practice before your interview?

---

## 🔍 What is RAG?

**RAG (Retrieval-Augmented Generation)** is a GenAI technique where instead of asking an LLM to generate an answer from its trained parameters alone, we **retrieve relevant external information** and feed it to the LLM as context before asking it to generate a response.

Think of it as:

> 🔎 "Find useful facts" ➕ 🤖 "Use those facts to generate a helpful answer"

---

## 🛠️ Tools & Terms Explained

| **Term**          | **Meaning**                                                                             |
| ----------------- | --------------------------------------------------------------------------------------- |
| **Embeddings**    | A way to convert text into high-dimensional vectors that capture meaning.               |
| **Vector Store**  | A database that stores these vectors and allows similarity searches.                    |
| **Vector Search** | Finding vectors that are closest (most similar) to your query vector.                   |
| **FAISS**         | Facebook AI Similarity Search – an efficient open-source vector database.               |
| **LangChain**     | A Python framework that connects LLMs with tools like FAISS, APIs, memory, and prompts. |
| **Retriever**     | A component that searches the vector store and returns relevant documents.              |
| **Prompt**        | A structured message sent to the LLM, often including retrieved context.                |
| **RAG Pipeline**  | The end-to-end process: ingest → embed → store → retrieve → prompt LLM → respond.       |

---

## 🔁 RAG Pipeline: Step-by-Step with Python

### ✅ Step 1: Document Ingestion

Load your source documents (PDFs, websites, CSVs, knowledge base, etc.)

```python
from langchain.document_loaders import DirectoryLoader

loader = DirectoryLoader('./kb', glob="**/*.txt")
docs = loader.load()
```

---

### ✅ Step 2: Chunking the Text

Break large texts into manageable, meaningful chunks (e.g., 300–500 words).

```python
from langchain.text_splitter import RecursiveCharacterTextSplitter

splitter = RecursiveCharacterTextSplitter(chunk_size=500, chunk_overlap=100)
chunks = splitter.split_documents(docs)
```

---

### ✅ Step 3: Generate Embeddings

Convert each chunk to a vector using an embedding model (like Google’s `textembedding-gecko` or OpenAI’s `text-embedding-ada-002`).

```python
from langchain.embeddings import VertexAIEmbeddings  # For GCP
# or use OpenAIEmbeddings if using OpenAI

embedding = VertexAIEmbeddings()  # uses PaLM under the hood
```

---

### ✅ Step 4: Store in Vector DB (e.g., FAISS)

Index the vectorized chunks in a fast-searchable database.

```python
from langchain.vectorstores import FAISS

vectorstore = FAISS.from_documents(chunks, embedding)
vectorstore.save_local("expedia_index")
```

Later, you can reload with:

```python
vectorstore = FAISS.load_local("expedia_index", embedding)
```

---

### ✅ Step 5: Query Handling + Retrieval

Now, when a user asks something, we:

1. Embed the query.
2. Retrieve the top relevant chunks from the vectorstore.

```python
retriever = vectorstore.as_retriever(search_type="similarity", k=5)

user_query = "How do I cancel a partner booking?"
relevant_docs = retriever.get_relevant_documents(user_query)
```

---

### ✅ Step 6: Generate Answer with LLM

Feed the retrieved docs + user question to a language model.

```python
from langchain.chat_models import ChatVertexAI
from langchain.chains import RetrievalQA

llm = ChatVertexAI(temperature=0)
qa_chain = RetrievalQA.from_chain_type(
    llm=llm,
    retriever=retriever,
    chain_type="stuff"  # can also use "map_reduce", "refine"
)

response = qa_chain.run(user_query)
print(response)
```

---

## 🧠 Summary of Core Concepts

| **Component**                | **Purpose**                                                   |
| ---------------------------- | ------------------------------------------------------------- |
| **Embeddings**               | Turns text into numeric vectors to represent meaning.         |
| **Chunking**                 | Helps manage LLM context size and improves retrievability.    |
| **Vector DB (FAISS)**        | Fast similarity search engine over embedded chunks.           |
| **Retriever**                | Finds top-k relevant chunks based on query embedding.         |
| **LLM (VertexAI or OpenAI)** | Generates coherent and context-aware answers.                 |
| **Chain (LangChain)**        | Links together retrieval and generation into a full pipeline. |

---

## 📘 When to Use RAG?

* Your model needs **up-to-date** or **domain-specific** knowledge.
* You want to **avoid fine-tuning** but still ground the model in your data.
* Your input data changes frequently (e.g., partner support docs, KBs).

---

## 🧪 Bonus: Test Query

```python
query = "How does Expedia handle duplicate partner listings?"
print(qa_chain.run(query))
```

---

## 📦 Key Components of the Google Playbook

### 1. **Instruction Writing**

**What it is**: This defines the **core goal and behavior** of the agent.

**Structure**:

* Role: Who is the agent? (e.g., “You are Expedia Support Bot”)
* Goal: What is it trying to achieve? (e.g., “Help partners with reservation issues.”)
* Constraints: What must it avoid/do?

**Best Practices**:

* Be specific: "Only answer using Expedia partner policies"
* Use positive reinforcement: "You should always confirm before cancelling bookings"
* Include examples in the instruction for few-shot learning

---

### 2. **Prompt Engineering**

**What it is**: Designing the inputs (prompts) given to the LLM to control its output.

**Types of Prompts**:

* **Zero-shot**: Ask directly (“What is the refund policy?”)
* **Few-shot**: Include 2–3 examples in the prompt
* **Chain-of-thought**: Encourage step-by-step reasoning (“Let’s think step-by-step...”)
* **RAG-enhanced**: Include context from knowledge base or vector DB

**Best Practices**:

* Use structured formatting: JSON or Markdown improves LLM understanding
* Use `system`, `user`, `assistant` roles (like in OpenAI ChatML)
* Minimize ambiguity: avoid vague terms like "handle this"
* Tune temperature and top-p for control vs creativity

---

### 3. **Tool Usage (Actions / API Calling)**

**What it is**: Allowing the agent to use external APIs or functions (via Extensions, Webhooks, or ADK).

**Types of tools**:

* Internal REST APIs (e.g., Expedia’s `/partner/reservation/cancel`)
* Google tools (BigQuery, Cloud Functions, Dialogflow CX)
* Search connectors (Vertex AI Search, embeddings)
* Calculators, database query runners, calendar checkers

**Best Practices**:

* Define tool schema clearly (input/output JSON)
* Make tool descriptions self-documenting (e.g., “Cancels reservation using bookingId”)
* Test with simulated payloads before deploying to prod
* Handle API errors with fallback prompts

---

### 4. **Data Sources (Knowledge and Memory)**

**What it is**:

* **Knowledge sources**: Static or dynamic data like documents, help articles, FAQs
* **Memory**: Dynamic data stored during a session (conversation history, preferences)

**Tools**:

* **RAG (Retrieval-Augmented Generation)** for document-based Q\&A
* **Vertex AI Grounding with Search** or **embedding-based** retrieval (FAISS, Pinecone)
* **Session memory** in ADK or Playbooks

**Best Practices**:

* Keep knowledge base updated and versioned
* Use chunking for large docs (e.g., 200–500 tokens/chunk)
* Refresh memory after every few turns in long conversations
* Set a context window limit (e.g., 4K or 8K tokens)

---

### 5. **Guardrails and Safety**

**What it is**: Controlling model behavior to ensure it’s safe, helpful, and on-brand.

**Types**:

* **Content filters**: Block offensive/harmful output
* **System prompts**: Remind the agent to “avoid personal opinions”
* **Hardcoded flows**: Redirect specific queries to fallback logic

**Best Practices**:

* Use deny lists for PII / out-of-scope questions
* Add grounding instructions (“Don’t answer if you don’t know”)
* Test with red team prompts (e.g., “pretend to be a customer”)

---

### 6. **Testing and Evaluation**

**What it is**: A/B testing prompts, agents, and tool integrations.

**Key Areas**:

* **Accuracy**: Factual correctness
* **Grounding quality**: Whether output is backed by trusted source
* **Latency**: API + LLM response time
* **User satisfaction**: Human feedback, survey scores

**Best Practices**:

* Use eval prompts (e.g., 100 partner queries with golden answers)
* Set thresholds for confidence (based on model scoring, cosine similarity)
* Iterate with real-world user data

---

## ✅ Sample Agent Design: Expedia Partner Support Agent

| Component       | Example                                                                                                                                           |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Instruction** | “You are a helpful Expedia Partner Bot. Help users with booking changes, refunds, and check-in info using Expedia policy. Avoid making up rules.” |
| **Prompt**      | "Customer asks: ‘Can I get a refund if guest doesn’t show up?’\nYour response:"                                                                   |
| **Tool**        | `GET /api/reservation-status?bookingId=XYZ123`                                                                                                    |
| **RAG**         | Retrieve hotel cancellation policy from KB using vector search                                                                                    |
| **Memory**      | Store that the partner’s language is Spanish                                                                                                      |
| **Guardrail**   | “Do not make speculative or legally binding statements.”                                                                                          |

---

## 🎯 Summary

| Category           | Description                              | Best Practice                         |
| ------------------ | ---------------------------------------- | ------------------------------------- |
| Instruction        | Defines the agent’s goal and behavior    | Be concise and strict about scope     |
| Prompt Engineering | Controls how the agent responds          | Use few-shot + chain-of-thought       |
| Tool Integration   | Enables action-taking by the agent       | Clear schema, test rigorously         |
| Knowledge          | Provides grounded facts                  | Use RAG with chunked, embedded docs   |
| Memory             | Tracks context within a session          | Use sparingly to avoid hallucinations |
| Guardrails         | Prevents harmful or irrelevant responses | Use system messages and filters       |

---

## 🧠 Interview Questions and Sample Answers

### ✅ Q1: What are the core components of Google’s agent playbook?

**A**: The core components are instruction writing, prompt engineering, tool integration, grounding via data sources, memory management, and guardrails. Each ensures the agent performs accurately, safely, and contextually.

---

### ✅ Q2: How would you design an agent that can book or cancel Expedia reservations?

**A**: I would use:

* Clear system instructions defining the agent’s role
* Prompt templates with fallback handling
* A tool that invokes `/reservation/cancel` API
* RAG to fetch cancellation policies
* Guardrails to prevent unauthorized actions

---

### ✅ Q3: What’s the difference between grounding and memory?

**A**: Grounding provides **external context** (facts from documents or APIs), while memory retains **session-specific info** (like prior messages, preferences).

---

## 🧠 Topic: Application Development Kit (ADK) with Python

> **ADK (Application Development Kit)** is a **Python-based framework from Google** used to define, orchestrate, and run agentic workflows powered by large language models (LLMs) in **Vertex AI Agent Builder** and **Playbooks**.

It enables **programmatic agent design** and is particularly useful when:

* You want full **control in code** (Python) over what an agent does.
* You’re integrating **custom logic, external APIs**, RAG, and multiple tools.
* You want to **deploy reusable agents** inside Dialogflow, Playbooks, or standalone Python apps.

---

## 🔧 What Is ADK with Python?

ADK in Python allows you to:

* Define **instructions** for your agent (who it is, what it can do).
* Register **tools** (functions, webhooks, APIs).
* Implement **control flow logic** (sequential, conditional, loops).
* Call external services, process data, or query vector databases (for RAG).
* Return formatted responses with JSON or markdown.

---

## ⚙️ Key Components of ADK in Python

| Component        | What It Is                           | Example                                    |
| ---------------- | ------------------------------------ | ------------------------------------------ |
| `LLMFunction`    | The LLM-powered step/decision maker  | Generates text or decisions using a prompt |
| `Tool`           | A function the agent can call        | E.g., `def get_booking_status(booking_id)` |
| `Action`         | A step that uses a tool or LLM       | Calls a tool and stores its result         |
| `Flow`           | A sequence of actions forming a task | Step 1 → Step 2 → Step 3                   |
| `Variables`      | Agent memory/context across steps    | Stores user intent, API response           |
| `PromptTemplate` | Defines how input is passed to LLM   | Few-shot, chain-of-thought formats         |

---

## 🛠️ Sample ADK Agent (Python)

```python
from genai_core.agents import Agent
from genai_core.tools import tool
from genai_core.llms import LLMFunction
from genai_core.flows import Flow, Action

@tool
def get_booking_status(booking_id: str) -> str:
    """Get status of a booking from Expedia's partner API"""
    # Simulated external call
    return "Confirmed"

agent = Agent(
    instructions="You are an Expedia Partner Bot. Help partners with booking info."
)

check_status_llm = LLMFunction(
    name="generate_booking_status_prompt",
    instructions="Generate a user-friendly status message using booking status.",
    prompt_template="The booking status is: {{ booking_status }}. Generate a message."
)

booking_flow = Flow([
    Action(tool=get_booking_status, input_keys=["booking_id"], output_key="booking_status"),
    Action(tool=check_status_llm, input_keys=["booking_status"], output_key="response")
])

response = booking_flow.run(inputs={"booking_id": "XYZ123"})
print(response["response"])
```

---

## 📂 ADK YAML vs ADK Python: Key Differences

| Feature     | ADK YAML Config                                  | ADK Python                          |
| ----------- | ------------------------------------------------ | ----------------------------------- |
| Format      | Declarative YAML                                 | Full Python scripting               |
| Use Case    | Config-driven deployments (used in Playbooks UI) | Custom agents or microservices      |
| Flexibility | Good for standard workflows                      | Best for complex logic and loops    |
| Deployment  | Agent Builder / Playbooks                        | Cloud Functions, Cloud Run, GKE     |
| Debugging   | Harder (visual or log based)                     | Easier with breakpoints and testing |
| Integration | UI-based                                         | Programmatic and CI/CD friendly     |

> **Best Practice**: Use ADK YAML for quick Playbook prototypes; use ADK Python when you need full control or reusable services.

---

## 🤖 Using ADK to Build Playbook-Based Agents

**Playbooks** in GenAI Studio can now **load ADK YAML files** to define multi-step agents. But you can also deploy **ADK Python agents as backends** for Playbooks via Cloud Run or Functions.

✅ Steps:

1. Write and test ADK Python agent locally
2. Wrap as a REST API with FastAPI or Flask
3. Deploy to Cloud Run / GKE / AWS EKS (if external)
4. In Playbooks, **use Extension → REST API** to call your agent

---

## 🗣️ Using ADK to Build Dialogflow Agents

Dialogflow CX doesn't natively run ADK, but you can:

* Host your ADK agent (Python) as a webhook
* Configure the **Dialogflow fulfillment** to call the ADK service
* Let Dialogflow handle NLU, and ADK handle response generation or orchestration

✅ Pattern:

1. Dialogflow detects intent (e.g., “cancel booking”)
2. Calls webhook (Cloud Run / EKS) → ADK agent
3. ADK orchestrates logic, tools, and returns a structured message
4. Dialogflow shows response to user

---

## 🧱 Deployment Options for ADK Python

| Platform                 | Use Case                                                  |
| ------------------------ | --------------------------------------------------------- |
| **Cloud Run**            | Stateless REST microservices (simple & scalable)          |
| **GKE (EKS)**            | Complex multi-agent systems (multi-service orchestration) |
| **Vertex AI Extensions** | If agent is simple and runs inside Playbook               |
| **Dialogflow Webhooks**  | For voice/chat NLU-based interfaces                       |
| **FastAPI local**        | For debugging & development                               |

---

## 🧪 Interview-Ready: Example Q\&A

### Q1: What is the ADK in the context of GenAI agent building?

**A**: ADK is Google's Python-based SDK for building intelligent agents that can orchestrate tools, generate responses using LLMs, integrate with APIs, and maintain context. It’s used for advanced control beyond what Playbooks or Dialogflow offer out of the box.

---

### Q2: How is ADK in Python different from ADK YAML configs?

**A**: YAML configs are declarative and typically used in Playbooks or Vertex Agent Builder UI. ADK Python is imperative and provides full scripting flexibility, better debugging, and integration with CI/CD or microservices.

---

### Q3: How do you use ADK Python in Dialogflow?

**A**: Deploy ADK Python agent as a webhook on Cloud Run or GKE. Dialogflow CX then calls this webhook during fulfillment. ADK handles orchestration, external APIs, and structured replies.

---

### Q4: Can you use ADK with Playbooks?

**A**: Yes. You can either use YAML-based ADK flows directly in Playbooks or call external ADK Python agents via REST API Extensions in Playbook steps.

---

### Q5: What’s the advantage of ADK Python over plain prompt chaining?

**A**: ADK provides structure, control, memory, state handling, and easier integration with tools and APIs. It supports conditional logic, loops, and modular flows—beyond what basic prompt chaining offers.

---
