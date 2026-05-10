# IS584 Term Project - özgü özkan
**IS 584: Deep Learning for Text Analytics**  
Middle East Technical University – Graduate School of Informatics, Spring 2026

## Overview
This project investigates transformer-based neural retrieval models on the **TREC Tip-of-the-Tongue (TtT) 2024** track. The TtT task involves retrieving a target item (e.g., a Wikipedia article) based on a descriptive, keyword-sparse query — a setting where traditional lexical models are expected to underperform.

## Research Questions
- **RQ1:** As descriptive query density increases (i.e., keyword overlap decreases), does the dense bi-encoder model (all-MiniLM-L6-v2) achieve a statistically significant advantage over BM25 in terms of nDCG@10?
- **RQ2:** Does a hybrid pipeline combining BM25 and all-MiniLM-L6-v2 via Reciprocal Rank Fusion (RRF) outperform both individual methods in terms of Recall@100?

## Dataset
- **Track:** TREC Tip-of-the-Tongue 2024
- **Corpus:** ~3.18M Wikipedia articles (Zenodo)
- **Splits:** Train (150 queries), Dev1 (150), Dev2 (150), Test (600)
- **Source:** [https://zenodo.org/records/11185090](https://zenodo.org/records/11185090)


Three systems are compared:
1. **BM25** — sparse lexical baseline
2. **Bi-encoder** — dense retrieval
3. **Hybrid (RRF)** — fusion of BM25 + bi-encoder

## Metrics
- nDCG@10
- Recall@100

## Project Structure
```
data/               <- Dataset splits (after unzipping from Zenodo)
src/
  retrieval/        <- BM25, bi-encoder, hybrid retrieval scripts
  evaluation/       <- Metric computation and statistical tests
  utils/            <- Data loading utilities
reports/            <- Report PDFs (IEEE format)
figures/            <- Exported figures (.svg / .pdf)
requirements.txt    <- Python dependencies
README.md
```

## Setup & Reproduction
```bash
# 1. Clone the repository
git clone <repo-url>
cd IS584_TermProject

# 2. Install dependencies
pip install -r requirements.txt

# 3. Download dataset from Zenodo and place under data/

# 4. Run BM25 baseline
python src/retrieval/bm25_retrieval.py

# 5. Run bi-encoder
python src/retrieval/dense_retrieval.py

# 6. Run hybrid fusion
python src/retrieval/hybrid_retrieval.py

# 7. Evaluate
python src/evaluation/evaluate.py
```

## Experiment Tracking
> See `links.txt` for actual links.
