# Meridian — AI Market Research & Strategy Engine

[![Live Demo](https://img.shields.io/badge/Live-Demo-2ea44f?style=for-the-badge)](https://meridian-fronted-resarch-engine.vercel.app/)
[![React](https://img.shields.io/badge/Frontend-React%2019%20%2B%20Vite-61DAFB?style=for-the-badge)](https://react.dev/)
[![FastAPI](https://img.shields.io/badge/Backend-FastAPI-009688?style=for-the-badge)](https://fastapi.tiangolo.com/)
[![Supabase](https://img.shields.io/badge/Database-Supabase-3ECF8E?style=for-the-badge)](https://supabase.com/)
[![Gemini](https://img.shields.io/badge/LLM-Google%20Gemini-4285F4?style=for-the-badge)](https://ai.google.dev/)
[![Tavily](https://img.shields.io/badge/Search-Tavily-111111?style=for-the-badge)](https://tavily.com/)

> **An autonomous multi-agent system that turns a research brief into a fully cited, evidence-grounded market report.**

### 🚀 Live Application

**[Open Meridian](https://meridian-fronted-resarch-engine.vercel.app/)**

---

## 📌 What Is Meridian?

**Meridian** is an AI-powered market research and strategy engine designed to automate the workflow typically performed by market researchers, business analysts, and strategy teams.

A user submits a natural-language research brief. Meridian then uses a **seven-stage AI agent pipeline** to:

1. Break the research brief into structured tasks.
2. Search the live web for relevant sources.
3. Extract supporting evidence.
4. Validate the evidence.
5. Build citations.
6. Generate a structured strategy report.
7. Link report findings back to their supporting evidence and sources.

The result is a **consulting-style, evidence-grounded report** where important findings can be traced back to their original sources.

---

## 🎯 Business Problem

Traditional market research often requires significant manual effort across multiple stages:

* Searching multiple websites and information sources
* Identifying relevant information from large amounts of content
* Extracting useful evidence and supporting claims
* Validating reliability and relevance
* Organizing findings into a structured report
* Maintaining a clear citation trail

Meridian automates this workflow through a multi-agent AI pipeline while keeping the research process **evidence-grounded and traceable**.

### Target Users

* Strategy Consultants
* Business Analysts
* Market Researchers
* Product Managers
* Startup Founders

---

## 🚀 Product Goal

The goal of Meridian is to provide an AI-powered research assistant that transforms a natural-language research brief into a structured, evidence-grounded market research report.

The system combines:

* Multi-agent AI reasoning
* Live web research
* Evidence extraction
* Evidence validation
* Citation generation
* Structured report generation
* Evidence-to-report traceability
* Secure user authentication
* Persistent research data storage

---

# ⭐ Key Highlights

### 🤖 Seven-Agent Research Pipeline

Seven specialized AI agents work together:

**Planner → Research → Extraction → Validation → Citation → Report → Linker**

Each agent has a focused responsibility and passes structured output to the next stage.

### 🔎 Live Web Research

The Research Agent uses **Tavily Search API** to retrieve relevant web sources for research tasks.

### 📚 Evidence-Grounded Reports

The system extracts and validates evidence before using it to generate the final report.

### 🔗 Full Traceability

Report findings are linked to supporting evidence and citations, allowing users to move from the final narrative to the underlying source.

### 🔐 Secure Authentication

Supabase Auth is used for authentication, with server-side token verification and user-level research ownership checks.

### ⚡ Reliability Features

The pipeline includes:

* Retry handling
* Exponential backoff
* Fallback handling
* Evidence validation
* Fail-fast execution
* Batched processing

---

# 🏗️ System Architecture

Meridian is divided into independently deployed frontend and backend services that communicate through a REST API secured with Supabase authentication.

```text
                    ┌──────────────────────┐
                    │       User           │
                    │   Research Brief     │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   React Frontend      │
                    │    Vite Dashboard     │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   FastAPI Backend     │
                    │   Authentication &    │
                    │   Orchestration       │
                    └──────────┬───────────┘
                               │
                               ▼
             ┌────────────────────────────────────┐
             │       Seven-Agent AI Pipeline       │
             │                                    │
             │ Planner → Research → Extraction    │
             │     ↓                               │
             │ Validation → Citation → Report      │
             │                    ↓                │
             │                  Linker             │
             └───────────────────┬────────────────┘
                                 │
                                 ▼
                    ┌──────────────────────┐
                    │      Supabase        │
                    │ PostgreSQL + Auth +   │
                    │      pgvector        │
                    └──────────────────────┘
```

### Architecture Components

| Layer            | Responsibility                    |
| ---------------- | --------------------------------- |
| Frontend         | React 19 + Vite dashboard         |
| Backend          | FastAPI API and orchestration     |
| Planner Agent    | Creates structured research tasks |
| Research Agent   | Performs live web searches        |
| Extraction Agent | Extracts evidence from sources    |
| Validation Agent | Validates evidence                |
| Citation Builder | Creates citation objects          |
| Report Agent     | Generates the final report        |
| Report Linker    | Links findings to evidence        |
| Database         | Supabase PostgreSQL persistence   |

---

# 🧠 The Multi-Agent Research Pipeline

The core pipeline is orchestrated by:

```text
ai/pipeline/research_pipeline.py
```

Each stage has one focused responsibility.

| Stage             | Module                              | Responsibility                                                  |
| ----------------- | ----------------------------------- | --------------------------------------------------------------- |
| **1. Planning**   | `ai/planner/planner_agent.py`       | Decomposes the research brief into searchable research tasks    |
| **2. Research**   | `ai/research/research_agent.py`     | Performs live web searches using Tavily                         |
| **3. Extraction** | `ai/extraction/extraction_agent.py` | Extracts concrete evidence and supporting quotes                |
| **4. Validation** | `ai/validation/validation_agent.py` | Validates evidence and assigns confidence verdicts              |
| **5. Citation**   | `ai/report/citation_builder.py`     | Converts sources into citation objects                          |
| **6. Report**     | `ai/report/report_agent.py`         | Generates the structured strategy report                        |
| **7. Linker**     | `ai/report/report_linker.py`        | Connects report findings with supporting evidence and citations |

### Fail-Fast Pipeline

The pipeline is designed to fail fast.

If an essential stage produces an empty result — such as no research tasks, no sources, or no evidence — the pipeline stops instead of silently generating an incomplete report.

---

# 🔍 LLM & Search Providers

### Google Gemini

Gemini is used as the reasoning engine for:

* Planner Agent
* Evidence Extraction Agent
* Validation Agent
* Report Agent

Implementation:

```text
ai/llm/gemini.py
```

### Tavily

Tavily provides live web search capabilities for the Research Agent.

Implementation:

```text
ai/browser/tavily_search.py
```

A mock search implementation is also available for offline development.

---

# ⚙️ Backend — FastAPI

The backend provides the API layer, authentication enforcement, research orchestration, and database persistence.

### Backend Structure

```text
backend/
├── main.py
├── core/
│   ├── config.py
│   ├── auth.py
│   ├── errors.py
│   └── logging.py
├── middleware/
│   └── request_id.py
├── api/
│   ├── research.py
│   ├── reports.py
│   └── evidence.py
├── repositories/
├── services/
│   └── research_service.py
└── db/
    ├── supabase_client.py
    └── migrations/
```

---

## 🔐 Authentication & Authorization

Meridian uses Supabase Auth with server-side authentication checks.

The authentication flow is:

1. The user signs in through the frontend.
2. Supabase provides an access token.
3. The frontend sends the token as a `Bearer` token.
4. The FastAPI backend verifies the token.
5. The authenticated user is injected into protected routes.
6. Job ownership is checked before user-specific research data is returned.

This prevents users from accessing research jobs belonging to other users.

---

# 🌐 API Surface

| Method | Route                                | Purpose                       |
| ------ | ------------------------------------ | ----------------------------- |
| `GET`  | `/`                                  | Service metadata / liveness   |
| `GET`  | `/health`                            | Health check                  |
| `GET`  | `/api/research/`                     | List user's research jobs     |
| `POST` | `/api/research/`                     | Submit a research brief       |
| `GET`  | `/api/research/{job_id}`             | Fetch job status and metadata |
| `GET`  | `/api/research/{job_id}/tasks`       | Fetch planner tasks           |
| `GET`  | `/api/research/{job_id}/sources`     | Fetch discovered sources      |
| `GET`  | `/api/research/{job_id}/evidence`    | Fetch extracted evidence      |
| `GET`  | `/api/research/{job_id}/validations` | Fetch validation results      |
| `GET`  | `/api/research/{job_id}/report`      | Fetch generated report        |

Interactive API documentation is available through FastAPI Swagger:

```text
http://localhost:8000/docs
```

---

# 🎨 Frontend — React + Vite

The frontend provides the user-facing research workspace.

### Frontend Structure

```text
src/
├── App.jsx
├── main.jsx
├── context/
│   ├── AuthContext.jsx
│   └── ThemeContext.jsx
├── components/
│   ├── ProtectedRoute.jsx
│   ├── AuthLayout.jsx
│   ├── Shell.jsx
│   ├── StatusBadge.jsx
│   └── Footer.jsx
├── pages/
│   ├── Login.jsx
│   ├── Signup.jsx
│   ├── Dashboard.jsx
│   ├── ResearchProgress.jsx
│   ├── ReportView.jsx
│   ├── Methodology.jsx
│   └── AboutProject.jsx
├── api/
│   └── client.js
└── lib/
    └── supabaseClient.js
```

### Main User Routes

| Route              | Page              | Access    |
| ------------------ | ----------------- | --------- |
| `/login`           | Login             | Public    |
| `/signup`          | Signup            | Public    |
| `/`                | Dashboard         | Protected |
| `/research/new`    | Research Progress | Protected |
| `/research/:jobId` | Report View       | Protected |
| `/methodology`     | Methodology       | Protected |
| `/about`           | About Project     | Protected |

### Design System

The interface follows a **navy-and-gold consulting-style design** intended to provide a professional strategy-research experience.

Technologies include:

* Tailwind CSS v4
* Framer Motion
* Lucide React
* React Icons
* FontAwesome

---

# 🗄️ Database — Supabase / PostgreSQL

Meridian uses Supabase for authentication and persistent research data storage.

The database includes:

| Migration | Purpose                        |
| --------- | ------------------------------ |
| `001`     | Initial research jobs schema   |
| `002`     | Planner tasks                  |
| `003`     | Sources                        |
| `004`     | Evidence                       |
| `005`     | Validation records             |
| `006`     | Memory / `pgvector` foundation |
| `007`     | Reports                        |
| `008`     | Indexes                        |

### Database Architecture

```text
Supabase
│
├── research_jobs
├── planner_tasks
├── sources
├── evidence
├── validation_records
├── reports
├── feedback
└── memory_records
```

`research_jobs.created_by` references `auth.users(id)` to support authenticated user ownership and data isolation.

---

# 🧰 Technology Stack

| Layer               | Technology            |
| ------------------- | --------------------- |
| Frontend            | React 19 + Vite       |
| Styling             | Tailwind CSS v4       |
| Animation           | Framer Motion         |
| Routing             | React Router v7       |
| Frontend Auth       | Supabase JS           |
| Backend             | FastAPI               |
| Language            | Python                |
| Server              | Uvicorn               |
| Configuration       | Pydantic Settings     |
| Database            | Supabase / PostgreSQL |
| Vector Foundation   | pgvector              |
| Authentication      | Supabase Auth         |
| LLM                 | Google Gemini         |
| Web Search          | Tavily                |
| Frontend Deployment | Vercel                |
| Backend Deployment  | Render                |

---

# 🔄 End-to-End User Flow

```text
User Sign Up / Login
        ↓
Dashboard
        ↓
Submit Research Brief
        ↓
Planner Agent
        ↓
Research Agent
        ↓
Evidence Extraction
        ↓
Evidence Validation
        ↓
Citation Builder
        ↓
Report Generation
        ↓
Report Linker
        ↓
Final Report
        ↓
Evidence + Sources
```

### User Experience

1. User signs up or logs in.
2. User enters a research brief.
3. The research progress screen displays the seven stages.
4. The backend executes the research pipeline.
5. Intermediate research artifacts are stored in Supabase.
6. The completed report is displayed.
7. Users can inspect the **Report, Evidence, and Sources**.

---

# 🛡️ Security

Meridian uses several security measures:

| Safeguard                | Description                                                    |
| ------------------------ | -------------------------------------------------------------- |
| Two-tier Supabase keys   | Public anon key for frontend, service-role key only on backend |
| Server-verified sessions | Backend independently verifies authentication tokens           |
| User data isolation      | Users can access only their own research jobs                  |
| Restricted CORS          | Approved frontend origins can be configured                    |
| Environment variables    | Secrets are stored outside source code                         |

> **Never expose the Supabase service-role key in the frontend or commit it to GitHub.**

---

# ⚡ Reliability & Optimization

Meridian includes several mechanisms designed to improve pipeline reliability.

### Retry Logic

Temporary Gemini failures can be retried with exponential backoff.

```text
Retry 1 → 2 seconds
Retry 2 → 4 seconds
Retry 3 → 8 seconds
```

### Fallback Handling

Fallback handling helps the workflow continue when the primary model or search flow encounters temporary problems.

### Batch Processing

Evidence extraction and validation can be processed in batches to reduce unnecessary API calls and token usage.

### Evidence Validation

Extracted evidence is validated before being used in the final report.

### Fail-Fast Execution

The pipeline stops when an essential stage produces an empty result instead of silently generating an incomplete report.

---

# 🧪 Evaluation & Testing

The project has been tested across key components of the research workflow.

### Tested Components

* Planner Agent
* Gemini connection
* Planner output validation
* Dependency validation
* Research pipeline
* Evidence validation
* End-to-end research execution

### Pipeline Validation

A successful execution follows:

```text
Planner
  ↓
Research
  ↓
Extraction
  ↓
Validation
  ↓
Citation
  ↓
Report
  ↓
Linker
```

The final output contains a structured report with supporting evidence and citations.

---

# 📁 Project Structure

```text
Meridian/
│
├── frontend/
│
├── backend/
│   ├── api/
│   ├── core/
│   ├── middleware/
│   ├── repositories/
│   ├── services/
│   └── db/
│
├── ai/
│   ├── planner/
│   ├── research/
│   ├── extraction/
│   ├── validation/
│   ├── report/
│   ├── pipeline/
│   ├── browser/
│   ├── llm/
│   └── schemas/
│
├── docs/
├── tests/
├── requirements.txt
└── README.md
```

---

# 🚀 Getting Started

## Prerequisites

Install:

* Git
* Node.js 18+
* Python 3.11+

---

## 1. Clone the Repository

```bash
git clone https://github.com/adityatygi/Meridian---AI-Market-Research-Strategy-Engine.git
cd Meridian---AI-Market-Research-Strategy-Engine
```

---

## 2. Backend Setup

Create a virtual environment:

```bash
python -m venv venv
```

### Windows

```bash
venv\Scripts\activate
```

### macOS / Linux

```bash
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r backend/requirements.txt
```

---

## 3. Backend Environment Variables

Create a `.env` file for the backend:

```env
GOOGLE_API_KEY=your_gemini_api_key
TAVILY_API_KEY=your_tavily_api_key
SUPABASE_URL=your_supabase_url
SUPABASE_KEY=your_supabase_service_role_key
```

Start the backend:

```bash
uvicorn backend.main:app --reload --port 8000
```

Backend:

```text
http://localhost:8000
```

Swagger documentation:

```text
http://localhost:8000/docs
```

---

## 4. Frontend Setup

Open a new terminal:

```bash
cd frontend
npm install
```

Create the frontend `.env` file:

```env
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
VITE_API_BASE_URL=http://localhost:8000
```

Start the frontend:

```bash
npm run dev
```

Frontend:

```text
http://localhost:5173
```

---

## 5. Supabase Setup

1. Create a Supabase project.
2. Run the migration files in `backend/db/migrations/` in numerical order.
3. Copy the Supabase project URL.
4. Add the frontend anon/public key.
5. Add the backend service-role key only to the backend environment.

---

## 6. Verify the Application

1. Open the frontend.
2. Create an account.
3. Submit a research brief.
4. Watch the seven pipeline stages.
5. Wait for the research report.
6. Open the **Report** tab.
7. Inspect the **Evidence** and **Sources** tabs.

---

# 📝 Sample Research Query

```text
Student placement rate and career outcomes at AlmaBetter compared to other edtech platforms in India.
```

### Expected Output

* Research Tasks
* Web Sources
* Extracted Evidence
* Validation Results
* Citations
* Executive Summary
* Key Findings
* Strategic Insights
* Recommendations
* Evidence / Sources

---

# 📸 Screenshots

## 1. Sign Up

The authentication interface allows new users to create an account securely.

![Meridian Sign Up](https://private-user-images.githubusercontent.com/260417729/646908927-fdb29a53-0905-4148-88ed-8c6cafb0357b.png)

---

## 2. Query Input

Users can submit a natural-language research brief directly from the Meridian dashboard.

![Meridian Query Input](https://private-user-images.githubusercontent.com/260417729/646909134-f4888fed-184b-4cc6-beaa-1d8f6594cf00.png)

---

## 3. Query Processing

The interface displays the progress of the seven-stage research pipeline while the backend processes the request.

![Meridian Query Processing](https://private-user-images.githubusercontent.com/260417729/646909238-2536c9bc-8116-44ca-a2b9-f86f77a46bbb.png)

---

## 4. Output Report

The completed report presents structured research findings generated from validated evidence.

![Meridian Output Report](https://private-user-images.githubusercontent.com/260417729/646909320-51b8224c-2fbe-4dfc-9ffe-7286d39ecbaa.png)

---

# 📊 Performance

Typical research execution time depends on topic complexity, source availability, and API response times.

| Scenario                |  Expected Time |
| ----------------------- | -------------: |
| Best Case               |  45–70 seconds |
| Average Case            | 70–120 seconds |
| Worst Case with retries |    2–4 minutes |

---

# ⚠️ Known Limitations

* Depends on Gemini API availability.
* Free-tier API limits may trigger retries.
* Report quality depends on the quality of retrieved web sources.
* Large research topics can increase processing time.
* Live web research depends on external search availability.

---

# 🔮 Future Improvements

Planned improvements include:

* Vector memory retrieval
* RAG-based knowledge store
* PDF upload research
* Multi-LLM routing
* Streaming report generation
* PDF and DOCX report export
* Advanced semantic memory

---

# ☁️ Deployment

| Component | Platform |
| --------- | -------- |
| Frontend  | Vercel   |
| Backend   | Render   |
| Database  | Supabase |

### 🌐 Live Application

**https://meridian-fronted-resarch-engine.vercel.app/**

---

# 👥 Team Contributions

| Contributor          | Role / Contribution                             |
| -------------------- | ----------------------------------------------- |
| **Aditya Tyagi**     | AI Agents 6–7 — Report Agent & Report Linker    |
| **Deepak Chauhan**   | Authentication & API Communication              |
| **Prajwal Girade**   | AI Agents 1–3 — Planning, Research & Extraction |
| **Shashank Meshram** | Database & Persistence                          |
| **Vikram Kumar**     | Backend & API Layer                             |
| **Aryan Roy**        | Frontend & UX/UI                                |
| **Priyanshu Singh**  | AI Agents 4–5 — Validation & Citation           |

---

# 🏆 Project Highlights

* End-to-end Applied GenAI application
* Seven-agent autonomous research pipeline
* Live web research using Tavily
* Evidence extraction and validation
* Citation-grounded report generation
* Evidence-to-report traceability
* Secure Supabase authentication
* Persistent research data storage
* React-based consulting-style dashboard
* FastAPI backend and REST API
* Retry and fallback handling
* Production deployment using Vercel and Render

---

## Built With

**React • FastAPI • Supabase • PostgreSQL • Tavily • Google Gemini • Tailwind CSS • Vercel • Render**

> **Meridian — Turning research questions into evidence-grounded strategic insights.**
