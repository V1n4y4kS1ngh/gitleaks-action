# AgentEase

### *Start with Assist. Scale to Autonomy.*

---

## 📄 Project Overview

**AgentEase** is a GenAI-powered virtual assistant tailored for contact center use cases. It leverages Amazon Lex for conversation handling, SageMaker for intent classification, and Bedrock Knowledge Base (KB) for intelligent responses based on uploaded documents. The system is designed to reduce agent load, accelerate support interactions, and elevate user experience.

This solution is modular, cloud-native, and adaptable to any enterprise or B2B support environment.

---

## 🌐 Use Case & Personas

**Primary Users:**

* End customers of customer support–centric enterprises such as BPOs, managed service providers, and SaaS support teams
* Visitors interacting via chat/voice interfaces

**Key Use Cases:**

* Understand and categorize user queries using an intent classifier
* Provide AI-generated answers from company KB or LLM fallback
* Route specific intents to downstream APIs or human agents
* Enable voicemail/callback scenarios to avoid wait queues *(planned)*

---

## 📊 Goals & KPIs

* 🔽 Reduce first-level agent workload
* ⏱ Improve response latency across support touchpoints
* 😊 Elevate customer satisfaction and self-service confidence

---

## 🛠️ Architecture Overview

### Core AWS Components:

| Component             | Role                                                                                            |
| --------------------- | ----------------------------------------------------------------------------------------------- |
| **Amazon Lex**        | Handles voice + text conversations and routes to the right Lambda                               |
| **Amazon Bedrock**    | Uses KB to provide natural answers based on provided documents                                  |
| **Amazon SageMaker**  | Hosts a trained intent classification model (multi-label classifier)                            |
| **Lambda (3)**        | 1. User fetch/store → DynamoDB. 2. Intent classifier. 3. LLM query handler *(not wired in yet)* |
| **DynamoDB**          | Stores user details (e.g. phone number → username)                                              |
| **Amazon S3**         | Stores model artifacts, training datasets, and Bedrock KB PDFs                                  |
| **Amazon Connect**    | Used for voice-based IVR integration                                                            |
| **Amazon CloudWatch** | Logs every flow step for observability, debugging, and traceability                             |
|                       |                                                                                                 |

---

## 🔍 Knowledge Base

Due to crawling restrictions on Algoworks.com, the KB currently contains:

* AI Hackathon documents uploaded  to S3
* These documents are temporarily acting as the information source for Bedrock KB ingestion.

*Figure: Indexed KB documents from S3 bucket*

---

## 📈 Top Use Cases

| **Use Case**                 | **Notes**                                               |
| ---------------------------- | ------------------------------------------------------- |
| 🔍 General Company Info      | Answered via Bedrock KB based on uploaded docs          |
| 🌐 Service/Contact Discovery | Intent classification guides user to contact info, etc. |
| 🗣️ Voicemail Drop (planned) | Will allow user to leave message + callback option      |

---

## 🪨 Known Limitations / Gaps

| **Limitation**               | **Description**                                                                                 |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| 🕵️ Web crawler blocked      | Could not index Algoworks site due to bot restrictions                                          |
| 📄 Temporary KB source       | KB docs used are specific to this AI Hackathon event and unrelated to company's actual services |
| 🪴 LLM Lambda not integrated | Lambda for querying LLM (non-KB) is in place but not currently used in flow                     |

---

## 🚀 Future Enhancements

* **Voicemail Implementation** – Allow users to drop a message and receive a follow-up
* **CRM Integration (Salesforce)** – Sync user details, leads, and support tickets
* **Hallucination Detection** – Detect and mitigate incorrect or low-confidence AI responses
* **Infrastructure as Code (IaC)** – Use Terraform/CDK to deploy the solution quickly across environments
* **Glossary-Aware Transcription** – Add support for custom vocabulary and domain-specific terms using Amazon Transcribe
* **Conversation Summaries for Handoff** – Generate context summaries for agents when escalation is needed
* **Analytics & Insights Layer** – Track usage metrics, query types, drop-offs, and unanswered questions

---

## 🌐 Real-World Potential

While the current KB is based on hackathon documents, this solution is easily repurposed to:

* Ingest and automate support from any public site
* Support use cases like field sales enablement, onboarding workflows, and AI-powered self-service portals
* Plug into WhatsApp, Slack, and other channels

---

## 📷 Screenshots & Attachments

**Lex chatbot responding to KB queries using test draft version:**

![Chatbot screenshot 1](sandbox:/mnt/data/f3b4a968-e23f-4d65-9e86-84b5ff785433.png)

**Chatbot responding with prize money details:**

![Chatbot screenshot 2](sandbox:/mnt/data/0ece89d5-1962-4bb8-9d1b-efb20c1c28bf.png)

---

## 🧪 How to Test It

You can try the experience live:

* Call our demo line: **+1-833-397-4200**
* Ask questions about the AI Hackathon documents (these are indexed in the Knowledge Base)
* Try open-ended queries like:

  * “What is this hackathon about?”
  * “Tell me the judging criteria”
  * “What's the prize?”
* Test the intent classification by saying:

  * “I want to talk to someone” → should trigger `connect_to_agent`
  * “Do you offer mobile app development?” → should match `mobile_app_development`

Let’s just say... our classifier might still confuse a compliment for a complaint — but hey, it’s learning! 😁

---

## 📝 Summary

**AgentEase** delivers a robust GenAI foundation for customer support teams. It blends automation, voice/chat, knowledge retrieval, and extensibility into one unified stack. With future additions like voicemail, CRM hooks, and conversation intelligence, it lays the groundwork for autonomous support systems across verticals.

---

## 👤 Author & Contact

**Suraj Singh Bani**
📧 [suraj.singh@algoworks.com](mailto:suraj.singh@algoworks.com)
Associate DevOps Lead
[www.algoworks.com](https://www.algoworks.com)

---

*"Assist now, automate later."*
