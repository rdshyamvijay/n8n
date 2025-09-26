# AI‑Powered WhatsApp Chatbot (Text, Voice, Images & PDF with RAG)

This workflow builds a WhatsApp chatbot that can answer user queries across multiple content types (text, voice, images, PDF) using retrieval-augmented generation (RAG). It ingests your product documentation, indexes it, and uses AI to respond via WhatsApp.

---

## 🧩 What It Does

### Workflow 1: Document Ingestion & Indexing  
- Triggered manually to import product documentation from **Google Docs**  
- Splits long documents into manageable chunks  
- Creates vector embeddings for each chunk using OpenAI embeddings  
- Stores chunks + metadata in a **MongoDB Atlas** vector store for semantic search  

### Workflow 2: Chat via WhatsApp  
- Listens for incoming WhatsApp messages (supports text, voice, images, PDF, etc.)  
- Converts non-text content to a textual representation as needed (e.g. OCR, transcription)  
- Embeds the user query, finds relevant chunks via vector similarity search  
- Uses OpenAI’s GPT‑4o‑mini model + retrieval context to generate answers  
- Maintains conversational memory context across multiple turns  
- Routes different input types to appropriate handlers for better responses  

---

## 🔧 Setup Instructions

### 1. Document Ingestion & Indexing

- Authenticate **Google Docs** and point to the docs/folder containing your product manuals  
- Authenticate **MongoDB Atlas**, and set the collection for storing embeddings and metadata  
- Create a vector index on that MongoDB collection (embedding, metadata, etc.)  
- Ensure the index name matches the one configured in the n8n nodes  

### 2. WhatsApp Chat Setup

- Authenticate the **WhatsApp (Meta)** node for receiving and sending messages  
- Link the same MongoDB collection (with embeddings) into the vector search node  
- Configure the **Knowledge Base Agent** or system prompt to reference your vector store and define your brand’s tone  

### 3. General Notes

- Both ingestion and chat parts must point to the same MongoDB collection  
- The collection must have:
  - A field storing embeddings (vector)
  - Metadata (e.g. document ID, source)
  - A vector index name consistent across nodes  
- Make sure permission scopes and credentials are correctly set in n8n for all external services  

---

## 🔍 Key Nodes & Their Roles

| Node | Role |
|------|------|
| Google Docs / Document Fetch | Retrieve the reference documentation |
| Text Splitter | Break content into smaller chunks |
| Embedding (OpenAI) | Create vector embeddings for chunks |
| MongoDB Vector Store | Store embeddings + metadata |
| WhatsApp Trigger | Listen to incoming WhatsApp messages |
| Media Processors | Handle audio → text, images → OCR, PDF parsing |
| Vector Search | Find relevant chunks given user input |
| GPT‑4o Model | Generate AI response using query + context |
| Memory Node | Keep conversation context across turns |

---

## 💡 Tips & Ideas for Customization

- Tailor the system prompt to match your company’s voice and knowledge limitations  
- Add rate limiting, validation, or fallback logic  
- Use additional AI models for OCR (if images contain text) or PDF parsing  
- Extend to other channels (e.g. Telegram, Slack) using the same architecture  
- Add logging, metrics, or error handling to monitor usage and failures  

---

## ✅ Requirements & Notes

- Google Docs access for documentation ingestion  
- MongoDB Atlas for vector storage  
- OpenAI API access for embeddings and responses  
- Proper WhatsApp (Meta) integration and credentials  
- n8n instance (cloud or self‑hosted)  
- Check that all nodes are pointed to correct credentials and indices  
- Test with small sample docs and messages first  

---

Feel free to tell me if you want diagrams, example prompts, or badge headers added.
