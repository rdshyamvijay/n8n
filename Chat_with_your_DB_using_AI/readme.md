# Chat with any Database Using AI

This workflow lets you ask natural language questions about data stored in a database. Under the hood, it translates user queries into SQL, fetches results, and returns human-friendly answers via an AI model.  [oai_citation:0‡n8n](https://n8n.io/workflows/2090-chat-with-a-database-using-ai/?utm_source=chatgpt.com)

---

## ⚙️ What It Does

- Accepts user input (chat-style prompt)
- Uses an AI model (e.g. from OpenAI) to translate the prompt into an SQL query
- Executes that query against your database (PostgreSQL, MySQL, or SQLite)  [oai_citation:1‡n8n](https://n8n.io/workflows/2090-chat-with-a-database-using-ai/?utm_source=chatgpt.com)
- Feeds the results back into the AI model to generate a readable answer
- Returns the answer in the chat interface  
- Optionally, you could adapt this to chat over Slack, MS Teams, WhatsApp, etc.  [oai_citation:2‡n8n](https://n8n.io/workflows/2090-chat-with-a-database-using-ai/?utm_source=chatgpt.com)

---

## 🔧 Setup Instructions

### 1. Database Access & Credentials

- Prepare a database you want to query (PostgreSQL, MySQL, or SQLite)  [oai_citation:3‡n8n](https://n8n.io/workflows/2090-chat-with-a-database-using-ai/?utm_source=chatgpt.com)
- Make sure n8n has credentials to connect (host, username, password, database name, port)
- Grant read access (or read/write if you allow updates) to the tables you'll query

### 2. OpenAI (or Equivalent) API

- Acquire an API key for OpenAI (or another AI service that can handle text and prompt‐to‐SQL translation)
- Configure that key in n8n credentials so AI nodes can call it

### 3. Import & Configure the Workflow

- Import the `workflow.json` into your n8n instance
- Set your database node (SQL node) to use your DB credentials
- Make sure the AI node is configured to use your OpenAI credential
- Optionally adjust prompts or templates used to generate SQL (to fit your schema or style)

### 4. Chat Interface

- The template uses n8n’s embedded chat trigger, but you can swap it out with Slack, Teams, or another channel  [oai_citation:4‡n8n](https://n8n.io/workflows/2090-chat-with-a-database-using-ai/?utm_source=chatgpt.com)
- Connect the chat input to start the flow

---

## 🧩 Key Nodes & Their Roles

| Node | Purpose |
|---|---|
| Chat Trigger | Accepts user questions |
| AI / OpenAI Node | Translates prompt → SQL, and afterward maps data → human response |
| Database Node (SQL) | Executes the SQL query on your connected DB |
| Response Formatter | Combines AI and query results into the final answer |

---

## 💡 Tips & Customization Ideas

- Tailor the prompt templates to your database schema so the AI generates correct SQL more reliably
- Add validation or safety layers to avoid destructive queries (e.g. `DROP`, `DELETE`) if not needed
- Use limit or pagination logic if tables are huge
- Swap in another AI provider if you don’t want to use OpenAI
- Extend to support write operations (insert, update) with care and validation
- Integrate with messaging platforms so users can chat from Slack, Teams, etc.

---

## ✅ Requirements & Notes

- Workflow requires **n8n version 1.19.4 or later**  [oai_citation:5‡n8n](https://n8n.io/workflows/2090-chat-with-a-database-using-ai/?utm_source=chatgpt.com)  
- Supported database types: PostgreSQL, MySQL, SQLite  [oai_citation:6‡n8n](https://n8n.io/workflows/2090-chat-with-a-database-using-ai/?utm_source=chatgpt.com)  
- Ensure all nodes have correct credentials  
- Test with a safe, sample table first to confirm it’s working  
- Be cautious exposing write access to the AI — limit to read unless you’ve vetted the logic

---

If you like, I can also create a flowchart image (diagram) and embed it into this README. Want me to generate that too for this one?
