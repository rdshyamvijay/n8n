# Social Media Automation Workflow

This n8n workflow automates the process of generating, reviewing, and publishing social media content across **LinkedIn**, **Instagram**, **Facebook**, and **X (formerly Twitter)** — all at once.

The automation is structured into four major steps:

---

## Step 1: Create Social Media Written Content

### What it does:
- Collects user input via a form (topic, tone, audience, etc.)
- Passes this input to the **Social Media Content Factory**, powered by:
  - GPT-4
  - Google Gemini
  - SerpAPI (optional real-time search)
- Generates platform-specific social media captions

### Optional:
- Formats an approval email with the generated content
- Sends the email via Gmail for manual approval
- Uses a `sendAndWait` block to pause execution until approval is received

### How to use:
- Start by submitting your content requirements in the "Submit Social Post Details" node
- Review and approve via email (or skip this step)
- The written content is passed to the image generation step

---

## Step 2: Create Image or Upload Image for Social Post

### What it does:
- Creates an image using OpenAI (DALL·E) based on the post content
- Alternatively, allows uploading a custom image
- Uploaded/generated image is saved to **imgbb.com**
- The image URL is passed forward for use in final publishing

### Optional:
- An alternate image generation method (`pollinations.ai`) is present but deactivated
- A user-upload form section is available for manual image selection (also deactivated)

### How to use:
- Ensure your OpenAI API key and imgbb credentials are set
- Enable the user-upload section if needed
- The image will be merged with content and forwarded automatically

---

## Step 3: Publish Final Social Media Posts

### What it does:
- Prepares content for final publishing
- Offers an optional post-approval step (deactivated by default)
- Publishes content to:
  - Instagram
  - Facebook
  - X (Twitter)
  - LinkedIn
- Formats the result data (post IDs, URLs, etc.)

### How to use:
- Authenticate each platform within n8n (Facebook, Instagram, X, LinkedIn)
- Modify or disable the manual approval step as required
- The publishing happens automatically once all conditions are met

---

## Step 4: Send Final Results of Social Media Factory

### What it does:
- Aggregates the results of all posted content
- Uses GPT-4 (mini) to summarize and format the outcome
- Sends a final update via:
  - Gmail (email)
  - Telegram (message)

### How to use:
- Set up Gmail and Telegram Bot credentials
- Messages are formatted and sent automatically

---

## Required Integrations

Make sure these are configured in your n8n instance:

- **OpenAI API**: https://auth.openai.com
- **SerpAPI (optional)**: https://serpapi.com
- **Gmail OAuth**: https://docs.n8n.io/integrations/builtin/credentials/google/
- **Telegram Bot (optional)**: https://docs.n8n.io/integrations/builtin/credentials/telegram/
- **imgbb (image hosting)**: https://imgbb.com

---

## Benefits

- One-click publishing to four major platforms
- Auto-generated and tailored content using advanced LLMs
- Approval steps for quality control
- Optional manual image upload or auto-generation
- Easy to customize and scale

---

## Future Enhancements

- Add support for Threads and YouTube Shorts
- Introduce scheduling and queuing
- Auto-translate posts into other languages
- Integrate with CRM or CMS systems

---

## License

This workflow is provided for personal and commercial use. Attribution appreciated but not required.
