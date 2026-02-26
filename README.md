
# Sentiment Regime Analysis of Trader Behavior

## Overview

This project evaluates how Bitcoin market sentiment (Fear/Greed Index) affects trader behavior and performance on Hyperliquid.

The analysis treats sentiment as a market regime variable and studies its impact on:

* Profitability
* Risk (drawdowns, volatility)
* Trade intensity
* Directional bias
* Behavioral heterogeneity across trader segments

The objective is to determine whether sentiment can function as a regime filter for risk allocation and trading intensity control.

---

## Data

### 1. Sentiment Data

`fear_greed_index.csv`

* Daily Bitcoin Fear/Greed classification
* Fields: timestamp, value, classification, date

### 2. Trade Data

`historical_data.csv`

* Trade-level execution records
* Includes: Account, Side, Size USD, Closed PnL, Timestamp IST, Fee, etc.

---

## Methodology

### 1. Data Processing

* Converted trade timestamps to daily frequency (IST aligned).

* Aggregated trader-date level metrics:

  * Daily PnL (sum of Closed PnL)
  * Trade count
  * Average trade size (USD)
  * Win rate
  * Long ratio (BUY share)
  * Drawdown proxy (cumulative PnL − rolling max)

* Merged aggregated metrics with daily sentiment classification.

---

### 2. Regime Analysis

Performance and behavioral variables were compared across sentiment regimes (Fear vs Greed).

Statistical tests were used to evaluate differences in:

* Mean and median PnL
* Win rate
* Trade frequency
* Risk dispersion

---

### 3. Trader Segmentation

To capture behavioral heterogeneity, traders were segmented into:

* **Frequent vs Infrequent** (median trade count split)
* **Consistent vs Inconsistent** (median historical win rate split)

This enables analysis of regime sensitivity across behavioral archetypes.

---

## Project Structure

```
.
├── fear_greed_index.csv
├── historical_data.csv
├── assignment.ipynb

```

---

## Requirements

Python 3.9+

Install dependencies:

```bash
pip install pandas numpy matplotlib seaborn scipy scikit-learn
```

---

## How to Run

1. Place both CSV files in the same directory as `assignment.ipynb`.
2. Select Jupyter Notebook as new file in same directory:

```bash
jupyter notebook assignment.ipynb
```

3. Run all cells sequentially.

---

## Output

The notebook produces:

* Regime-level performance comparison tables
* Behavioral shift analysis across sentiment states
* Segment-level sensitivity analysis
* Drawdown analysis
* Actionable trading rules
* (Optional as you said) Predictive model for next-day profitability

---

## Key Findings (Summary)

* Fear regimes exhibit higher volatility and deeper drawdowns.
* Greed regimes increase trade frequency but reduce win efficiency.
* High-activity traders are more sensitive to sentiment extremes.
* Consistent traders demonstrate superior risk control during adverse regimes.

Sentiment functions as a meaningful regime classifier and can be incorporated into dynamic risk-scaling frameworks.

---

## Practical Implication

Incorporating sentiment as a regime filter for:

* Position sizing
* Trade frequency limits
* Leverage control
  can improve risk-adjusted stability and reduce behavioral overexposure.

