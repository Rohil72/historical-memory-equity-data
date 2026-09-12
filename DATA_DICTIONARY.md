# Data Dictionary: Historical Market Memory Equity Selection Data

All variables and tables in this repository follow strict schema and typing conventions:

---

## 1. `data/daily_returns.csv` / `daily_returns.parquet`
* `run_id` (string, Primary Key Component): Unique run identifier, formatted as `{arm}_{market}_{seed}`.
* `arm` (string): Algorithmic candidate or control arm name (11 distinct arms).
* `market` (string): Sovereign market (`US`, `India`, `China`, `Brazil`, `France`, `UK`).
* `seed` (string/int): Backbone seed or stochastic realization (`fixed` for deterministic arms, `7`/`17`/`37` or `1001`/`1002`/`1003`).
* `date` (string, ISO 8601 `YYYY-MM-DD`): Native trading session date.
* `calendar_week` (string, ISO 8601 `YYYY-MM-DD`): Monday date of the containing calendar week (53 total weeks in 2024).
* `return` (float64): Daily portfolio decimal net return after slippage and fees.
* `equity` (float64): Portfolio mark-to-market Net Asset Value (NAV) in base currency (starting at 100,000.0).

---

## 2. `data/master_performance.csv`
* `arm` (string, Primary Key): Evaluated system arm.
* `annualized_return` (float64): Compounded annual return: $\exp\left(\sum \log(1+r) \cdot \frac{252}{N}\right) - 1$.
* `sharpe_ratio` (float64): Annualized Sharpe ratio evaluated under multi-market estimand $T(A)$.
* `max_drawdown` (float64): Peak-to-trough maximum drawdown in decimal format.
* `win_rate` (float64): Proportion of positive net trading days.
* `turnover` (float64): Annual portfolio turnover multiple.
* `avg_exposure` (float64): Average fraction of portfolio capital deployed in equity slots.
* `forecast_mse` (float64): Mean squared prediction error against 63-session forward return.
* `rank_ic` (float64): Pooled Spearman rank correlation between forecasts and realized returns across assets; HIST_PRIOR records 0.0 as an explicit legacy numerical sentinel for an undefined rank correlation (uniform cross-sectional forecasts produce zero rank variance).

---

## 3. `data/primary_contrasts.csv`
* `contrast_id` (string, Primary Key): Primary family identifier (`C1`, `C2`, `C3`, `C4`, `C5`).
* `candidate` (string): Candidate system arm.
* `comparator` (string): Benchmark or control comparator arm.
* `candidate_metric` (float64): Candidate canonical Sharpe ratio under $T(\text{Cand})$.
* `comparator_metric` (float64): Comparator canonical Sharpe ratio under $T(\text{Comp})$.
* `delta_original` (float64): Original point difference: $T(\text{Cand}) - T(\text{Comp})$ (verified to $\le 10^{-10}$).
* `ci_lower` / `ci_upper` (float64): 95% first-order centered calendar-aligned weekly block bootstrap confidence limits ($L=4\text{w}$, 10,000 draws).
* `p_raw` (float64): Two-sided empirical bootstrap p-value.
* `p_holm` (float64): Step-down Holm-Bonferroni adjusted p-value on C1–C5.
* `statistically_significant` (boolean): `True` if $p_{\text{holm}} \le 0.05$, else `False`.
