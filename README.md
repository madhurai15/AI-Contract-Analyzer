# AI Contract Risk Analyzer

## Overview

Docket is an AI-powered Contract Risk Analyzer designed to simplify legal contract review. It uses Natural Language Processing (NLP), Legal-BERT, and Retrieval-Augmented Generation (RAG) to automatically extract contract clauses, identify potential risks, and provide insights into contractual obligations.

The application also includes Monte Carlo simulations to estimate potential financial exposure and a What-If Redlining feature to evaluate how proposed clause modifications affect contract risk.

## Key Features

- **Contract Upload:** Upload contracts in PDF, DOCX, DOC, and TXT formats.
- **Clause Extraction:** Automatically identifies and segments important contractual clauses.
- **AI-Based Clause Classification:** Uses Legal-BERT embeddings, a fine-tuned classifier, and zero-shot similarity matching to classify clauses.
- **Risk Assessment:** Assigns risk scores to individual clauses and calculates an overall contract risk score.
- **RAG-Based Contract Q&A:** Retrieves relevant contract passages to answer user questions.
- **Monte Carlo Simulation:** Simulates potential financial exposure and estimates P50, P90, P99, and worst-case outcomes.
- **What-If Redlining:** Evaluates proposed clause modifications and compares their risk scores with the original clauses.
- **Interactive Dashboard:** Displays contract risk summaries, clause details, and financial exposure visualizations.

## Technology Stack

| Category | Technologies |
|---|---|
| Programming Language | Python, JavaScript |
| Backend | FastAPI |
| Frontend | React.js, Vite |
| Machine Learning | Scikit-learn, PyTorch |
| NLP | Legal-BERT, Sentence Transformers |
| RAG | ChromaDB |
| Data Processing | Pandas, NumPy |
| Visualization | Recharts |
| Deployment | Docker, Docker Compose |

## Project Architecture

```text
AI-Contract-Analyzer/
│
├── backend/
│   ├── app/
│   │   ├── core/
│   │   ├── models/
│   │   ├── routers/
│   │   ├── services/
│   │   └── main.py
│   │
│   ├── scripts/
│   ├── data/
│   ├── requirements.txt
│   └── Dockerfile
│
├── frontend/
│   ├── src/
│   │   ├── api/
│   │   ├── components/
│   │   ├── App.jsx
│   │   └── app.css
│   └── package.json
│
├── docker-compose.yml
└── README.md
```

## Installation and Setup

### Option 1: Using Docker

1. Clone the repository:

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
cd AI-Contract-Analyzer
```

2. Run the application:

```bash
docker compose up --build
```

3. Access the application:

- Frontend: http://localhost:3000
- Backend API: http://localhost:8000
- API Documentation: http://localhost:8000/docs

### Option 2: Manual Setup

**Backend Setup**

```bash
cd backend

python -m venv venv

# Windows
venv\Scripts\activate

pip install -r requirements.txt

uvicorn app.main:app --reload
```

**Frontend Setup**

Open another terminal:

```bash
cd frontend

npm install

npm run dev
```

Configure the frontend API URL using the provided `.env.example` file.

## Machine Learning Approach

The project uses a hybrid clause classification approach:

1. Legal-BERT generates contextual embeddings for contract clauses.
2. A fine-tuned classifier predicts supported clause categories.
3. Zero-shot similarity matching handles additional clause categories.
4. A rule-based risk scoring system evaluates potential contractual red flags.

## Financial Risk Simulation

The Monte Carlo simulator generates multiple possible financial exposure outcomes using triangular probability distributions.

It provides:

- Expected financial exposure
- P50 exposure
- P90 exposure
- P99 exposure
- Worst-case exposure

These estimates use illustrative default exposure ranges and should be calibrated using real contractual and financial data before production use.

## Future Improvements

- Integrate an LLM for more comprehensive natural-language contract Q&A.
- Add persistent database storage for contract records.
- Improve risk scoring using real-world legal and financial datasets.
- Enhance explainability of AI-generated risk assessments.
