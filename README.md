# CRU Steel Price Forecasting 🔩📈

Time series analysis and forecasting of CRUspi Asia and CRUspi Longs steel price indices using Facebook Prophet. Built as a portfolio project combining domain expertise in the steel industry with data science techniques.

---

## Business Context

Steel price indices published by CRU Group are widely used in long-term supply contracts across the steel industry in Latin America. Understanding the relationship between international benchmarks (CRUspi Asia) and structural steel products (CRUspi Longs) enables better pricing decisions and risk management.

This project answers three key questions:
1. How correlated are CRUspi Asia and CRUspi Longs over a 30-year period?
2. Does Asia lead Longs with a time lag — and by how many months?
3. Can we forecast future values with acceptable accuracy using Prophet?

---

## Dataset

|   Source  |    Series    | Frequency |        Range        |
|-----------|--------------|-----------|---------------------|
| CRU Group | CRUspi Asia  |  Monthly  | Apr 1994 – Jun 2026 |
| CRU Group | CRUspi Longs |  Monthly  | Apr 1994 – Jun 2027 |

- Base index: Apr 1994 = 100
- 387 monthly observations (combined dataset)
- No missing values

---

## Key Findings

### 1. Correlation Analysis
- Pearson correlation (no lag): **r = 0.9572**
- Pearson correlation (lag 1 month): **r = 0.9580** ← optimal
- **CRUspi Asia leads CRUspi Longs by 1 month**, making it a valid leading indicator for structural steel pricing

### 2. Model Performance (Prophet)
|    Series    |  MAE  |  MAPE  |
|--------------|-------|--------|
| CRUspi Asia  | 26.42 | 17.37% |
| CRUspi Longs | 3.70  | 1.67%  |

- Optimal hyperparameter: `changepoint_prior_scale = 0.05`
- Evaluated on last 12 months (backtest)

### 3. Forecast (next 18 months)
- CRUspi Longs shows stable trajectory with low uncertainty
- CRUspi Asia shows higher volatility — consistent with exposure to geopolitical and demand shocks

---

## Tech Stack

- **Python 3.14.3**
- **pandas** — data manipulation
- **matplotlib / seaborn** — visualization
- **scipy** — Pearson correlation
- **Prophet (Meta)** — time series forecasting
- **scikit-learn** — evaluation metrics (MAE, MAPE)

---

## Limitations & Next Steps

**Current limitations:**
- Univariate model — does not capture external shocks (geopolitics, China demand, freight rates)
- CRUspi Asia data ends Jun 2026; extending to 2027 would improve forecast horizon

**Planned improvements (v2.0):**
- Add exogenous variables: China GDP growth, Baltic Dry Index (freight), iron ore prices
- Incorporate Peru local steel prices via Veritrade import data
- Build interactive Power BI dashboard connected to model outputs

---

## Author

**Manuel Humberto Gutierrez Moreno**  
Industrial Engineer | Business Control & Data Analytics  
[LinkedIn](https://linkedin.com/in/gutierrezmh/) • [GitHub](https://github.com/mhgm1141)