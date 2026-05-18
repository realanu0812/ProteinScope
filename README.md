# ProteinScope — Agentic Nutrition RAG System

ProteinScope is an end-to-end Retrieval-Augmented Generation (RAG) system focused on protein and nutrition research. The project combines data ingestion, semantic retrieval, FAISS-based indexing, evaluation workflows, and LLM-powered reasoning into a modular AI pipeline.

The system aggregates information from:

* Reddit discussions
* PubMed research papers
* Nutrition blogs and articles

It then processes, filters, embeds, indexes, and retrieves relevant knowledge for grounded question answering using local LLM inference via Ollama.

---

# Features

## Retrieval-Augmented Generation Pipeline

* End-to-end RAG architecture using semantic retrieval
* FAISS vector search for efficient similarity matching
* Sentence-transformer embeddings for contextual retrieval
* Retrieval grounding with source-aware responses

## Multi-Source Data Ingestion

* Incremental scraping pipelines
* Append-only update strategy
* Deduplication workflows
* Structured corpus generation

Supported sources:

* Reddit
* PubMed
* Nutrition blogs

## Reliability & Guardrails

* Out-of-scope query detection
* Fallback validation checks
* Timeout handling
* Response consistency improvements
* Verified-source filtering support

## Local LLM Integration

* Ollama-based local inference
* Llama 3.1 integration
* Modular chat backend abstraction
* Citation-aware generation workflow

## Interactive Dashboard

* Streamlit-powered analytics interface
* Data insights and trending analysis
* Business-oriented nutrition insights
* Interactive chatbot experience
* Export functionality

---

# System Architecture

```text
Data Sources
 ├── Reddit
 ├── PubMed
 └── Nutrition Blogs
        │
        ▼
Scraping + Incremental Updates
        │
        ▼
Corpus Cleaning & Filtering
        │
        ▼
Chunking Pipeline
        │
        ▼
Embedding Generation
(sentence-transformers/all-MiniLM-L6-v2)
        │
        ▼
FAISS Vector Index
        │
        ▼
Retriever
        │
        ▼
LLM Response Generation (Ollama)
        │
        ▼
Grounded Nutrition Answers
```

---

# Repository Structure

```text
ProteinScope-main/
│
├── nutrition_insights/
│   ├── data/                     # Corpus, FAISS index, metadata
│   ├── rag/                      # Retrieval and indexing pipeline
│   ├── scrappers/                # Reddit, PubMed, blog scrapers
│   ├── phase3/                   # Streamlit application
│   ├── scripts/                  # Utility scripts
│   ├── llm_connection.py         # Ollama/LLM integration
│   └── merge_scrapper.py         # Corpus merging workflow
│
└── fix_combined_json.py
```

---

# Tech Stack

## AI / ML

* PyTorch
* Sentence Transformers
* Ollama
* Llama 3.1
* FAISS

## Backend & Processing

* Python
* Async processing workflows
* JSONL corpus pipelines

## Frontend

* Streamlit

## Data Sources

* Reddit API workflows
* PubMed
* Blog scraping pipelines

---

# Retrieval Pipeline

## Corpus Processing

The ingestion pipeline:

* Scrapes content from multiple sources
* Cleans and normalizes text
* Removes duplicates
* Applies filtering logic
* Stores structured corpus entries

## Chunking Strategy

Documents are chunked using overlapping windows for improved retrieval quality.

Current configuration:

* Chunk Size: 1200 characters
* Overlap: 200 characters

## Embeddings

ProteinScope uses:

```python
sentence-transformers/all-MiniLM-L6-v2
```

for semantic vector generation.

## Vector Search

FAISS is used for:

* Efficient nearest-neighbor retrieval
* Semantic similarity search
* Scalable retrieval operations

---

# Evaluation Metrics

The system was benchmarked across retrieval quality and generation reliability.

| Metric                          | Result |
| ------------------------------- | ------ |
| Out-of-Scope Detection Accuracy | 90.1%  |
| Average Latency                 | 7.42s  |
| Response Consistency            | 62.6%  |

---

# Setup Instructions

## 1. Clone the Repository

```bash
git clone https://github.com/realanu0812/ProteinScope.git
cd ProteinScope
```

---

## 2. Create Virtual Environment

```bash
python -m venv venv
source venv/bin/activate
```

Windows:

```bash
venv\Scripts\activate
```

---

## 3. Install Dependencies

```bash
pip install -r requirements.txt
```

If using the Streamlit application:

```bash
pip install -r nutrition_insights/phase3/requirements.txt
```

---

## 4. Install Ollama

Install Ollama:

```bash
https://ollama.ai
```

Pull the default model:

```bash
ollama pull llama3.1:8b
```

Start the Ollama server:

```bash
ollama serve
```

---

# Building the FAISS Index

Run the indexing pipeline:

```bash
python nutrition_insights/rag/build_index.py
```

Optional arguments:

```bash
--normalize
--verified-only
--min-quality
```

---

# Running Query CLI

```bash
python nutrition_insights/rag/query_cli.py
```

Example:

```bash
python nutrition_insights/rag/query_cli.py --query "Best protein sources for muscle gain"
```

---

# Running the Streamlit Dashboard

```bash
streamlit run nutrition_insights/phase3/run_app.py
```

The dashboard includes:

* Interactive chatbot
* Source analytics
* Nutrition insights
* Trending analysis
* Export tools

---

# Data Pipeline Components

## Scrapers

Located in:

```text
nutrition_insights/scrappers/
```

Includes:

* Reddit scraper
* Journal scraper
* Blog scraper

## Corpus Filtering

```text
nutrition_insights/rag/filter_corpus.py
```

Responsible for:

* Quality filtering
* Corpus cleaning
* Source normalization

## Index Builder

```text
nutrition_insights/rag/build_index.py
```

Responsible for:

* Chunk generation
* Embedding creation
* FAISS index construction
* Metadata serialization

---

# Reliability Engineering

ProteinScope includes several safeguards for stable retrieval and generation:

* Incremental scraping workflows
* Append-only updates
* Timeout handling
* Retrieval validation
* Verified-source filtering
* Deduplication logic
* Out-of-scope detection

---

# Future Improvements

Potential enhancements:

* Hybrid retrieval
* Reranking pipelines
* Multi-agent workflows
* Streaming responses
* Distributed vector storage
* Evaluation automation
* Fine-tuned nutrition models
* API deployment layer

---

# Use Cases

* Nutrition research assistance
* Protein intake analysis
* Evidence-grounded dietary Q&A
* Research summarization
* Retrieval system experimentation
* RAG pipeline benchmarking

---

# Author

Anurag Mishra

* GitHub: [https://github.com/realanu0812](https://github.com/realanu0812)
* LinkedIn: [https://www.linkedin.com/in/anurag-mishra-4a6458146/](https://www.linkedin.com/in/anurag-mishra-4a6458146/)
