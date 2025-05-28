## 🧠 What is GCP’s **Agent Development Kit (ADK)?**

**GCP’s Agent Development Kit (ADK)** is an **open-source SDK provided by Google Cloud** to help developers build, deploy, and maintain **large-scale, production-grade Dialogflow CX agents** **programmatically** using reusable components and automation.

Rather than building every agent manually via the UI, the ADK allows you to:

* Programmatically define agent logic (flows, pages, routes, entities, intents)
* Reuse modular code and conversation patterns
* Write tests and version-control your bot as source code
* Build declarative bots from configuration files (YAML/JSON)

It promotes **agent-as-code** development, supports **DevOps and CI/CD pipelines**, and improves **agent reliability and scalability**.

---

## 🧩 Core Components of ADK (Explain These in Interviews)

| Component               | Description                                                                                    | How It’s Used in Your Project                                       |
| ----------------------- | ---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **Flows**               | High-level conversational contexts that group related intents and pages                        | Separate flows for: Payments, Listing Issues, Policy Questions      |
| **Pages**               | Nodes within flows; define what to prompt, collect, and respond                                | Page: `MissingPayoutPage` inside `PaymentsFlow`                     |
| **Intents**             | Capture what the user is trying to say                                                         | `missing_payout`, `edit_cancellation_policy`, `listing_not_visible` |
| **Parameters**          | Variables extracted from user input (via entities or manual entry)                             | `property_id`, `booking_id`, `date_range`                           |
| **Entities**            | Define reusable data types (like dates, property IDs, policy types)                            | Custom entity: `@policy_type`, `@region_name`                       |
| **Webhooks**            | Call external services (APIs, LLM backends) based on collected inputs                          | Call Cloud Run/GKE services to validate listings or trigger RAG     |
| **Route Groups**        | Reusable collections of routes (intent → page/action mappings)                                 | Helps maintain standard logic across pages/flows                    |
| **Playbooks (via ADK)** | Declarative YAML configs to define pre-built multi-turn conversation logic                     | `trigger_payment_investigation.yaml`, `escalate_to_agent.yaml`      |
| **Templates**           | Boilerplate conversational patterns stored as code modules                                     | Template for property verification or guest fraud workflow          |
| **Testing Framework**   | Built-in tools to simulate conversations and validate agent behavior                           | Regression testing for conversation logic when flows update         |
| **CI/CD Integration**   | Push agents to environments (Dev/Staging/Prod) automatically using GitHub Actions + gcloud CLI | Deploy new bot versions via CI/CD pipeline with version tagging     |

---

## 💡 How ADK Was Used in the Expedia Help Me Bot Project

Here’s how you can **articulate the usage of ADK** in your project during an interview:

---

### 🧾 **Problem**:

Expedia Partner Central serves thousands of partners (hotels, hosts) globally. Partners often have recurring but diverse support needs—like missing payouts, listing issues, policy clarifications.

Manual support handling was inefficient and inconsistent.

---

### ⚙️ **Solution – Using ADK in GenAI Bot Development**:

We **used ADK to scale and standardize bot development** by:

1. **Modularizing flows** using ADK:

   * Built modular flows (`PayoutSupportFlow`, `ListingSupportFlow`, etc.) defined declaratively using YAML configs.
   * Reused **route groups** and **templates** across multiple flows.

2. **Centralizing intent definitions**:

   * Created a shared `intents.yaml` using ADK structure.
   * Supported multilingual intents with ADK’s localization configs.

3. **Integrating GenAI via Webhooks**:

   * Added webhook routes in ADK YAML that call LLM-powered microservices (LangChain/Gemini backends) via GCP Cloud Run or GKE.
   * Used ADK’s webhook schema validation to catch errors early.

4. **Using Playbooks**:

   * Predefined common task sequences (e.g., “investigate missing payout”) as YAML **Playbooks**.
   * This allowed new agents to be bootstrapped quickly and consistently.

5. **Testing and Deployment**:

   * Wrote test cases using ADK’s test framework to simulate partner conversations.
   * Hooked into our **CI/CD pipeline** (GitHub Actions + Google Cloud Build) to run tests and deploy ADK agent packages to staging and prod automatically.

---

### ✅ **Result**:

* Accelerated bot development across support teams
* Enabled consistent agent behavior across languages and flows
* Automated testing and version control of agents
* Reduced manual errors and improved time-to-resolution via RAG + webhook orchestration

---

## 🗣️ Example Interview Explanation (Quick Summary)

> "In my last project, we used Google Cloud’s Agent Development Kit to build and scale our Expedia Help Me Bot. ADK let us define flows, intents, entities, and webhooks as reusable YAML configs, making the entire Dialogflow CX bot modular and version-controlled. We used Playbooks to implement prebuilt workflows like 'report a missing payout' or 'change cancellation policy'. Webhooks connected to our LLM services for document comprehension and policy explanations using RAG. We integrated this with CI/CD using GitHub Actions, enabling us to safely deploy bot updates with full test coverage. This allowed us to build high-quality, scalable bots that delivered consistent support experiences across Expedia Partner Central."

---

## ✅ When to Bring Up ADK in Interviews

* When asked **"How did you manage complex bots?"**
* When asked **"How did you maintain and scale agent development?"**
* When discussing CI/CD for conversational agents
* When asked about **DevOps or testing with Dialogflow CX**

---

Absolutely! Let's use this **"Listing Not Visible"** support workflow and break it down into a **Google Cloud Agent Development Kit (ADK)** configuration.

---

## 🧠 Goal

You want to create a Dialogflow CX agent using ADK that handles the partner support case:

> *"Why is my listing not visible?"*

We'll convert the flow diagram into:

* An **Intent** for detecting the issue
* A **Flow** called `listing_visibility_check`
* **Pages** for verification, onboarding, and property attribute decisions
* **Webhooks** for backend integrations
* **Route groups** for response actions
* **Conditional routes** for logic

---

## 📁 File Structure (ADK Example Layout)

```
expedia-agent/
├── agent.yaml
├── flows/
│   └── listing_visibility_check/
│       ├── flow.yaml
│       ├── pages/
│       │   ├── StartPage.yaml
│       │   ├── VerificationPage.yaml
│       │   ├── OnboardingPage.yaml
│       │   ├── AttributeCheckPage.yaml
│       │   └── FinalResponsePage.yaml
├── webhooks/
│   └── visibilityChecker.yaml
├── route_groups/
│   └── standardResponses.yaml
├── intents/
│   └── listing_not_visible.yaml
```

---

## 📝 1. `intents/listing_not_visible.yaml`

```yaml
displayName: listing_not_visible
trainingPhrases:
  - Why is my listing not visible?
  - My property isn’t showing up on the site.
  - I cannot find my listing.
```

---

## 📝 2. `flows/listing_visibility_check/flow.yaml`

```yaml
displayName: listing_visibility_check
startPage: StartPage
```

---

## 📝 3. `flows/listing_visibility_check/pages/StartPage.yaml`

```yaml
displayName: StartPage
transitionRoutes:
  - intent: listing_not_visible
    targetPage: VerificationPage
```

---

## 📝 4. `flows/listing_visibility_check/pages/VerificationPage.yaml`

```yaml
displayName: VerificationPage
entryFulfillment:
  webhook: visibilityChecker
  tag: check_verification
transitionRoutes:
  - condition: "$session.verificationStatus = 'PENDING'"
    targetPage: FinalResponsePage
  - condition: "$session.verificationStatus = 'APPROVED'"
    targetPage: OnboardingPage
```

---

## 📝 5. `flows/listing_visibility_check/pages/OnboardingPage.yaml`

```yaml
displayName: OnboardingPage
entryFulfillment:
  webhook: visibilityChecker
  tag: check_onboarding
transitionRoutes:
  - condition: "$session.onboardingStatus = 'ONBOARDED'"
    targetPage: AttributeCheckPage
  - condition: "$session.onboardingStatus = 'NOT_ONBOARDED'"
    targetPage: FinalResponsePage
```

---

## 📝 6. `flows/listing_visibility_check/pages/AttributeCheckPage.yaml`

```yaml
displayName: AttributeCheckPage
entryFulfillment:
  webhook: visibilityChecker
  tag: check_property_attributes
transitionRoutes:
  - condition: "$session.attributeIssue = 'blackout_dates'"
    targetPage: FinalResponsePage
```

---

## 📝 7. `flows/listing_visibility_check/pages/FinalResponsePage.yaml`

```yaml
displayName: FinalResponsePage
entryFulfillment:
  messages:
    - text:
        text: ["Thanks. We've processed your listing status. Do you want to update your property configuration?"]
  transitionRoutes:
    - condition: "$session.userWantsToUpdate = true"
      targetFlow: system
      targetPage: property_configuration_page
    - condition: "$session.userWantsToUpdate = false"
      targetPage: END_SESSION
```

---

## 📝 8. `webhooks/visibilityChecker.yaml`

```yaml
displayName: visibilityChecker
genericWebService:
  uri: https://backend.expedia.com/check-listing-status
  requestHeaders:
    Authorization: "Bearer $PROJECT_API_TOKEN"
  timeout: 10s
```

This webhook handles:

* `check_verification`: call verification service
* `check_onboarding`: call onboarding service
* `check_property_attributes`: call attribute check service

Each webhook should return fields like:

```json
{
  "verificationStatus": "APPROVED",
  "onboardingStatus": "NOT_ONBOARDED",
  "attributeIssue": "blackout_dates",
  "userWantsToUpdate": true
}
```

---

## ✅ Summary of ADK Usage in This Flow

| ADK Feature        | How It's Used                                                            |
| ------------------ | ------------------------------------------------------------------------ |
| **Flows & Pages**  | Structured flow for listing issue diagnosis                              |
| **Webhooks**       | Fetch status from Expedia internal services (Property, Onboarding, etc.) |
| **Intents**        | Catch user phrase like “listing not visible”                             |
| **Session Params** | Store and use backend results to control next step                       |
| **Conditions**     | Route user to correct next page depending on status values               |
| **CI/CD Friendly** | This YAML setup can be versioned and deployed via GitHub Actions         |

---

Great follow-up questions. Let's dive into both parts:

---

## ✅ **1. Explanation of Each ADK Component & Field**

The Google Cloud Dialogflow **Agent Development Kit (ADK)** is a developer-centric way to define a Dialogflow CX agent using code — specifically YAML files. Each component maps to the building blocks of a Dialogflow CX agent.

---

### 🔹 `agent.yaml`

This is the root configuration of your agent.

```yaml
displayName: ExpediaPartnerSupport
defaultLanguageCode: en
timeZone: America/Los_Angeles
description: Agent for Expedia Partner Central Support bot
```

| Field                 | Purpose                              |
| --------------------- | ------------------------------------ |
| `displayName`         | The name shown in Dialogflow console |
| `defaultLanguageCode` | Language of the bot (e.g., `en`)     |
| `timeZone`            | Used to schedule responses, sessions |
| `description`         | Developer-friendly description       |

---

### 🔹 `intents/*.yaml`

Each YAML defines a user **intent** (user’s goal).

```yaml
displayName: listing_not_visible
trainingPhrases:
  - Why is my listing not visible?
  - My property isn’t showing up
```

| Field             | Purpose                                                      |
| ----------------- | ------------------------------------------------------------ |
| `displayName`     | Unique name of the intent                                    |
| `trainingPhrases` | User inputs used to train the model to recognize this intent |

---

### 🔹 `flows/` and `pages/`

Each **flow** handles a use-case or scenario. Inside a flow, you have **pages**, each like a state in a state machine.

#### `flow.yaml`

```yaml
displayName: listing_visibility_check
startPage: StartPage
```

| Field         | Purpose                                          |
| ------------- | ------------------------------------------------ |
| `displayName` | Name of the flow                                 |
| `startPage`   | First page Dialogflow uses when this flow starts |

---

#### `pages/*.yaml`

Each page represents a step in the conversation.

```yaml
displayName: VerificationPage
entryFulfillment:
  webhook: visibilityChecker
  tag: check_verification
```

| Field              | Purpose                                                            |
| ------------------ | ------------------------------------------------------------------ |
| `entryFulfillment` | Executes actions when user reaches this page (e.g., webhook calls) |
| `webhook`          | The webhook service to call                                        |
| `tag`              | Identifies the operation inside the webhook                        |
| `transitionRoutes` | Defines what to do next based on conditions or user inputs         |

---

### 🔹 `webhooks/*.yaml`

Defines external services that the agent can call.

```yaml
displayName: visibilityChecker
genericWebService:
  uri: https://backend.expedia.com/check-listing-status
  requestHeaders:
    Authorization: "Bearer $PROJECT_API_TOKEN"
  timeout: 10s
```

| Field            | Purpose                                    |
| ---------------- | ------------------------------------------ |
| `displayName`    | Name used in page/webhook reference        |
| `uri`            | Endpoint to hit                            |
| `requestHeaders` | Auth headers (API key, token, etc.)        |
| `timeout`        | How long Dialogflow waits before giving up |

---

### 🔹 `route_groups/*.yaml` (Optional)

Reusable transition routes that can be included in many pages.

```yaml
routes:
  - condition: "$session.userWantsToUpdate = true"
    targetPage: UpdatePropertyPage
```

| Field        | Purpose                                               |
| ------------ | ----------------------------------------------------- |
| `condition`  | When this route is activated                          |
| `targetPage` | Where to route the user next if the condition matches |

---

## ✅ 2. Deployment Options: Where and How to Deploy

Dialogflow CX agents defined using ADK can be deployed using:

### 🛠 **A. CLI Deployment via `dfcx` Tool (Recommended)**

**Steps:**

1. **Install CLI Tool:**

   ```bash
   pip install dfcx
   ```

2. **Deploy Agent from ADK:**

   ```bash
   dfcx deploy-agent --agent-path=expedia-agent/ --project=my-gcp-project --location=us-central1
   ```

> This uploads all flows, intents, pages, webhooks, and parameters to your Dialogflow CX console.

---

## 🧭 3. Runtime Hosting Options

The Dialogflow CX **agent itself is hosted on Google infrastructure** (you don’t need to host it manually). But if you’re using **custom webhooks**, you must host them somewhere.

### Webhook Hosting Options:

| Platform                           | Used for                                                                |
| ---------------------------------- | ----------------------------------------------------------------------- |
| **Cloud Run** (✅ Recommended)      | Stateless HTTPS endpoints with autoscaling — easy and cheap to maintain |
| **GKE (Google Kubernetes Engine)** | More complex orchestration — use only if you're already on Kubernetes   |
| **Cloud Functions**                | Simpler functions with less control, great for prototyping              |

### Example Cloud Run Webhook Setup:

1. Build and deploy your webhook app:

   ```bash
   gcloud run deploy visibilityChecker \
     --source . \
     --region us-central1 \
     --allow-unauthenticated
   ```

2. Use the deployed URL in your webhook YAML:

   ```yaml
   uri: https://visibilitychecker-abc123.a.run.app/check
   ```

---

## ✅ Recap: What You Deploy Where

| Component                  | Deployment Target                                        |
| -------------------------- | -------------------------------------------------------- |
| `agent.yaml`, flows, pages | Uploaded to **Dialogflow CX** using ADK                  |
| Webhooks                   | Hosted on **Cloud Run**, **GKE**, or **Cloud Functions** |
| ADK YAML Files             | Stored in GitHub/Cloud Source for CI/CD                  |
| Deployment Automation      | Done using `dfcx` CLI, or GitHub Actions workflows       |

---


