# AI Customer Support Assistant — WhatsApp Ready

This workflow turns your website into a live customer support agent on WhatsApp. It crawls your domain (products, FAQs, policies) on demand and uses that content to answer user queries in real time. Context is preserved across the conversation using memory stored in Supabase/Postgres.

---

## What It Does

- On each user message, the bot fetches fresh content from your domain (no manual uploads or fine‑tuning needed)  [oai_citation:0‡n8n](https://n8n.io/workflows/3859-ai-customer-support-assistant-whatsapp-ready-works-for-any-business/)  
- Maintains chat history: each turn is stored and replayed into the next prompt so follow‑ups “make sense”  [oai_citation:1‡n8n](https://n8n.io/workflows/3859-ai-customer-support-assistant-whatsapp-ready-works-for-any-business/)  
- Supports free‑form responses within WhatsApp’s 24‑hour window; switches to message templates when required by Meta policies  [oai_citation:2‡n8n](https://n8n.io/workflows/3859-ai-customer-support-assistant-whatsapp-ready-works-for-any-business/)  
- Minimal setup: add OpenAI, WhatsApp, and Supabase credentials; point to your domain; expose a webhook.  [oai_citation:3‡n8n](https://n8n.io/workflows/3859-ai-customer-support-assistant-whatsapp-ready-works-for-any-business/)  

---

## Setup Instructions

1. Import the workflow into your n8n environment  
2. Add credentials for:
   - OpenAI  
   - WhatsApp (Meta) Cloud API  
   - Supabase (or Postgres) for chat memory  
3. Set a `root_url` variable to your domain  
4. Configure the webhook in Meta’s WhatsApp dashboard to point to your n8n URL  
5. Trigger the flow and send “Hi” from WhatsApp to test  
6. The bot will respond based on live data from your site  [oai_citation:4‡n8n](https://n8n.io/workflows/3859-ai-customer-support-assistant-whatsapp-ready-works-for-any-business/)  

---

## Key Nodes & Their Roles

| Node | Role |
|---|---|
| Webhook / Trigger | Receives incoming WhatsApp messages |
| Domain Crawler | Fetches updated website content (products, FAQs, etc.) |
| AI / OpenAI | Generates replies using context + fetched content |
| Memory Storage (Supabase/Postgres) | Persists chat history and context |
| WhatsApp Reply | Sends responses via WhatsApp API |
| Template Fallback | Uses Meta message templates when needed |

---

## What It Replaces / Simplifies

- Manual content upload or fine‑tuning models  
- Standalone SaaS chat solutions for WhatsApp  
- Maintaining a separate knowledge base or CMS for chat  
- Custom coding of chat agents and memory logic  

---

## Advantages & Benefits (Practical)

- Always‑live content: the bot is always fetching from your site, so answers stay up to date  
- Contextual conversation: memory helps answer follow‑ups sensibly  
- Channel readiness: built for WhatsApp out of the box, but adaptable to other channels  
- Low maintenance: minimal manual overhead once set up  
- Cost control: you don’t need an expensive third‑party chatbot platform  

---

## Requirements & Notes

- OpenAI API key  
- Meta WhatsApp Cloud API number + permanent token  [oai_citation:5‡n8n](https://n8n.io/workflows/3859-ai-customer-support-assistant-whatsapp-ready-works-for-any-business/)  
- Supabase or Postgres instance for chat memory  [oai_citation:6‡n8n](https://n8n.io/workflows/3859-ai-customer-support-assistant-whatsapp-ready-works-for-any-business/)  
- A domain with content (product pages, FAQs, etc.)  
- n8n instance (self‑hosted or cloud)  
- A webhook endpoint exposed to WhatsApp  
- Test in a safe environment before going live  

---

If you like, I can also generate a schematic diagram or prompt examples to include in this README. Do you want me to add those?
