# 🌿 Cosmetic Ingredient Analyzer (AI RAG Agent)

An intelligent AI-powered agent designed to analyze cosmetic product compositions. By leveraging **Retrieval-Augmented Generation (RAG)**, this agent doesn't just guess, it retrieves factual data about chemical compounds, safety ratings, and benefits from a specialized vector database hosted on **Pinecone**.

The entire logic is orchestrated using **n8n**, providing a seamless flow between the user input, the vector store, and the Large Language Model.

## 🚀 Features

- **Deep Ingredient Analysis:** Identifies allergens, comedogenic components, and active ingredients.
- **RAG Architecture:** Uses a custom-built database of cosmetic ingredients to ensure high accuracy and reduce hallucinations.
- **Automated Data Pipeline:** Easy ingestion of ingredient datasets into the vector database.

## 🛠 Tech Stack

- **n8n:** Workflow automation and agent orchestration.
- **Pinecone:** Vector database for high-performance ingredient retrieval.
- **Gemini:** LLM for natural language processing and reasoning.
- **LangChain (via n8n):** Framework for managing RAG logic.

---

## 🏗 Workflow Architecture

The project consists of two main n8n workflows:

### 1. Data Ingestion Workflow
This workflow processes raw cosmetic ingredient data (CSV/JSON), generates embeddings, and upserts them into a **Pinecone** index. This serves as the "knowledge base" for the agent.

<img width="996" height="373" alt="image" src="https://github.com/user-attachments/assets/43f9ce00-2291-42e4-aa05-8cb60231291f" />

*Workflow steps: Read Data from Google Sheet -> Parse text -> Gemini Embeddings and Data Loader -> Pinecone Vector Store.*

### 2. AI Agent & RAG Workflow
This is the consumer-facing workflow. It receives a product label (text or image), queries the Pinecone index for relevant ingredient information, and generates a detailed report.

<img width="673" height="642" alt="image" src="https://github.com/user-attachments/assets/9fcc70bf-1755-4f62-8b55-735129df14a6" />

*Workflow steps: Chat Trigger -> Check if user attached image -> AI Agent Node -> Pinecone Vector Store Tool -> Output*

## ⚡ Try It Yourself

You can interact with the live version of the **Cosmetic AI Agent** directly through your browser. Click the link below to start analyzing ingredients in real-time:

👉 **[Launch Live Chat Demo](https://130.61.87.184.sslip.io/webhook/6778a52f-50c8-40a6-b8c1-cc168bd1ddca/chat)** -> User: user, Password: user

### How to use the chat: 
Paste the Ingredients or attach image
