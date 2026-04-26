<p align="center">
  <img src="https://img.shields.io/badge/🏥_MedAssist-AI_Medical_Chatbot-0ea5e9?style=for-the-badge&labelColor=0f172a" alt="MedAssist"/>
</p>

<h1 align="center">MedAssist — Agentic AI Medical Chatbot</h1>

<p align="center">
  <em>An intelligent, multi-tool medical assistant powered by LangChain Agents, GPT-4o Vision, and real-time FDA data</em>
</p>

<p align="center">
  <a href="https://rajaganaa.github.io/medassist-frontend">
    <img src="https://img.shields.io/badge/🔴_LIVE_DEMO-Click_Here-ef4444?style=for-the-badge&labelColor=1e293b" alt="Live Demo"/>
  </a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.9+-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python"/>
  <img src="https://img.shields.io/badge/Azure_Functions-Serverless-0078D4?style=flat-square&logo=microsoft-azure&logoColor=white" alt="Azure"/>
  <img src="https://img.shields.io/badge/LangChain-Agents-1C3C3C?style=flat-square&logo=langchain&logoColor=white" alt="LangChain"/>
  <img src="https://img.shields.io/badge/OpenAI-GPT--4o-412991?style=flat-square&logo=openai&logoColor=white" alt="OpenAI"/>
  <img src="https://img.shields.io/badge/GitHub_Pages-Frontend-222222?style=flat-square&logo=github&logoColor=white" alt="GitHub Pages"/>
  <img src="https://img.shields.io/badge/ChromaDB-Vector_Store-FF6F00?style=flat-square" alt="ChromaDB"/>
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" alt="License"/>
</p>

---

## 🌟 What is MedAssist?

**MedAssist** is a production-deployed **Agentic AI chatbot** that helps users get reliable information about medications. Upload a photo of any medicine, and MedAssist will:

- 📸 **Extract** drug name, strength, expiry date, and manufacturer using **GPT-4o Vision**
- 🔍 **Search** a curated medical database using **RAG (Retrieval-Augmented Generation)**
- 📊 **Fetch** real adverse event reports from the **FDA FAERS database**
- 🧮 **Calculate** weight-based dosage for common medications
- 📅 **Check** if the medicine is expired

All through a natural **multi-turn conversation** — just like chatting with a pharmacist.

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                        MEDASSIST ARCHITECTURE                       │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│   ┌─────────────┐         ┌──────────────────────────────────────┐ │
│   │   Frontend   │  HTTPS  │       Azure Functions Backend        │ │
│   │  (GitHub     │────────▶│                                      │ │
│   │   Pages)     │◀────────│  ┌──────────┐   ┌────────────────┐  │ │
│   │              │         │  │  Query    │──▶│  LangChain     │  │ │
│   │  index.html  │         │  │  Rewriter │   │  Agent         │  │ │
│   │  • Chat UI   │         │  └──────────┘   │  (GPT-4o-mini) │  │ │
│   │  • Image     │         │                 │                 │  │ │
│   │    Upload    │         │  ┌──────────┐   │  Decides which  │  │ │
│   │  • Tool      │         │  │ Session  │   │  tools to use   │  │ │
│   │    Status    │         │  │ Memory   │   └───────┬─────────┘  │ │
│   └─────────────┘         │  └──────────┘           │             │ │
│                           │                ┌────────┴─────────┐   │ │
│                           │                ▼                  ▼   │ │
│                           │  ┌──────────────┐  ┌──────────────┐  │ │
│                           │  │ 📚 RAG Search │  │ 📊 FDA API   │  │ │
│                           │  │ (ChromaDB +   │  │ (OpenFDA     │  │ │
│                           │  │  Medical PDFs)│  │  FAERS Data) │  │ │
│                           │  └──────────────┘  └──────────────┘  │ │
│                           │  ┌──────────────┐  ┌──────────────┐  │ │
│                           │  │ 🧮 Dosage    │  │ 📅 Expiry    │  │ │
│                           │  │ Calculator   │  │ Checker      │  │ │
│                           │  │ (Python)     │  │ (Python)     │  │ │
│                           │  └──────────────┘  └──────────────┘  │ │
│                           └──────────────────────────────────────┘ │
│                                                                     │
│   ┌─────────────────────────────────────────────────────────────┐   │
│   │                    GPT-4o Vision                             │   │
│   │    Medicine Image → Extract Name, Strength, Expiry, etc.    │   │
│   └─────────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────────┘
```

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 📸 **Vision-Powered Analysis** | Upload a medicine photo → GPT-4o extracts drug name, strength, expiry, manufacturer |
| 🤖 **Agentic AI** | LangChain agent autonomously decides which tools to use for each query |
| 📚 **RAG Search** | Searches curated medical PDFs via ChromaDB vector store |
| 📊 **FDA Real Data** | Fetches actual adverse event reports from FDA FAERS database |
| 🧮 **Dosage Calculator** | Weight & age-based dosage computation for common drugs |
| 📅 **Expiry Checker** | Parses 6+ date formats, checks validity with detailed status |
| 💬 **Multi-Turn Chat** | Context-aware conversations — "Is it expired?" resolves to the uploaded medicine |
| 🔄 **Query Rewriting** | Transforms ambiguous follow-ups into precise standalone queries |
| 🎯 **Tool Transparency** | UI shows which tools were used (✓), tried/failed (✗), or skipped (○) |
| 🌐 **Fully Deployed** | Frontend on GitHub Pages, Backend on Azure Functions — zero server management |

---

## 🛠️ Tech Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **Frontend** | HTML/CSS/JS | Single-page chat interface |
| **Hosting (FE)** | GitHub Pages | Static site hosting |
| **Backend** | Azure Functions (Python) | Serverless API |
| **LLM** | GPT-4o-mini (GitHub Models) | Agent reasoning & responses |
| **Vision** | GPT-4o Vision | Medicine image analysis |
| **Agent Framework** | LangChain | Tool-using agent orchestration |
| **Vector Store** | ChromaDB | Document embeddings for RAG |
| **Embeddings** | OpenAI text-embedding-3-small | Text vectorization |
| **External API** | OpenFDA FAERS | Real adverse event data |
| **PDF Processing** | PyPDF | Medical document loading |

---

## 🔄 How It Works — Agent Flow

```
User Message
     │
     ▼
┌─────────────────┐
│ Query Rewriter   │  "Is it expired?" → "Is Paracetamol 650mg expired? Expiry: Dec 2025"
│ (Context-Aware)  │
└────────┬────────┘
         ▼
┌─────────────────┐
│ LangChain Agent  │  Analyzes the query and decides which tool(s) to call
│ (GPT-4o-mini)    │
└────────┬────────┘
         │
    ┌────┼────┬────────┐
    ▼    ▼    ▼        ▼
  📚    📊   🧮       📅
  RAG   FDA  Dosage   Expiry
         │
         ▼
┌─────────────────┐
│ Agent Response   │  Synthesizes tool results into a natural language answer
│ + Source Labels  │  📚 From database | 📊 From FDA | 💡 LLM Knowledge
└─────────────────┘
```

---

## 📁 Project Structure

```
medassist/
├── 🌐 frontend/                    ← medassist-frontend repo (GitHub Pages)
│   ├── index.html                   # Complete single-page application
│   └── staticwebapp.config.json     # Routing config
│
├── ⚡ backend/                      ← medassist-backend repo (Azure Functions)
│   ├── function_app.py              # HTTP endpoints (chat, upload, clear, health)
│   ├── components/
│   │   ├── memory.py                # Session & medicine context management
│   │   ├── query_rewriter.py        # Follow-up → standalone query transform
│   │   └── vision_extractor.py      # GPT-4o Vision integration
│   ├── tools/
│   │   ├── rag_search.py            # ChromaDB medical PDF search
│   │   ├── fda_api.py               # OpenFDA adverse events API
│   │   ├── dosage_calc.py           # Weight-based dosage computation
│   │   └── expiry_check.py          # Date parsing & expiry validation
│   ├── data/drug_guides/            # 5 curated medical PDFs
│   ├── build_vectorstore.py         # ChromaDB builder utility
│   ├── host.json                    # Azure Functions config
│   └── requirements.txt             # Python dependencies
│
├── README.md                        # This file
├── LICENSE                          # MIT License
└── CONTRIBUTING.md                  # Contribution guidelines
```

---

## 🚀 Local Development Setup

### Prerequisites
- Python 3.9+
- [Azure Functions Core Tools v4](https://learn.microsoft.com/en-us/azure/azure-functions/functions-run-local)
- [GitHub Models API Key](https://github.com/marketplace/models) (free)

### 1. Backend Setup

```bash
# Clone backend
git clone https://github.com/rajaganaa/medassist-backend.git
cd medassist-backend

# Create virtual environment
python -m venv .venv
.venv\Scripts\activate          # Windows
# source .venv/bin/activate     # Linux/Mac

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
cp .env.example .env
# Edit .env → add your OPENAI_API_KEY (GitHub Models token)

# Build vector store from medical PDFs
python build_vectorstore.py

# Start the Azure Functions backend
func start
```

Backend runs at → `http://localhost:7071/api/`

### 2. Frontend Setup

```bash
# Clone frontend
git clone https://github.com/rajaganaa/medassist-frontend.git
cd medassist-frontend

# Update API_BASE in index.html to point to local backend:
# const API_BASE = 'http://localhost:7071/api';

# Open in browser
start index.html
# Or use Live Server extension in VS Code
```

---

## ☁️ Deployment Guide

### Backend → Azure Functions

```bash
# Login to Azure
az login

# Create resources
az group create --name medassist-rg --location centralindia
az functionapp create \
    --name medassist-api \
    --resource-group medassist-rg \
    --consumption-plan-location centralindia \
    --runtime python \
    --runtime-version 3.9 \
    --os-type linux \
    --functions-version 4

# Set environment variables
az functionapp config appsettings set \
    --name medassist-api \
    --resource-group medassist-rg \
    --settings OPENAI_API_KEY="your-key" \
               OPENAI_BASE_URL="https://models.inference.ai.azure.com"

# Deploy
func azure functionapp publish medassist-api
```

### Frontend → GitHub Pages

1. Push `index.html` to the `medassist-frontend` repo
2. Go to **Settings → Pages**
3. Set Source to **Deploy from a branch** → `main` → `/ (root)`
4. Update `API_BASE` in `index.html` to your Azure Function URL

---

## 📡 API Documentation

### `GET /api/health`
Health check endpoint.

**Response:**
```json
{
    "status": "healthy",
    "version": "1.0.0",
    "timestamp": "2026-04-25T12:00:00"
}
```

### `POST /api/chat`
Send a message to the MedAssist agent.

**Request:**
```json
{
    "session_id": "session_123",
    "message": "What is paracetamol used for?"
}
```

**Response:**
```json
{
    "response": "Paracetamol is used for...",
    "tools_used": ["search_drug_database"],
    "tools_status": [
        {"name": "search_drug_database", "status": "success", "success": true},
        {"name": "get_fda_adverse_events", "status": "not_used", "success": false},
        {"name": "calculate_dosage", "status": "not_used", "success": false},
        {"name": "check_medicine_expiry", "status": "not_used", "success": false},
        {"name": "llm_knowledge", "status": "not_used", "success": false}
    ],
    "rewritten_query": null,
    "medicine_context": null
}
```

### `POST /api/upload-image`
Upload and analyze a medicine image.

**Request:**
```json
{
    "session_id": "session_123",
    "image_data": "<base64_encoded_image>",
    "image_type": "image/jpeg"
}
```

**Response:**
```json
{
    "success": true,
    "medicine_info": {
        "generic_name": "Paracetamol",
        "brand_name": "Dolo",
        "strength": "650mg",
        "form": "Tablet",
        "expiry_date": "Dec 2025",
        "manufacturer": "Micro Labs"
    },
    "message": "Analyzed: Paracetamol 650mg"
}
```

### `POST /api/clear`
Clear session conversation and medicine context.

**Request:**
```json
{
    "session_id": "session_123"
}
```

### `GET /api/session/{session_id}`
Get current session info (medicine context, etc).

---

## 📸 Screenshots

> *Screenshots coming soon — try the [live demo](https://rajaganaa.github.io/medassist-frontend) in the meantime!*

<!-- Add screenshots here:
![Chat Interface](screenshots/chat.png)
![Medicine Analysis](screenshots/analysis.png)
![Tool Status](screenshots/tools.png)
-->

---

## 🗺️ Roadmap

- [ ] Drug interaction checker tool
- [ ] Multi-language support (Hindi, Tamil)
- [ ] Voice input for queries
- [ ] Prescription OCR & parsing
- [ ] User authentication & history
- [ ] Mobile-responsive PWA

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file.

---

## 👨‍💻 Author

<p align="center">
  <strong>RAJAGANAPATHY M</strong><br/>
  <em>AI/ML Post Graduate Student</em><br/>
  <em>SRM University, Chennai</em><br/><br/>
  <a href="https://github.com/rajaganaa">
    <img src="https://img.shields.io/badge/GitHub-rajaganaa-181717?style=flat-square&logo=github" alt="GitHub"/>
  </a>
</p>

---

<p align="center">
  <sub>Built with ❤️ using LangChain, Azure Functions, and GPT-4o</sub><br/>
  <sub>⭐ Star this repo if you found it useful!</sub>
</p>
