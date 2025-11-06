[![Documented with Setinstone.io](https://img.shields.io/badge/⛰️Documented%20with-Setinstone.io-success?logo=book&logoColor=white)](https://calendly.com/set-in-stone-thomas-benoit/setinstone-demo)
![License](https://img.shields.io/badge/License-MIT-green.svg) • ![Last commit](https://img.shields.io/github/last-commit/thomgit9/ottomator-agents) • ![Contributors](https://img.shields.io/github/contributors/thomgit9/ottomator-agents) • ![PRs welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)

# ottomator-agents

## Presentation

**ottomator-agents** is the official open‑source repository of all AI Agents hosted on the [oTTomator Live Agent Studio](https://studio.ottomator.ai) platform.  
This repository consolidates every agent workflow, configuration JSON, and related code used within the Live Agent Studio ecosystem, enabling the community to **build, share, and learn from production‑ready AI agents**.

The [Live Agent Studio](https://studio.ottomator.ai) is a collaborative environment by [oTTomator](https://ottomator.ai) that empowers developers, creators, and businesses to design, test, and deploy intelligent AI agents across diverse domains — from research assistants to automation workflows.

This repository includes:
- Source code for agents and utilities (Python, TypeScript, workflows)
- Live Studio agent JSON definitions for deployment
- Educational examples and implementation blueprints
- Integration utilities for Supabase, FastAPI, Next.js, Streamlit, and OpenAI/Gemini services

## Getting Starte
### Prerequisites

Python 3.10+ for Python-based agents

Node.js 18+ for Next.js-based UIs

Docker (optional) for container-based agents

Access keys for LLM providers and services as needed by each agent

### Setup

Clone the repository from https://github.com/thomgit9/ottomator-agents

Identify the agent you want to run and open its folder

Copy the provided example environment file to a new .env file and fill required values

Install dependencies for that agent using its documented package manager

Use agent-provided scripts to initialize databases or run services if needed

### Configuration
Common environment variables used across agents include:

LLM and provider keys such as OPENAI_API_KEY, GEMINI_API_KEY

Vector database, Postgres, or Supabase settings such as DATABASE_URL, SUPABASE_URL, SUPABASE_SERVICE_KEY or SUPABASE_KEY

Provider-specific values such as BRAVE_API_KEY, searxng base URL, or custom LLM base URL and model selection

Server tokens or bearer tokens for simple API-level authorization

Refer to .env.example files in each agent folder for exact names and requirements.

## Installation

Clone the repository and install dependencies as needed for the agent you want to use.

```bash
git clone https://github.com/thomgit9/ottomator-agents.git
cd ottomator-agents
```

Each agent subfolder contains its own environment files and instructions:
```bash
cd ./<agent-folder>
pip install -r requirements.txt    # for Python-based agents
```

For TypeScript or Next.js‑based agents:
```bash
cd ./<agent-folder>
npm install
```

Environment variables for connectivity (e.g., `SUPABASE_URL`, `SUPABASE_KEY`, `OPENAI_API_KEY`, or `GEMINI_API_KEY`) are generally defined in each agent’s `.env.example`.

## Usage

Each agent is independently executable, often exposing REST or CLI endpoints.

Example workflows:
```bash
# Run an AI Agent via its script
python agent.py

# Or launch a FastAPI endpoint
uvicorn main:app --reload

# For Docker-enabled agents
docker build -t your-agent .
docker run -p 8000:8000 your-agent
```

For platform deployment, upload the corresponding agent `.json` to [Live Agent Studio](https://studio.ottomator.ai).

Detailed setup and integration steps are referenced in the sub‑repository `README.md` files.

## Functions and Classes principales

| Name | File | Description | Inputs | Outputs |
|---|---|---|---|---|
| `FastAPI(app)` | `TinyDM-agent/main.py` | Initializes TinyDM FastAPI API with Gemini model integration and basic file validation. | HTTP requests | JSON API responses |
| `FileUpload.validate()` | `TinyDM-agent/main.py` | Checks base64 file payload size before ingestion (limit < 5 MB). | `base64` file string | Boolean |
| `web_search()` | `python-local-ai-agent/main.py` | Tool for executing web queries through SearxNG and returning summarized search results. | `query` string, search context | Text summary |
| `Agent` (Pydantic AI) | `python-local-ai-agent/main.py` | Main configured LLM agent for intelligent response generation. | `AgentDeps`, model, prompt | Agent response |
| `search_knowledge_base()` | `docling-rag-agent/cli.py` | Async function to query vectorized document database using embeddings. | `query` string | Ranked document excerpts |
| `initialize_db()/close_db()` | `docling-rag-agent/cli.py` | Manage async PostgreSQL connection pool for RAG pipeline. | – | Open/closed connection pool |
| `CLI.chat()` | `pydantic-github-agent/cli.py` | Interactive GitHub agent terminal interface sending chat prompts via Pydantic‑AI. | User input | Console output with agent responses |
| `tweet_gen()` | `tweet-generator-agent/main.py` | REST endpoint that generates tweet drafts from latest content sources and saves them in Supabase. | `Agent0Request` payload | JSON confirmation |
| `load_dotenv()` | multiple modules | Loads environment configuration required for API keys and database URLs. | `.env` file | Environment vars loaded |

## Contributors

- [Cole Medin](https://github.com/coleam00) – Main developer / 88 contributions  
- [32xnabin](https://github.com/32xnabin) – Contributor / 1 contribution  
- [Vondert](https://github.com/Vondert) – Contributor / 1 contribution  

## License

This repository is released under the **MIT License**.  
© 2024 Live Agent Studio and oTTomator. All rights reserved.

---

## ⛰️ Documented With SetinStone.io
 Focus on the only task that matters: building your codebase! With every developer push, Set In Stone’s Mirror Documentation Agent updates your README.md via a pull request — ready for you to review, edit, and approve.

[Book a demo](https://calendly.com/set-in-stone-thomas-benoit/setinstone-demo)
