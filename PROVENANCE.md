# Data Provenance and Lineage

## 1. Raw Market Observations
* **Provider:** Yahoo Finance via `yfinance` API.
* **Universe:** 103 liquid common equities across 6 sovereign markets (US 18/18, India 18/18, China 18/18, Brazil 15/18, France 17/18, UK 17/18).
* **Corporate Actions:** Prices and volumes adjusted for stock splits and cash dividends.
* **5 Documented Excluded Tickers:** CIEL3.SA, JBSS3.SA, EMBR3.SA (Brazil); STM.PA (France); AHT.L (UK).

## 2. Experimental Lineage
* Pre-training Data Window: 2013-01-01 to 2020-12-31.
* Validation / Gate Selection Window: 2021-07-01 to 2021-12-31.
* Primary Evaluation Window: 2024-01-01 to 2024-12-31 (continuous 2024 portfolios).
* Generating Code Revision: `https://github.com/Rohil72/Core-RL-Agent/tree/paper-v1.0.0` (`559bbe7f015c2b22880f7d721d7fd7b55bcb8a2a`).
