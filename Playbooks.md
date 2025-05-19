
⸻

## 🤖 Create a Conversational Agent with Playbooks in Dialogflow CX 

### 🎯 Example Use Case: “Check Claim Status” Assistant

The user should be able to say:

“Can you check the status of my insurance claim 12345?”

The agent should:
	•	Understand the intent
	•	Extract the claim number
	•	Query a BigQuery table or API
	•	Return the claim status to the user

⸻

### 🛠️ Tools You’ll Use

Tool Type	Purpose
OpenAPI Tool	Query backend REST API (claim status)
Data Store	Provide knowledge answers (e.g., FAQs)
Connector	Query BigQuery claim data


⸻

### 🧱 Step 1: Create an Agent in Dialogflow CX
	1.	Go to: https://dialogflow.cloud.google.com/cx
	2.	Click “Create Agent”
	3.	Fill:
   •	Agent Name: ClaimStatusAgent
   •	Location: Select a region (e.g., us-central1)
   •	GCP Project: Your current project
	4.	Click Create

⸻

### 📘 Step 2: Create a Playbook
	1.	In the left sidebar, click Playbooks
	2.	Click + Create Playbook
	3.	Fill in:
   •	Playbook Name: check_claim_status
   •	Goal: Help users check the status of their insurance claims
   •	Instructions:
    
    1. Ask the user for the claim number.
    2. Use the connector or OpenAPI to look up claim status.
    3. Summarize the result and respond to the user.


  •	Click Next

	4.	(You’ll add tools after creating them in the next steps)

⸻

### 🔧 Step 3: Create and Link Tools

### 🛠 A. OpenAPI Tool (To hit a REST API)

For example, an endpoint: GET /claims/{claim_id}

	1.	Go to Tools → Click + Create Tool
	2.	Fill:
     •	Tool Name: get_claim_status_tool
     •	Tool Type: OpenAPI
     •	Description: Fetch claim status from backend API
	3.	Paste this OpenAPI schema:

      openapi: 3.0.0
      info:
        title: Claim API
        version: 1.0.0
      paths:
        /claims/{claim_id}:
          get:
            summary: Get claim status
            parameters:
              - name: claim_id
                in: path
                required: true
                schema:
                  type: string
            responses:
              '200':
                description: Successful response
                content:
                  application/json:
                    schema:
                      type: object
                      properties:
                        status:
                          type: string

	4.	Auth Settings:
     •	If the API doesn’t require auth: Leave blank
     •	Otherwise, select API key or Service Account Token
	5.	Click Create Tool

⸻

### 🛠 B. Data Store Tool (For FAQs or contextual grounding)
	
  1.	Go to Tools → + Create Tool
	2.	Fill:
     •	Tool Name: claim_faq_tool
     •	Type: Data Store
     •	Description: Answers common questions about insurance claims
     •	Enable Grounding: ✅
     •	Enable Summarization: ✅
	3.	Click Create Tool
	4.	Go to the created tool → Click Manage Documents
	5.	Upload PDF/CSV (e.g., “Claims FAQ.pdf”)

⸻

### 🛠 C. Connector Tool (BigQuery claim dataset)

  Dataset: insurance_data.claims

	1.	Go to Tools → + Create Tool
	2.	Fill:
     •	Tool Name: claim_status_connector_tool
     •	Type: Connector
     •	Connector Type: BigQuery
	3.	Set Connection:
     •	Project ID: your-project-id
     •	Dataset: insurance_data
     •	Table: claims
   •	You can allow read-only access using a Service Agent
	4.	Click Create Tool

⸻

### 🔗 Step 4: Link Tools to the Playbook
	1.	Go back to Playbooks
	2.	Click check_claim_status
	3.	Click Edit
	4.	Scroll to Available Tools
	5.	Add
     •	get_claim_status_tool
     •	claim_faq_tool
     •	claim_status_connector_tool
	6.	Click Save

⸻

### 🧪 Step 5: Test the Agent
	1.	Click Train Agent
	2.	Click “Try It Now”
	3.	Enter test phrase:

    I want to check the status of my claim 78910


	4.	The agent will:
     •	Detect the goal → check_claim_status
     •	Ask for missing info (claim_id)
     •	Call the correct tool (API or BigQuery)
     •	Respond with the claim status

⸻

### 📌 Sample YAML Representation of the Playbook

    goal: Check Claim Status
    instructions:
      - Ask for claim ID
      - Call tool to check status
      - Return response to user
    
    availableTools:
      - name: get_claim_status_tool
        type: openapi
      - name: claim_faq_tool
        type: data_store
      - name: claim_status_connector_tool
        type: connector
    

⸻

### 🧹 Cleanup Tips
	
   •	Delete unused tools in the Tools tab
   •	Re-train agent if tools or instructions change
   •	Monitor interactions in Test > View Trace

⸻

### ✅ Summary Table

    Component	Name	Purpose
    Agent	ClaimStatusAgent	Main agent
    Playbook	check_claim_status	Handles claim status goal
    OpenAPI Tool	get_claim_status_tool	Calls REST API
    Data Store Tool	claim_faq_tool	Handles user questions
    Connector Tool	claim_status_connector_tool	Queries BigQuery claim data


⸻
