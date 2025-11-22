Here’s a **clean, professional, impressive README** you can use for your n8n WhatsApp AI Agent project.

---

# 🚀 WhatsApp AI Agent using n8n, Meta WhatsApp Cloud API & Local LLM (Ollama)

This project showcases a fully automated **WhatsApp AI Agent** built using **n8n**, **Meta WhatsApp Cloud API**, and a **locally hosted LLM via Ollama**.
It demonstrates how to integrate conversational AI with WhatsApp to automatically process user messages and reply with intelligent responses.

---

## 📌 Features

* 🤖 **AI-powered responses** using a local LLM through **Ollama**
* 🔗 **Workflow automation** via n8n
* 💬 **WhatsApp message handling** (send + receive) using Cloud API
* 🌐 **Secure webhook exposure** using Ngrok
* 🔁 **Two-way communication** between WhatsApp → n8n → AI → WhatsApp
* 🧠 **Dynamic message generation** based on user input
* 📦 **Modular workflow** that can be extended for FAQ bots, assistants, chatbots, CRM, automations, etc.

---

## 🔧 Tech Stack

| Component                   | Purpose                                       |
| --------------------------- | --------------------------------------------- |
| **n8n**                     | Workflow automation engine                    |
| **Meta WhatsApp Cloud API** | Sending & receiving WhatsApp messages         |
| **Ollama**                  | Running local LLMs (e.g., Phi-3, Llama, etc.) |
| **Ngrok**                   | Public webhook URL for Meta                   |
| **Docker**                  | Containerizing n8n + Ollama                   |

---

## 🧩 How It Works

1. User sends message to WhatsApp
2. Meta forwards the message to your n8n webhook
3. Workflow extracts the user’s text
4. n8n sends this text to the **AI Agent node**, which queries the local LLM through Ollama
5. The model generates a reply
6. n8n sends the AI-generated response back to WhatsApp using **Send Message** node
7. User receives an intelligent answer on WhatsApp

---

## 📁 Project Workflow (Simplified)

```
WhatsApp → Webhook → AI Agent (Ollama) → WhatsApp Send Message
```

---

## ⚙️ Setup Instructions

### 1️⃣ Install & Run Docker Containers

* **Ollama container** (LLM)
* **n8n container** (automation)

Ensure both containers are connected through an internal Docker network.

---

### 2️⃣ Install Your Model in Ollama

```bash
ollama pull phi3
```

---

### 3️⃣ Start Ngrok

```bash
ngrok http 5678
```

Copy the forwarding URL (e.g.,
`https://random.ngrok-free.app` )

---

### 4️⃣ Configure Webhook in Meta Developer Portal

* **Callback URL:**
  `https://your-ngrok-url/webhook/whatsapp-webhook`

* **Verify Token:**
  Any token you choose (e.g., `n8nverify`)

---

### 5️⃣ Build Workflow in n8n

Your workflow includes:

* **Webhook (GET/POST)**
* **AI Agent (model = Ollama)**
* **WhatsApp Send Message node**

Map this in Send Message body:

```
{{ $json["response"] }}
```

---

## 🧪 Testing

Send a WhatsApp message like:

```
Explain AI in simple words
```

Your WhatsApp will receive an AI-generated message from the local model.

---

