# 🤖 Nkululeko-VillI-Nhlapo — AI-Powered CV Assistant with RAG Architecture  

An **automated CV chatbot** built with **n8n workflow automation**, integrating **document processing, vector embeddings, and conversational AI** to create an intelligent assistant that can answer detailed questions about my professional background and experience.  

---

## 🌍 Overview  

This project demonstrates a complete **Retrieval-Augmented Generation (RAG)** implementation that transforms a traditional CV into an **interactive conversational interface**.  

- 📂 **Upload CV → Automated Processing → Vector Embeddings → Conversational AI**  
- 💬 **Chat with your CV**: Get accurate, context-aware answers about education, experience, and skills.  
- ⚡ Built entirely with **n8n visual workflows** (no custom backend).  

---

## 🏗️ Architecture  
Google Drive Upload → Document Processing → Text Extraction → Vector Embeddings
↓
Chat Interface ← AI Agent (Claude) ← Vector Retrieval ← Pinecone Storage


### 🔹 Workflows  
- **Data Processing Pipeline** → Converts CV into a searchable knowledge base.  
- **Chat Interface** → Real-time Q&A powered by embeddings + AI agent.  

---

## ⚙️ Technical Stack  

- ⚡ **Workflow Engine:** n8n (Dockerized)  
- 📂 **Document Storage:** Google Drive API + triggers  
- 📑 **Text Processing:** Native PDF/Word extraction in n8n  
- 🧠 **Embeddings:** OpenAI `text-embedding-ada-002` (1536 dimensions)  
- 🗄️ **Vector Database:** Pinecone Serverless (cosine similarity)  
- 🤝 **Conversational AI:** Anthropic Claude 3.5 Haiku  
- 📝 **Memory:** Session-based conversation context  
- 🐳 **Deployment:** Docker with persistent volumes  

---

## ✨ Key Features  

### 📑 Automated Document Pipeline  
- 🔔 **Real-time Upload Detection** with Google Drive triggers  
- 📝 **Multi-format Support**: PDF + Word  
- ✂️ **Intelligent Chunking** for efficient retrieval  
- 🧠 **Semantic Vectorization** with OpenAI embeddings  
- ☁️ **Scalable Pinecone Storage** (41 processed chunks)  

### 💬 RAG-Powered Chat Interface  
- ❓ Ask: *“What programming languages does this person know?”*  
- ✅ **Context-aware answers** directly from CV  
- 🧩 **Memory** for conversation flow  
- 🌍 **Webhook endpoint** for API integration  
- ⚡ **Fast responses** (~2–3s)  

### 🔗 Multi-API Orchestration  
- Google Drive, OpenAI, Anthropic, Pinecone  
- 🔐 Secure OAuth2 + API key handling  
- 🔁 Retry logic + error handling  
- ☑️ Cloud-ready setup  

---

## 🔨 Workflow Components  

### 📂 Data Processing Pipeline  
1. Google Drive Trigger → fileCreated  
2. Download File  
3. Extract from File (PDF/Word → text)  
4. Chunk & structure data  
5. Generate Embeddings (OpenAI)  
6. Store in Pinecone  

### 💬 Chat Interface  
1. Webhook Trigger → receives user query  
2. AI Agent (Claude) orchestrates reasoning  
3. Pinecone Retrieval → semantic context fetch  
4. Claude generates response  
5. n8n returns answer to user  

---

## 🛠️ Implementation Details  

### 🔹 Vector DB Config  
- Index: `cv-portfolio`  
- Dimensions: `1536`  
- Metric: `cosine`  
- Region: `aws-us-east-1`  
- ✅ 41 document chunks  

### 🔹 System Prompt Engineering  
- Guides the AI agent for:  
  - Professional context understanding  
  - Accurate, **source-grounded responses**  
  - Smooth conversation flow  

---

## 🔑 API Integrations  

- **📂 Google Drive:** OAuth2 + real-time triggers  
- **🧠 OpenAI:** Embeddings for semantic search  
- **🗄️ Pinecone:** Vector similarity search  
- **🤝 Anthropic Claude:** Conversational reasoning  

---

## 🚀 Setup Instructions  

### 🔧 Prerequisites  
- n8n (Docker or Cloud)  
- Google Cloud project (Drive API enabled)  
- Pinecone account (free tier works)  
- OpenAI API key  
- Anthropic API key (min $5 credits)  

### ⚡ Environment Setup  
```bash
docker run -it --rm --name n8n \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  n8nio/n8n


