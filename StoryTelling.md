
## 🙋‍♀️ **Self Introduction (2–3 mins)**

Hi, my name is Puthali Ravella. I’m currently based in Seattle and I’ve been working in the AI and Data space for around 5 years now. My journey started with data engineering, then moved into data science, and now I’m fully focused on conversational AI and Generative AI. I enjoy building intelligent systems that solve real problems using tools like DialogFlow CX, LangChain, LLMs, and GCP.

I began my career at **Capgemini**, where I worked on banking data projects. I built pipelines, worked with large datasets, and created dashboards to help business teams make better decisions. It gave me a solid foundation in how to handle and analyze real-world data.

After that, I joined **Maruti Suzuki** as a Data Scientist. I worked in the marketing analytics team where I built models to predict campaign performance and segment customers based on behavior. I automated a lot of the data processing using Python and helped the team get insights faster and make data-backed decisions.

Currently, I’m working at **Expedia Group** as a GenAI Engineer. My work here is focused on building smart virtual agents for partner support using DialogFlow CX, LangChain, and Google Cloud. I build end-to-end solutions—from designing conversation flows to deploying Python webhooks on Kubernetes, integrating LLMs for smarter responses, and continuously improving them using partner feedback and data analysis. We’re also testing agentic playbook-based flows to make our bots more autonomous and task-capable.

---

## ✈️ **Expedia Project Deep Dive (Story-style, 5–7 mins)**

Sure, I’d love to walk you through one of my main projects at Expedia, which was focused on building conversational AI bots for partner support.

### **Project Background**

So the problem we were trying to solve was that hotel and travel partners often reached out to us with common questions like, “Why isn’t my property showing up in search results?” or “How do I fix my availability?” These queries were traditionally handled through email or support tickets, which could take time and effort on both sides. Our goal was to build an AI assistant—what we called the “Help Me Bot”—that could instantly help partners with these queries inside the Expedia Partner Central portal.

### **Approach & Flow**

We started by designing this solution using **DialogFlow CX**. It allowed us to define very structured conversation flows, where we could map partner questions to specific intents. For example, one of the most frequent questions we saw was around a property not showing up in search results. Internally, we handled this under a `listing_not_found` intent.

Now, let’s say a partner typed in, “Why is my hotel not visible?” DialogFlow would first pick that up and trigger this intent. At this point, the bot needed more than a basic FAQ-type response—it had to understand the partner's situation, check the property’s actual status, and then give a meaningful answer. That’s where we brought in Python-based webhooks.

These webhooks were deployed on **Google Kubernetes Engine**, and they would reach out to internal Expedia APIs to fetch live data about that specific property—things like whether the listing was active, if images were missing, or if room rates were set incorrectly. If we found a clear reason, like missing images, the bot would explain that right away to the partner.

But in many cases, the query wasn’t straightforward, or the partner would ask a follow-up question. That’s when we started bringing in **LLMs**, using frameworks like **LangChain** and models like **GPT-4** or **Gemini**. These large language models helped us provide more context-aware answers, especially by combining system data with our internal documentation.

Now, to make sure the LLMs responded accurately and safely, we put a lot of focus on **prompt engineering**. We didn’t just send in raw questions. We followed a layered approach.

First, we used **RAG-based prompting**, or Retrieval-Augmented Generation. This meant that before sending the prompt to the model, we would first look up the relevant documentation—maybe a help article or an internal policy—and include it in the prompt. So, the model wasn’t hallucinating or guessing; it was answering based on real data.

Second, we used **instructional prompts** where we told the model exactly how to behave. For example, we’d say something like, “You are an Expedia support assistant. Only provide answers based on the attached content. Keep your response short and polite.” This helped maintain a consistent tone and format across all responses.

Third, we implemented **guardrail prompts**. These were simple but powerful. They would tell the model, “If you don’t have a clear answer, please respond with: ‘I recommend contacting support for further help.’” This avoided situations where the model might guess and give a wrong answer, which could create confusion for the partner.

We also made the prompt generation dynamic. Based on the user's question and the intent matched in DialogFlow, we would build a custom prompt on the fly in Python—embedding the right documents and past conversation context. This helped in handling multi-turn queries smoothly.

We also collected data from all interactions using **BigQuery**—this helped us analyze which intents were performing well, where drop-offs were happening, and which parts of the conversation needed refining. This feedback loop was critical in improving both the bot flows and our prompts.

### **Recent Enhancements**

More recently, we’ve been working on taking these bots to the next level using something called **Playbooks**. Instead of just answering a question, playbook-powered bots can follow a full process—like checking if the listing is active, verifying the calendar settings, and even suggesting next steps automatically. These agentic workflows make the bots feel more human and capable of handling complex tasks across multiple steps. We’re currently testing this, but the early results have been very promising.

On the infrastructure side, everything is containerized and deployed on **GKE**, with **horizontal pod autoscaling** enabled. That means when there’s a spike in partner traffic—like during holidays—the system automatically scales to handle more queries. We also have CI/CD set up through **GitHub Actions and Google Cloud Build**, which lets us push updates quickly and safely without downtime.

Overall, this project has been one of the most rewarding ones for me. Not only did we reduce the average time to resolve partner issues by about 20%, but we also built a system that’s reliable, smart, and improving every day with feedback and iteration. It was a full-stack AI problem—conversation design, prompt engineering, cloud deployment, and continuous learning—and I got to own and contribute across all those layers.

---

## 🕐 **Maruti Suzuki (1 min)**

At Maruti Suzuki, I was part of the marketing analytics team. I helped improve campaign performance using machine learning. I built models that could predict how much to spend on future campaigns, and which customer segments were more likely to respond. I also automated a lot of data cleaning and reporting tasks using Python and Snowflake, which helped the marketing team make faster and smarter decisions. One of our models helped boost ROI by over 30%.

---

## 🕐 **Capgemini (1 min)**

Capgemini was my first job, and I worked as a data engineer on a banking project. I built data pipelines using AWS and worked with large sets of transaction data. I also created dashboards using Tableau so the business teams could track customer behavior and performance. I learned a lot about writing clean SQL, presenting insights clearly, and working in an agile team environment.

---
