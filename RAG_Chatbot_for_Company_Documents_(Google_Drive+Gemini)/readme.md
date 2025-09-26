# RAG Chatbot for Company Documents (Google Drive + Gemini)

This workflow implements a Retrieval Augmented Generation (RAG) chatbot that answers questions based on documents stored in Google Drive. It keeps the document index up to date and uses Google Gemini (PaLM) for embeddings and response generation.  

---

## 🧠 How It Works

1. Two **Google Drive Trigger** nodes monitor a specified folder:  
   - One for **new files**  
   - One for **updates to existing files**

2. When a document is created or updated:  
   - It’s downloaded via a **Google Drive** node  
   - Processed by a **Default Data Loader** to extract content  
   - Split into smaller chunks using **Recursive Character Text Splitter**  
   - Sent to **Google Gemini embeddings** (model: `text-embedding-004`)  
   - Indexed in Pinecone via a **Pinecone Vector Store** node

3. When a user asks a question via the **Chat Trigger**:  
   - The **AI Agent** node retrieves relevant text chunks via a **Vector Store Tool** (query mode)  
   - Those retrieved chunks + the user query are passed to **Google Gemini Chat Model** (`gemini-pro`)  
   - Output is a coherent answer informed by your documents  
   - A **Window Buffer Memory** node gives short-term conversation context

---

## 🔧 Setup Instructions

### 1. Google Cloud & Vertex AI

- Create a Google Cloud project  
- Enable **Vertex AI API**  
- Get a **Google AI API key** from Google AI Studio

### 2. Pinecone

- Create a free Pinecone account  
- Get your **API key**  
- Create a vector index (e.g. `company-files`)

### 3. Google Drive

- Make a dedicated folder in your Drive for your company documents  
- Use this folder path in your trigger nodes

### 4. Configure n8n Credentials

You’ll need to set up:

- **Google Drive OAuth2** credentials  
- **Google Gemini / PaLM API** — using your Google AI key  
- **Pinecone API** — using your Pinecone key

### 5. Import & Configure the Workflow

- Import `workflow.json` into n8n  
- Point both **Google Drive Trigger** nodes to the folder you created  
- Configure **Pinecone Vector Store** nodes to use your `company-files` index  
- Ensure Gemini and Drive nodes use correct credentials

---

## ⚙️ Key Nodes & Their Roles

| Node | Role |
|---|---|
| Google Drive Trigger | Detect new or updated docs |
| Google Drive | Download the document |
| Default Data Loader | Extract readable content |
| Recursive Character Text Splitter | Break content into chunks |
| Google Gemini (embeddings) | Generate embeddings for chunks |
| Pinecone Vector Store (index) | Store chunk embeddings in index |
| Chat Trigger | Accept user queries |
| AI Agent | Manage retrieval + response generation |
| Vector Store Tool | Query embedding index |
| Google Gemini Chat Model | Generate responses |
| Window Buffer Memory | Maintain conversational context |

---

## 💡 Customization Ideas

- Use a different embedding or LLM provider  
- Add an approval or filtering step before indexing new docs  
- Use another vector database instead of Pinecone  
- Add logging, metrics, or error handling  
- Improve conversational memory (longer history, context retention)

---

## ✅ Requirements

- A Google Cloud / Vertex AI setup with Gemini access  
- Pinecone account and index  
- Google Drive folder for document storage  
- A working n8n instance (cloud or self-hosted)  
- Proper credentials configured in n8n

---

## 📜 License

This workflow is open‑use (personal & commercial). Attribution is optional.  
