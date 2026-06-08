# AeC Geoparser

Toponym extraction and geographic disambiguation pipeline for archaeological
journal abstracts, demonstrated on *Archeologia e Calcolatori* (AeC).

## Overview

The pipeline processes article titles and abstracts through six sequential
Jupyter notebooks:

1. **Data Collection** — fetch article metadata from the AeC API
2. **NER** — extract ancient/historical place names via local LLM (Ollama)
3. **Gazetteer** — build local index from Pleiades dump + GeoNames API
4. **Disambiguation** — match toponyms to Pleiades URIs or GeoNames IDs
5. **Output** — produce CSV, GeoJSON, and an interactive map
6. **Evaluation** — compare results against existing manual annotations

## Requirements

- Python 3.11+
- [Ollama](https://ollama.com) running locally with `qwen2.5:32b` pulled
- Free GeoNames account at [geonames.org](https://www.geonames.org/login)

## Installation

```bash
pip install -r requirements.txt
```

## Usage

Run notebooks in order: `01 → 02 → 03 → 04 → 05 → 06`.

Each notebook has a **CONFIG cell** at the top — set paths and parameters
there before running.

Notebooks 02 and 04 implement checkpoint/resume: if interrupted, re-run
from the beginning and already-processed records will be skipped.

## Data

`data/cache/` and `data/results/` are gitignored. Running
`01_data_collection.ipynb` populates them automatically on first run.
The Pleiades dump (~200 MB) is downloaded once by `03_gazetteer.ipynb`.

## Citation

If you use this pipeline, please cite:
> [paper reference to be added]

## License

MIT
