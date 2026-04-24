# Mitr.ai 🤖
**A minimalist, no-code RAG chatbot builder for LINE Official Accounts.**

Mitr.ai (มิตร) empowers businesses to seamlessly convert their menus, FAQs, and business documents into an intelligent, context-aware AI assistant on the LINE platform. Built with a focus on clean architecture and a minimalist user experience.

## 🛠 Tech Stack
* **Frontend:** React, TypeScript, Vite
* **Backend:** Node.js, Express
* **AI & Data:** LLM API (OpenAI/Gemini), MongoDB Atlas (Vector Search)
* **Integration:** LINE Messaging API

---

## 📋 1. Functional Requirements (FR)
* **FR1 (Knowledge Ingestion):** The system must allow administrators to upload business documents (Text/PDF) and automatically process them into vector embeddings stored in the database.
* **FR2 (Bot Configuration):** The system must provide a settings interface to configure the chatbot's persona (System Prompt), display name, and avatar image.
* **FR3 (Sandbox Testing):** The system must include a web-based chat interface (Sandbox) allowing administrators to test and refine the bot's responses before public deployment.
* **FR4 (LINE Integration):** The system must securely receive webhooks from the LINE Messaging API, process user inquiries using a RAG pipeline, and return accurate, context-aware replies.

## ⚡ 2. Non-Functional Requirements (NFR)
* **NFR1 (Performance - Latency):** The end-to-end processing time—from receiving the LINE webhook to dispatching the LLM-generated reply—must not exceed 5 seconds to ensure a natural conversational flow.
* **NFR2 (Security):** Sensitive credentials, including LINE Channel Access Tokens and Channel Secrets, must be strictly encrypted at rest within the database.
* **NFR3 (Usability):** The admin dashboard must employ a minimalist, distraction-free design system and be fully responsive, ensuring seamless operability on iPads and mobile devices used in retail environments.

---

## 👤 3. User Stories & Acceptance Criteria

### User Story 1: Knowledge Management
> **As a** business owner (Admin),  
> **I want to** upload my restaurant's menu and FAQ documents into the system,  
> **So that** the chatbot possesses the correct knowledge to answer customer inquiries about my specific products.

* **Acceptance Criteria 1:** Given the admin uploads a supported `.pdf` file (under 5MB), when the upload is complete, the system displays a "Processing" status and updates to "Success" once the vector embeddings are generated.
* **Acceptance Criteria 2:** Given the admin attempts to upload an unsupported file format (e.g., `.zip` or `.exe`), when the file is selected, the system immediately rejects the upload and displays a clear error message.

### User Story 2: Platform Integration (LINE)
> **As a** business owner (Admin),  
> **I want to** input my LINE Official Account API credentials,  
> **So that** my custom chatbot can connect to my business's LINE account and automatically reply to customers.

* **Acceptance Criteria 1:** Given the admin inputs a Channel Access Token and clicks "Connect", when the system successfully pings the LINE API, the connection status updates to "Connected" with a green indicator.
* **Acceptance Criteria 2:** Given a customer sends a message to the connected LINE account, when the webhook is triggered, the backend strictly retrieves context belonging ONLY to that specific business to formulate the reply, ensuring no data cross-contamination between different shops.
