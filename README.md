# **📰 n8n Daily Tech & Railway News Automation Agent**

An automated AI agent built with **n8n** that curates, summarises, and delivers the latest technology and railway signalling news directly to your inbox and WhatsApp every morning.

![n8n Workflow](https://github.com/JackyZhiJie/n8n-Tech-News-Automation/blob/9121710ae25d4469e0cfa2f70f4f8ed4d62132cd/Daily%20Summarised%20Railway%20News%20Report%20Automation.png)

## **🚀 Project Overview**

This workflow is designed to streamline information intake. Instead of manually checking multiple news sources, this agent acts as a personal research assistant. It fetches RSS feeds, uses a local Large Language Model (LLM) to read and summarise the content, and dispatches a consolidated report.

### **✨ Key Features**

* **⏰ Automated Scheduling:** Triggers daily at 08:00 AM.  
* **📡 Smart Aggregation:** Fetches from *The Verge* and *Global Railway Review*.  
* **🧠 Local AI Processing:** Uses **Llama 3.2 (1B)** via Ollama to generate 100-word executive summaries for each article.  
* **📱 Multi-Channel Delivery:**  
  * **Email:** Formatted HTML report via Gmail.  
  * **WhatsApp:** Instant text alerts for urgent updates.

## **🛠️ Technical Workflow**
```
graph LR
    A[🕒 Schedule Trigger] --> B(📡 RSS Fetcher)
    B --> C{⚡ Limit Top 5}
    C --> D[🧠 AI Agent - Llama 3.2]
    D --> E[📝 Format Data]
    E --> F[📦 Aggregate]
    F --> G[📧 Gmail]
    F --> H[📱 WhatsApp]
```

### **Node Configuration**

| Node Type | Function | Configuration Details |
| :---- | :---- | :---- |
| **Schedule Trigger** | Wake up | Runs everyday at 8:00 AM |
| **RSS Feed Read** | Input | Sources: The Verge, Global Railway Review |
| **AI Agent** | Processor | **Model:** Llama 3.2:1b **Prompt:** "Summarise tech-related news into a paragraph of executive summary." |
| **Gmail** | Output | Sends HTML formatted daily digest |
| **WhatsApp** | Output | Sends text-based quick summary |

## **📊 Performance Metrics**

This workflow is optimised for edge computing on standard business laptops.

* **Host Machine:** Ryzen 5 4650U Pro (CPU Only)  
* **Average Runtime:** \~2 minutes 30 seconds  
* **Token Throughput:** \~4,672 tokens processed per run  
* **Cost:** $0.00 (Running 100% locally)

## **⚙️ Setup & Requirements**

### **Prerequisites**

1. **n8n:** Installed via Docker or npm.  
2. **Ollama:** Running locally with the llama3.2:1b model pulled.  
   ollama pull llama3.2:1b

3. **Credentials:**  
   * Gmail OAuth2 Client ID/Secret.  
   * Meta for Developers App (for WhatsApp Business API).

### **Installation**

1. Open your n8n instance.  
2. Import the Tech News Automation Email.json file.  
3. Update the **Credentials** for Gmail and WhatsApp nodes.  
4. Activate the workflow\!

**Note:** This project is part of the AI Research Initiative focusing on Local LLM Ecosystems.
