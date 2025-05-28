Here is a **Prompt Engineering Cheatsheet** perfect for interviews, quick reference, or practice.

---

# 🧠 Prompt Engineering Cheatsheet

---

## ✅ **Core Concepts**

| Term                       | Description                                                   |
| -------------------------- | ------------------------------------------------------------- |
| **Prompt**                 | The input given to an LLM to generate a desired response.     |
| **Instruction Tuning**     | Training LLMs to follow instructions (e.g., ChatGPT, Claude). |
| **Few-shot Prompting**     | Giving a few examples to guide model behavior.                |
| **Chain-of-Thought (CoT)** | Prompting the model to reason step-by-step.                   |
| **Role Prompting**         | Asking the model to act as an expert (e.g., doctor, lawyer).  |
| **Formatting Prompt**      | Requesting structured output (e.g., JSON, table).             |

---

## 🛠️ **Prompting Techniques**

### 1. **Zero-Shot Prompting**

> Ask a question without giving any examples.
> **Example:**
> "Translate 'Hola' to English."

---

### 2. **Few-Shot Prompting**

> Provide a few input/output pairs.
> **Example:**

```
Translate the following:
- Bonjour → Hello
- Merci → Thank you
- Au revoir → Goodbye
- Lundi → ?
```

---

### 3. **Chain-of-Thought Prompting**

> Encourage the model to reason step by step.
> **Example:**

```
Question: If I have 3 red apples and buy 2 green apples, how many apples do I have?
Let's think step by step.
```

---

### 4. **Instruction Prompting**

> Direct command in natural language.
> **Example:**
> "Summarize this text in 3 bullet points using a formal tone."

---

### 5. **Role Prompting**

> Assign the model a role to simulate expertise.
> **Example:**
> "You are a tax consultant. Explain section 179 of the IRS code."

---

### 6. **Output Format Prompt**

> Guide the structure of the response.
> **Example:**
> "Return the result as JSON with keys: `date`, `amount`, `name`."

---

## 💬 **Common Prompt Templates**

| Goal               | Template                                                              |
| ------------------ | --------------------------------------------------------------------- |
| Summarization      | "Summarize the text below in 3 bullet points."                        |
| Classification     | "Categorize this document as finance, legal, or marketing."           |
| Data extraction    | "Extract the person's name, date, and amount from this text."         |
| Sentiment analysis | "What is the sentiment (positive/negative/neutral) of this sentence?" |
| Conversational AI  | "You are a helpful assistant. Answer politely and concisely."         |

---

## 🧪 **Advanced Prompt Patterns**

| Pattern           | Description                                        |
| ----------------- | -------------------------------------------------- |
| **ReAct**         | Combines reasoning and tool use                    |
| **PAL**           | Uses Python code to solve (Program-Aided Language) |
| **Self-Ask**      | Model breaks task into sub-questions               |
| **System + User** | Used in chat models like ChatGPT                   |

---

## ⚙️ **Tips for Better Prompts**

* ✅ Be **explicit and detailed** in what you ask.
* ✅ Use **delimiters** (\`\`\`, """ etc.) to isolate text.
* ✅ Include **clear examples** when using few-shot prompts.
* ✅ Use **"Let's think step by step"** for better reasoning.
* ✅ Ask for output in **specific format** (JSON, bullet points, code).

---

## 🔐 Prompt Security (Awareness)

| Concept              | Description                                         |
| -------------------- | --------------------------------------------------- |
| **Prompt Injection** | Malicious input overrides system prompt             |
| **Mitigation**       | Escape inputs, verify context, use retrieval guards |

---

## 🧠 Memory-Friendly Prompts (for small context LLMs)

* Summarize previous conversation before each new query.
* Use embeddings to select relevant context (used in RAG).

---

## 📚 Tools to Practice

| Tool                     | Use                          |
| ------------------------ | ---------------------------- |
| OpenAI Playground        | Try prompts interactively    |
| LangChain PromptTemplate | Modular prompt building      |
| PromptPerfect            | Optimize prompts with AI     |
| LlamaIndex               | Use prompts in RAG pipelines |
| PromptLayer              | Track and version prompts    |

---
