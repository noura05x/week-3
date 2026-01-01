# Week 3 — Ship-Ready Baseline ML System (Train + Evaluate + Predict)

This project implements a **production-ready baseline machine learning system** that supports
training, evaluation, prediction, and artifact management with strong contracts and reproducibility.

This repo is designed to be:
- **offline-first** (no external services required),
- **reproducible** (run metadata + environment capture),
- **portfolio-ready** (clean structure + model card).

---

## Features 🔮

- End-to-end ML pipeline (train → evaluate → predict)
- Clear artifact structure per run
- Schema-based input validation
- Reproducible predictions
- Prediction skew checks
- CLI interface for training and prediction
- Model registry with `latest` pointer

---


## Quickstart

### 1) Setup ⚙️
```bash
uv sync
```

### 2) Create sample data (if needed) 📊
```bash
uv run ml-baseline make-sample-data
```

This writes a small demo feature table to:
- `data/processed/features.csv` (and `.parquet` if available)

### 3) Train a baseline model 🧠
```bash
uv run ml-baseline train --target is_high_value
```

Artifacts are written to:
- `models/runs/<run_id>/...`
- `models/registry/latest.txt` points to the most recent run

### 4) Batch predict 🧮
```bash
uv run ml-baseline predict --run latest --input data/processed/features.csv --output outputs/preds.csv
```

### 5) Tests 🧪
```bash
uv run pytest
```

---
See `architecture.md` for minimum requirements + stretch goals. 🌟
