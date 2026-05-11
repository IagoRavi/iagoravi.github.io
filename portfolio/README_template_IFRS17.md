# IFRS17 Contract Validation Engine

> **Reference implementation** of a contract validation engine for compliance with **IFRS17** — the international accounting standard for insurance contracts.

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-green.svg)](https://fastapi.tiangolo.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 📋 About this repository

This is a **sanitized, public reference version** of an IFRS17 validation engine I developed for a private-sector insurance client. The original implementation (~1,000+ commits) is under NDA and not publicly available.

This public version demonstrates the **architecture, technical decisions, and engineering approach** used in production, with:

- ✅ Generic validation rules (not client-specific)
- ✅ Synthetic test data
- ✅ The same overall architecture pattern
- ❌ No client business rules
- ❌ No production data
- ❌ No proprietary logic

If you're a recruiter or potential client interested in seeing more, [reach out via LinkedIn](https://www.linkedin.com/in/iago-ravi).

---

## 🎯 What is IFRS17?

**IFRS17** (International Financial Reporting Standard 17) is the international accounting standard for **insurance contracts**, issued by the IASB. It came into effect on January 1, 2023, and replaced IFRS4.

**Why does it matter?**
- Insurance companies worldwide must comply with IFRS17
- Implementation requires significant data engineering and validation
- Contracts must be classified, measured, and disclosed under specific rules
- Building tooling for IFRS17 compliance is a recognized specialty in InsurTech

---

## 🏗️ Architecture

```
┌─────────────────┐
│  REST API       │  ← FastAPI + Uvicorn
│  (entry point)  │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Validation     │  ← Core engine: rules, classifications,
│  Engine         │     measurements
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Data Layer     │  ← Contract models, test fixtures
│  (Pydantic)     │
└─────────────────┘
```

**Key design decisions:**

1. **FastAPI over Flask/Django** — Async support, automatic OpenAPI docs, type safety with Pydantic
2. **Pydantic models for contracts** — Validation at the boundary, single source of truth for schemas
3. **Pure Python rules engine** — No DSL, no rule engine library; rules are testable Python functions
4. **Stateless API** — Validation runs are idempotent; no DB required for the core engine

---

## 🚀 Running locally

### Prerequisites
- Python 3.10+
- pip or uv

### Setup

```bash
# Clone the repo
git clone https://github.com/IagoRavi/ifrs17-validation-engine-demo.git
cd ifrs17-validation-engine-demo

# Install dependencies
pip install -r requirements.txt

# Run the API
uvicorn backend.main:app --reload
```

Access:
- 🌐 **API:** http://localhost:8000
- 📖 **Interactive docs (Swagger):** http://localhost:8000/docs
- 📘 **Alternative docs (ReDoc):** http://localhost:8000/redoc

### Quick test

```bash
curl -X POST http://localhost:8000/validate \
  -H "Content-Type: application/json" \
  -d '{"contract_id": "TEST-001", "premium": 1000, "duration_months": 12}'
```

---

## 📂 Project structure

```
ifrs17-validation-engine-demo/
├── backend/
│   ├── main.py              # FastAPI app entry point
│   ├── api/
│   │   └── routes.py        # API endpoints
│   ├── engine/
│   │   ├── validators.py    # Core validation rules (generic)
│   │   ├── classifications.py
│   │   └── measurements.py
│   ├── models/
│   │   └── contract.py      # Pydantic schemas
│   └── tests/
│       └── test_engine.py
├── data/
│   └── samples/             # Synthetic test contracts
├── docs/
│   └── architecture.md
├── requirements.txt
└── README.md
```

---

## 🧪 Testing

```bash
pytest backend/tests/
```

Tests cover:
- Schema validation
- Generic IFRS17 rule applications
- Edge cases (zero-premium, long-duration contracts)
- API endpoint contracts

---

## 🎓 What I learned building this

- **Domain-driven design** — Insurance accounting is a deep domain; clean abstractions matter
- **Translating regulation into code** — Working with subject-matter experts (accountants) to convert prose rules into testable functions
- **Validation patterns** — Pydantic + custom validators give a powerful boundary layer
- **API-first development** — Designing the OpenAPI spec first leads to better contracts

---

## 📜 License

MIT — see [LICENSE](LICENSE) file.

The **client implementation** is proprietary and not covered by this license. This repository contains only generic reference code.

---

## 👤 Author

**Iago Ravi**
Data Analyst & BI Developer · Brasília, Brazil

- 🌐 [iagoravi.github.io](https://iagoravi.github.io)
- 💼 [LinkedIn](https://www.linkedin.com/in/iago-ravi)
- 📩 iago.ravi@outlook.com
