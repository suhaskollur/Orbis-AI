# 🤖 Orbis AI Agent – Conversational AI for WhatsApp using n8n

Orbis AI Agent is an intelligent, multi-modal WhatsApp chatbot built with [n8n](https://n8n.io/), integrated with the **WhatsApp Business Cloud API**, **OpenAI**, and additional tools for audio, image, and text processing.

This system is capable of understanding and responding to text prompts, analyzing uploaded images, transcribing audio, generating spoken responses, and even fetching real-time information such as weather — all via WhatsApp.

---

## 📌 Key Features

### 🧠 AI-Powered Chat
- Conversational replies using OpenAI’s GPT model.
- Context retention using memory nodes.

### 🖼️ Image Analysis
- Detects and interprets content from images.
- Generates descriptive responses based on visual inputs.

### 🎤 Audio Interaction
- Converts WhatsApp voice messages to text.
- Responds using synthesized voice audio.

### 💬 Multi-Modal Processing
- Smart routing based on the incoming message type (text, image, or audio).
- Unified response logic via an AI agent node.

### 🌦️ Real-Time Information
- Fetches contextual info like weather from the Internet (via AI API calls or plugin tools like SerpAPI).

---
### Main Nodes

| Node                  | Function                                           |
|-----------------------|----------------------------------------------------|
| WhatsApp Trigger      | Captures incoming user message via webhook         |
| Switch                | Routes flow by content type (text, audio, image)   |
| Download Audio/Image  | Downloads media from WhatsApp                      |
| Transcribe Audio      | Converts audio to text using OpenAI Whisper        |
| Analyze Image         | Uses OpenAI Vision API for image captioning        |
| AI Agent              | Central logic hub with tools + memory + model      |
| Generate Audio        | Converts text to speech (TTS)                      |
| Respond with Text     | Sends back text response                           |
| Respond with Audio    | Sends back audio message                           |

---

## ⚙️ Tech Stack

- **n8n** (visual automation platform)
- **OpenAI GPT / Whisper / Vision** (for AI processing)
- **WhatsApp Business Cloud API**
- **Node.js & JavaScript** (for custom scripting nodes)
- **SerpAPI** (for search/weather data)
- **TTS engine** (for audio response generation)

---

## 🛠️ Setup Instructions

### 1. Clone the Repository

git clone [https://github.com/YOUR_USERNAME/orbis-ai-agent.git](https://github.com/suhaskollur/Orbis-AI.git)

## 🚀 Getting Started

Follow the steps below to set up and run the Orbis AI Agent on your local or cloud n8n instance.

---

### 📥 2. Import Workflows into n8n

1. Open **n8n** (either locally or via n8n Cloud).
2. Click the **☰ menu** in the top-left and select **"Import Workflow"**.
3. Upload the exported workflow file located in the `/workflows/` directory of this repository.

---

### 🔐 3. Configure API Credentials

In **n8n**, go to the **Credentials** section and create the following:

- **OpenAI API Key**  
  Used for generating text responses, transcribing audio, and analyzing images.

- **WhatsApp Business Cloud API Credentials**  
  - Access Token (with `whatsapp_business_messaging` permission)  
  - Phone Number ID (not the raw phone number)

- **SerpAPI Key (optional)**  
  Used for fetching live weather updates or search-based answers.

> 🔒 **Tip**: Never commit these credentials to your repository. Use `.env` files or secure vaults if needed.

---

### 🌐 4. Set Up WhatsApp Webhook (Meta)

To receive messages from users via WhatsApp:

1. Go to [Meta Developer Console](https://developers.facebook.com/).
2. Under your app, navigate to **"WhatsApp > Configuration"**.
3. Set your webhook URL to point to your n8n instance’s webhook node (e.g., `https://your-n8n-domain/webhook/whatsapp`).
4. Configure webhook events:
   - `messages`
   - `message_status`
   - `message_template`

5. Verify the webhook using the token mechanism provided by Meta.
6. Use a **live number** or **sandbox number** to test incoming messages and bot replies.

> 📱 You can now interact with the bot over WhatsApp and test its ability to respond to text, audio, and image inputs.
