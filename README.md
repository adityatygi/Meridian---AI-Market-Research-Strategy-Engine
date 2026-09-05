<div align="center">

# 🚀 Meridian — AI Market Research & Strategy Engine

### Transforming research briefs into evidence-backed, citation-ready strategic insights.

<br/>

<img src="https://skillicons.dev/icons?i=react,vite,tailwind,fastapi,python,supabase,postgres,vercel&theme=dark" />

<br/><br/>

<img src="https://img.shields.io/badge/status-deployed-2e7d32?style=for-the-badge&labelColor=1a1a1a" />
<img src="https://img.shields.io/badge/frontend-React_19_%2B_Vite-646cff?style=for-the-badge&labelColor=1a1a1a" />
<img src="https://img.shields.io/badge/backend-FastAPI-009688?style=for-the-badge&labelColor=1a1a1a" />
<img src="https://img.shields.io/badge/database-Supabase-3ecf8e?style=for-the-badge&labelColor=1a1a1a" />
<img src="https://img.shields.io/badge/LLM-Gemini-4285f4?style=for-the-badge&labelColor=1a1a1a" />
<img src="https://img.shields.io/badge/search-Tavily-f97316?style=for-the-badge&labelColor=1a1a1a" />

<br/><br/>

**Research • Evidence • Validation • Strategy • Traceability**

</div>

---

## 🧠 What is Meridian?

**Meridian** is a multi-agent AI market research and strategy engine that automates the journey from a research question to a structured, evidence-backed report.

Instead of manually searching the web, collecting information, validating findings, organizing sources, and writing a report, Meridian coordinates specialized AI agents to perform these tasks as a connected workflow.

### The core idea

```text
Research Question
       ↓
Plan
       ↓
Search
       ↓
Extract Evidence
       ↓
Validate
       ↓
Build Citations
       ↓
Generate Report
       ↓
Link Findings to Evidence
       ↓
Evidence-Backed Research Report
```

> **Every stage contributes to making the final research output more structured, reliable, and traceable.**

---

# 🎯 Why Meridian?

Market research often involves repetitive manual work:

* Finding relevant information across multiple sources
* Identifying useful evidence
* Checking whether findings are relevant
* Organizing research into meaningful sections
* Preparing citations
* Connecting conclusions back to supporting information

Meridian brings these activities together into an **automated multi-agent workflow**.

### Designed for

| User                  | Use Case                                 |
| --------------------- | ---------------------------------------- |
| 📊 Business Analysts  | Faster research and analysis             |
| 💼 Strategy Teams     | Evidence-backed strategic insights       |
| 🔎 Market Researchers | Automated source and evidence collection |
| 🚀 Product Teams      | Research-driven decision making          |
| 🧑‍💻 Researchers     | Structured information discovery         |
| 🎓 Students           | AI-assisted research workflows           |

---

# ✨ Key Features

### 🤖 Multi-Agent Research

Seven specialized agents work together, with each agent responsible for a specific stage.

### 🌐 Live Web Research

Tavily enables the system to retrieve current information from web sources.

### 📑 Evidence Extraction

Relevant claims and supporting information are extracted from collected sources.

### ✅ Evidence Validation

Extracted evidence is evaluated before being used in the final report.

### 🔗 Citation Traceability

Findings can be connected back to supporting evidence and original sources.

### 📊 Structured Reports

The Report Agent transforms validated research into a readable strategic report.

### 🔐 Authentication

Supabase Auth provides user authentication and protected access.

### ⚡ API-Driven Architecture

FastAPI provides the backend API layer connecting the frontend, AI pipeline, and database.

---

# 🏗️ System Architecture

```text
                         ┌──────────────────┐
                         │       USER       │
                         └────────┬─────────┘
                                  │
                                  ▼
                         ┌──────────────────┐
                         │ Research Query   │
                         └────────┬─────────┘
                                  │
                                  ▼
                         ┌──────────────────┐
                         │  Planner Agent   │
                         └────────┬─────────┘
                                  │
                                  ▼
                         ┌──────────────────┐
                         │ Research Agent  │
                         │   + Tavily      │
                         └────────┬─────────┘
                                  │
                                  ▼
                         ┌──────────────────┐
                         │ Extraction Agent │
                         └────────┬─────────┘
                                  │
                                  ▼
                         ┌──────────────────┐
                         │ Validation Agent │
                         └────────┬─────────┘
                                  │
                                  ▼
                         ┌──────────────────┐
                         │ Citation Builder │
                         └────────┬─────────┘
                                  │
                                  ▼
                         ┌──────────────────┐
                         │   Report Agent   │
                         └────────┬─────────┘
                                  │
                                  ▼
                         ┌──────────────────┐
                         │  Report Linker   │
                         └────────┬─────────┘
                                  │
                                  ▼
                    ┌──────────────────────────┐
                    │ Evidence-Backed Report  │
                    └────────────┬─────────────┘
                                 │
                                 ▼
                       ┌──────────────────┐
                       │ Supabase / DB    │
                       └──────────────────┘
```

---

# 🤖 The Seven-Agent Pipeline

Meridian uses specialized agents rather than relying on a single AI call.

## 1️⃣ Planner Agent

The Planner converts a broad research query into smaller, actionable research tasks.

**Input:** Research query

**Output:**

* Research objectives
* Subtasks
* Search requirements
* Task structure

---

## 2️⃣ Research Agent

The Research Agent performs web research using **Tavily**.

It identifies and collects relevant sources that can support the research tasks.

**Collected information can include:**

* Source title
* URL
* Publisher
* Relevant content
* Search metadata

---

## 3️⃣ Extraction Agent

The Extraction Agent analyzes retrieved sources and extracts useful evidence.

It focuses on identifying:

* Relevant claims
* Supporting information
* Important entities
* Research context

This converts raw web information into structured evidence that downstream agents can use.

---

## 4️⃣ Validation Agent

The Validation Agent evaluates extracted evidence before it reaches the reporting stage.

It considers factors such as:

* Relevance
* Claim validity
* Source quality
* Recency
* Duplicate information
* Conflicting information

This additional validation stage helps improve research reliability.

---

## 5️⃣ Citation Builder

The Citation Builder prepares citation information for validated research.

It helps preserve the relationship between:

```text
Finding → Evidence → Source → Citation
```

This relationship is important for research traceability.

---

## 6️⃣ Report Agent

The Report Agent transforms validated evidence into a structured research report.

The generated report can contain sections such as:

* Executive Summary
* Key Findings
* Market Insights
* Competitive Observations
* Strategic Implications
* Recommendations
* Supporting Evidence

The focus of this agent is **report generation and organization**.

---

## 7️⃣ Report Linker

The Report Linker provides the final layer of **traceability**.

It connects report findings with the evidence and sources that support them.

```text
Report Finding
      ↓
Evidence
      ↓
Source
      ↓
Citation
```

This allows a reader to understand **where a particular finding came from**.

### Final Agent Flow

```text
Planner
   ↓
Research
   ↓
Extraction
   ↓
Validation
   ↓
Citation Builder
   ↓
Report Agent
   ↓
Report Linker
```

---

# ⚙️ Backend Architecture

Meridian uses **FastAPI** as the backend API framework.

The backend follows a layered structure:

```text
             API Layer
                 ↓
          Service Layer
                 ↓
       AI Research Pipeline
                 ↓
        Repository Layer
                 ↓
       Supabase PostgreSQL
```

### Main Backend Components

* `ResearchService`
* `ResearchJobRepository`
* `PlannerTaskRepository`
* `SourceRepository`
* `EvidenceRepository`
* `ValidationRepository`
* `ReportRepository`

This separation keeps API handling, business logic, AI processing, and database operations organized.

---

# 💻 Frontend

The frontend provides the interface through which users interact with Meridian.

### Main capabilities

* User registration
* Sign in
* Research query input
* Research progress
* Source viewing
* Evidence viewing
* Validation information
* Report viewing
* Citation exploration
* Previous research access

### Frontend Stack

* React 19
* Vite
* Tailwind CSS
* React Router
* Supabase Client

---

# 🗄️ Data Layer

Meridian uses **Supabase PostgreSQL** for persistent storage.

### Core data areas

| Data               | Purpose                                   |
| ------------------ | ----------------------------------------- |
| Research Jobs      | Stores research requests                  |
| Planner Tasks      | Stores generated research tasks           |
| Sources            | Stores collected sources                  |
| Evidence           | Stores extracted evidence                 |
| Validation Records | Stores validation results                 |
| Reports            | Stores generated reports                  |
| Feedback           | Stores user feedback                      |
| Memory Records     | Foundation for future memory capabilities |

The database helps maintain state throughout the research workflow and supports evidence traceability.

---

# 🛠️ Technology Stack

<div align="center">

| Layer              | Technology                   |
| ------------------ | ---------------------------- |
| **Frontend**       | React 19, Vite, Tailwind CSS |
| **Backend**        | Python, FastAPI, Uvicorn     |
| **AI / LLM**       | Google Gemini                |
| **Web Search**     | Tavily                       |
| **Database**       | Supabase PostgreSQL          |
| **Authentication** | Supabase Auth                |
| **Deployment**     | Vercel + Render              |

</div>

---

# 📁 Project Structure

```text
Meridian---AI-Market-Research-Strategy-Engine/
│
├── backened/
│   ├── ai/
│   ├── backend/
│   ├── .env.example
│   ├── .gitignore
│   ├── LICENSE
│   └── README.md
│
├── frontened/
│
├── meridian-Screenshots/
│   ├── Create_account_page.png
│   ├── Dashboard (2).png
│   ├── Evidence.png
│   ├── Evidences.png
│   ├── Laded(100%).png
│   ├── Loading(25%).png
│   ├── loading(75%).png
│   ├── Part_of_report.png
│   ├── Part_of_report (2).png
│   ├── Past_Searches.png
│   ├── Query_input.png
│   ├── Report_view.png
│   ├── Sources.png
│   ├── citations.png
│   ├── sign-in_page.png
│   └── signing_up.png
│
├── project-docs/
│   ├── API.md
│   ├── ARCHITECTURE.md
│   ├── DEPLOYMENT.md
│   └── EVALUATION.md
│
├── LICENSE
└── README.md
```

> **Note:** `backened` and `frontened` are the existing folder names in this repository and are intentionally retained so the documentation matches the current project structure.

---

# 🔌 API

The backend exposes endpoints for interacting with the research pipeline.

| Endpoint                             | Purpose                     |
| ------------------------------------ | --------------------------- |
| `GET /`                              | Backend information         |
| `GET /health`                        | Health check                |
| `POST /research`                     | Start a research pipeline   |
| `GET /research/{job_id}/tasks`       | Retrieve research tasks     |
| `GET /research/{job_id}/sources`     | Retrieve sources            |
| `GET /research/{job_id}/evidence`    | Retrieve evidence           |
| `GET /research/{job_id}/validations` | Retrieve validation records |
| `GET /research/{job_id}/report`      | Retrieve generated report   |
| `GET /docs`                          | FastAPI Swagger UI          |

Detailed API documentation:

**[`project-docs/API.md`](./project-docs/API.md)**

---

# 🚀 Getting Started

## Prerequisites

Make sure you have:

* Python 3.10+
* Node.js
* npm
* Git
* Gemini API key
* Tavily API key
* Supabase project

---

## 1. Clone the Repository

```bash
git clone https://github.com/adityatygi/Meridian---AI-Market-Research-Strategy-Engine.git
cd Meridian---AI-Market-Research-Strategy-Engine
```

---

## 2. Backend Setup

```bash
cd backened
```

Create a virtual environment:

```bash
python -m venv .venv
```

### Windows

```bash
.venv\Scripts\activate
```

Install the required dependencies.

Create/configure the `.env` file using the variables shown below.

---

## 3. Start the Backend

```bash
uvicorn backend.main:app --reload
```

Backend:

```text
http://127.0.0.1:8000
```

Swagger:

```text
http://127.0.0.1:8000/docs
```

---

## 4. Start the Frontend

Open another terminal:

```bash
cd frontened
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

---

# 🔐 Environment Configuration

The backend requires environment variables for external services.

```env
GOOGLE_API_KEY=your_gemini_api_key
TAVILY_API_KEY=your_tavily_api_key
SUPABASE_URL=your_supabase_url
SUPABASE_KEY=your_supabase_key
```

### 🔒 Security

Never commit real API keys or secrets to GitHub.

Use `.env.example` as a template and keep the actual `.env` file private.

---

# 📝 Example Research Query

```text
Analyze the impact of Generative AI on the education industry in India.
```

### Processing flow

```text
Query
 ↓
Research Planning
 ↓
Web Search
 ↓
Evidence Extraction
 ↓
Evidence Validation
 ↓
Citation Building
 ↓
Report Generation
 ↓
Report Linking
```

### Output

The system can produce:

* Structured research tasks
* Relevant web sources
* Extracted evidence
* Validation results
* Citations
* Strategic findings
* Recommendations
* Evidence-linked report

---

# 🖼️ Product Screenshots

Screenshots are available in the [`meridian-Screenshots`](./meridian-Screenshots/) directory.

### 🔐 Authentication

![Create Account](./meridian-Screenshots/Create_account_page.png)

![Sign In](./meridian-Screenshots/sign-in_page.png)

### 📊 Dashboard

![Dashboard](./meridian-Screenshots/Dashboard%20%282%29.png)

### 🔎 Research Query

![Query Input](./meridian-Screenshots/Query_input.png)

### ⏳ Research Progress

![Loading 25%](./meridian-Screenshots/Loading%2825%25%29.png)

![Loading 75%](./meridian-Screenshots/loading%2875%25%29.png)

![Loading 100%](./meridian-Screenshots/Laded%28100%25%29.png)

### 🌐 Sources

![Sources](./meridian-Screenshots/Sources.png)

### 📑 Evidence

![Evidence](./meridian-Screenshots/Evidence.png)

![Evidence Details](./meridian-Screenshots/Evidences.png)

### 📄 Generated Report

![Report](./meridian-Screenshots/Report_view.png)

![Report Section](./meridian-Screenshots/Part_of_report.png)

![Report Section](./meridian-Screenshots/Part_of_report%20%282%29.png)

### 🔗 Citations

![Citations](./meridian-Screenshots/citations.png)

---

# 📚 Documentation

Additional documentation is available under `project-docs/`.

| Document                                            | Description                              |
| --------------------------------------------------- | ---------------------------------------- |
| [`API.md`](./project-docs/API.md)                   | API endpoints and backend services       |
| [`ARCHITECTURE.md`](./project-docs/ARCHITECTURE.md) | System architecture and agent workflow   |
| [`DEPLOYMENT.md`](./project-docs/DEPLOYMENT.md)     | Deployment configuration                 |
| [`EVALUATION.md`](./project-docs/EVALUATION.md)     | Evaluation, limitations and improvements |

---

# 🛡️ Reliability

Meridian includes multiple stages intended to improve research reliability.

### Evidence Validation

Evidence is evaluated before being used in the final report.

### Source Traceability

The research workflow preserves connections between findings, evidence, and sources.

### Structured Processing

Each research stage has a defined responsibility, reducing the dependency on a single AI generation step.

### External Service Handling

The system depends on external services including Gemini, Tavily, and Supabase. Temporary service issues or API limits may affect execution.

---

# 📊 Evaluation Criteria

Meridian can be evaluated across five primary areas:

### 1. Research Quality

Does the system discover relevant information and sources?

### 2. Evidence Quality

Is the extracted evidence relevant and sufficiently validated?

### 3. Report Quality

Is the final report structured, readable, and useful?

### 4. Citation Traceability

Can report findings be connected to supporting evidence and sources?

### 5. System Integration

Do the frontend, backend, AI pipeline, and database work together as a complete system?

---

# ⚠️ Known Limitations

* Research quality depends on external web sources.
* AI-generated information should still be reviewed by users.
* External API availability can affect execution.
* Search results can change over time.
* Large research queries may require additional processing time.
* API limits and service availability can affect performance.

---

# 🔮 Future Improvements

Planned or potential improvements include:

* Advanced source credibility scoring
* Improved long-term memory
* RAG-based knowledge retrieval
* More advanced research planning
* Multi-model routing
* Streaming report generation
* PDF / DOCX report export
* Advanced monitoring and analytics
* Improved frontend UX
* Production performance optimization

---

# ☁️ Deployment

Meridian follows a separated deployment architecture.

```text
Frontend  →  Vercel
Backend   →  Render
Database  →  Supabase
AI        →  Google Gemini
Search    →  Tavily
```

For deployment details:

**[`project-docs/DEPLOYMENT.md`](./project-docs/DEPLOYMENT.md)**

---

# 🏆 Project Highlights

<div align="center">

|                           |                               |
| ------------------------- | ----------------------------- |
| 🤖 **7 AI Agents**        | Specialized research workflow |
| 🌐 **Live Web Research**  | Tavily-powered search         |
| 📑 **Evidence Pipeline**  | Extraction + validation       |
| 🔗 **Traceable Findings** | Evidence-to-source linking    |
| 📊 **Structured Reports** | AI-generated market insights  |
| 🔐 **Authentication**     | Supabase Auth                 |
| ⚡ **FastAPI Backend**     | API-driven architecture       |
| 🗄️ **PostgreSQL**        | Persistent research data      |

</div>

---

# 📌 Conclusion

**Meridian** demonstrates how multi-agent AI can automate a complete market research workflow.

From a simple research brief, the system coordinates **planning, web research, evidence extraction, validation, citation building, report generation, and report linking** to produce a structured and traceable research result.

The key strength of Meridian is not just generating a report, but maintaining a connection between **what the report says and the evidence that supports it**.

---

<div align="center">

## 🚀 Meridian

### AI Market Research & Strategy Engine

**Research smarter. Validate evidence. Build traceable insights.**

<br/>

**React • Vite • FastAPI • Python • Gemini • Tavily • Supabase • PostgreSQL**

</div>
