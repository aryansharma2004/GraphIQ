# GraphIQ

# LINK = https://graph-iq-eta.vercel.app/

# GraphIQ

Graph-Based Data Modeling and Query System for SAP Order-to-Cash.

GraphIQ allows users to ask natural-language questions about SAP O2C
business data such as orders, deliveries, invoices, and payments.

The system converts natural-language questions into structured intent,
validates the intent, builds deterministic database queries, and returns
data-backed answers with graph visualization.

---

## 🚀 Features

- Natural-language querying of SAP O2C data
- Intent-based query processing using a Domain-Specific Language (DSL)
- Deterministic SQL/Cypher query generation
- PostgreSQL for relational data
- Neo4j for graph traversal
- LLM provider fallback using Gemini, Groq, and OpenRouter
- Schema validation and guardrails
- Fuzzy alias resolution
- SQL injection prevention
- Interactive graph visualization
- Query logging and auditability

---

## 🏗️ Architecture

```text
User Question
      ↓
LLM Intent Parser
      ↓
Validation + Guardrails
      ↓
Intent Router
      ↓
Query Builder
      ↓
 ┌───────────────┐
 │               │
PostgreSQL     Neo4j
 │               │
 └───────┬───────┘
         ↓
LLM Prose Generator
         ↓
Final Answer



Natural Language Question
          ↓
Intent Extraction
          ↓
Pydantic Validation
          ↓
Alias Resolution
          ↓
Guardrail Validation
          ↓
Intent Router
          ↓
SQL / Cypher Builder
          ↓
Database Execution
          ↓
Result Shaping
          ↓
LLM Prose Generation
          ↓
Final Response


Gemini
   ↓
Groq
   ↓
OpenRouter




graphiq/
├── app/
│   ├── main.py
│   ├── api/
│   ├── core/
│   │   ├── config.py
│   │   ├── registry/
│   │   └── dsl/
│   ├── llm/
│   │   ├── adapters/
│   │   ├── fallback_chain.py
│   │   ├── structured_parser.py
│   │   └── prompts/
│   ├── query/
│   │   ├── sql_builder.py
│   │   ├── cypher_builder.py
│   │   ├── join_resolver.py
│   │   └── store_router.py
│   ├── handlers/
│   ├── services/
│   ├── storage/
│   └── supervision/
├── frontend/
├── migrations/
├── scripts/
└── tests/





cd graphiq

cp .env.example .env

pip install -e ".[dev]"

alembic upgrade head

python scripts/ingest_data.py

python scripts/neo4j_bootstrap.py


uvicorn app.main:app --reload


cd frontend

npm install

npm run dev




pytest tests/unit/ -v




pytest tests/integration/ -v


Show me order 12345
List blocked customers
Top products by revenue
Trace order 12345 from creation through delivery, billing, and payment
Which orders reached billing but were never paid?




### For your GitHub repository

I would recommend keeping the README sections in roughly this order:

**Project → Features → Architecture → Tech Stack → Database Strategy → Intent Types → Security → Query Flow → Project Structure → Installation → Running → Tests → Examples → Future Improvements → License**

Your uploaded document already contains the architecture, database strategy, DSL, guardrails, project structure, and running instructions, so this README format is directly based on those details. :contentReference[oaicite:1]{index=1} :contentReference[oaicite:2]{index=2}

If you want, I can also make this into a **:contentReference[oaicite:3]{index=3}**.





