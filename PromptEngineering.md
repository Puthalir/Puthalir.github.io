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

In context with expedia project 

Great! Here's a complete example of a **Playbooks YAML prompt block** that combines:

* Retrieval-Augmented Prompting
* Role-Oriented Instructional Prompting
* Guardrail Prompts for safety
* OpenAPI integration fallback (if you want to connect to backend APIs)

This is designed to be part of a `prompt_template.yaml` inside your Playbooks config folder (`prompt_templates/`).

---

### 📄 `prompt_templates/help_bot_prompt.yaml`

```yaml
name: expedia_partner_help_prompt
description: Prompt for Expedia Partner Support Bot using contextual grounding and guardrails
type: prompt_template
template:
  system_message: |
    You are Expedia’s Partner Help Assistant. You assist verified Expedia property partners with their support queries related to onboarding, payout issues, listings, taxes, and account settings.

    - Always be polite, professional, and concise.
    - Confirm understanding of the partner’s issue before suggesting a solution.
    - Use only the context provided to answer the question.
    - If the answer is not found in the context, say:
      “I couldn't find a definitive answer. Would you like me to connect you to a support agent?”
    - Never guess or provide legal, financial, or compliance advice.
    - If the query is about something unrelated to Expedia or contains inappropriate content, respond with:
      “I'm here to assist with Expedia Partner-related queries only.”

  user_message: |
    Context:
    {{context}}

    Partner Question:
    {{input}}

  variables:
    - context
    - input
```

---

### 🔒 Guardrails Embedded

The guardrails here include:

* Avoiding hallucination (by restricting to context only)
* Handling unknowns gracefully
* Filtering out off-topic/inappropriate input
* Blocking legal/compliance advice
* Offering escalation fallback

---

### 🧠 How to Use This in a Playbook

In your **playbook.yaml**, reference this template like this:

```yaml
steps:
  - name: generate_answer
    type: LLM_GENERATE
    model: gemini-pro
    prompt_template: help_bot_prompt
    inputs:
      context: ${retrieved_knowledge}
      input: ${partner_query}
```

---

### 🤖 Retrieval Integration

Make sure your Playbook also includes a `RETRIEVE_KNOWLEDGE` step before this, like:

```yaml
- name: retrieve_docs
  type: RETRIEVE_KNOWLEDGE
  knowledge_connector: expedia_support_kb
  query: ${partner_query}
  output: retrieved_knowledge
```

---

### ✅ Benefits of This Setup

| Feature                  | Benefit                                   |
| ------------------------ | ----------------------------------------- |
| Context-grounded answers | Reduces hallucination                     |
| Role clarity             | Keeps tone consistent                     |
| Guardrails               | Ensures safe, brand-aligned responses     |
| Escalation fallback      | Improves user trust                       |
| Modular prompt           | Easy to evolve for other teams or domains |

---

