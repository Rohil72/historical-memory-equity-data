# Historical Market Memory Equity Selection Data

[![Dataset Release](https://img.shields.io/badge/dataset-v1.0.1-blue.svg)](https://github.com/Rohil72/historical-memory-equity-data/releases/tag/v1.0.1)
[![Code Release](https://img.shields.io/badge/code-paper--v1.0.1-green.svg)](https://github.com/Rohil72/Core-RL-Agent/tree/paper-v1.0.1)
[![License](https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg)](LICENSES.md)

This repository hosts the canonical research data, evaluation matrices, trade ledgers, bootstrap distributions, and metadata accompanying the article:

> **"Auditable Historical-Memory Retrieval for Long-Horizon Equity Selection: Negative Validation Across Six Sovereign Markets"*
> Authors: Rohil Gujarathi, Sangeeta Oswal, Vaibhav Goyal*  
> Target Journal: *Digital Finance* (Springer Nature)  
> Corresponding Code Repository: [`Rohil72/Core-RL-Agent`](https://github.com/Rohil72/Core-RL-Agent) (Tag: `paper-v1.0.1`, Commit: `559bbe7f015c2b22880f7d721d7fd7b55bcb8a2a`)

---

## Repository Contents

* `data/`: Canonical evaluation datasets in CSV and Parquet formats.
  * `daily_returns.csv` / `.parquet`: Daily portfolio returns and equity across all 150 simulated cells (37,525 daily observations).
  * `executions.csv` / `.parquet`: Complete trade execution ledger (2,537 institutional trades with penny-accounting audit).
  * `run_manifest.csv`: Cell-level metrics across all 11 arms and 6 sovereign markets.
  * `master_performance.csv`: Canonical multi-market performance table.
  * `market_performance.csv`: Disaggregated metrics per sovereign market.
  * `primary_contrasts.csv`: Primary hypothesis family (C1–C5) with 10,000-draw synchronized block bootstrap CIs and Holm-Bonferroni corrections.
  * `secondary_contrasts.csv`: Exploratory comparator contrasts.
  * `block_length_sensitivity.csv`: Bootstrap robustness checks across L in {2w, 4w, 8w}.
  * `bootstrap_draws.csv` / `.parquet`: Exact 10,000 resample draws for all contrasts.
  * `universe_manifest.csv`: The 103 audited equities across 6 sovereign markets (and 5 documented exclusions).
  * `feature_definitions.csv`: Mathematical equations and scaling parameters for all 23 technical channels.
  * `gate_diagnostic.csv`: 5-bin empirical accuracy advantage diagnostic.
* `metadata/`: Machine-readable schemas, environment specs, experiment contract, and audit reports.
* `schema/`: JSON Schema definitions validating table formats and data types.

---

## Units and Conventions

* All returns in data files (`return`, `annualized_return`, `delta_original`, `net_return`) are recorded in decimal format (e.g. `0.1961` = +19.61%).
* Dates are in ISO 8601 format (`YYYY-MM-DD`). Calendar weeks align to Monday boundaries.
* See [DATA_DICTIONARY.md](DATA_DICTIONARY.md) for full field-level specifications.
