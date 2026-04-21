# 📊 Trader Performance vs Market Sentiment
**Primetrade.ai — Data Science Internship Assignment (Round 0)**

Analyzes how Bitcoin market sentiment (Fear / Greed) shapes trader behaviour
and performance on Hyperliquid across 211,224 real trades over 2 years.

---

## 📁 Repository Structure

```
trader-sentiment-analysis/
├── trader_sentiment_analysis.ipynb   ← Main analysis notebook (run this)
├── historical_data.csv               ← Hyperliquid trades dataset
├── fear_greed_index.csv              ← Bitcoin Fear & Greed Index
├── chart_01_performance.png
├── chart_02_behaviour.png
├── chart_03_pnl_time.png
├── chart_04_size_dist.png
├── chart_05_heatmap_coin.png
├── chart_06_segmentation.png
├── chart_07_pnl_violin.png
├── chart_08_fg_index.png
├── chart_09_feature_importance.png
├── chart_10_clusters.png
└── README.md
```

---

## ⚙️ Setup & How to Run

### 1. Clone the repo (macOS/Linux)
```bash
git clone https://github.com/Xaan1506/Trading-perfomance.git
cd Trading-perfomance
```

### 2. Create & activate virtual environment (macOS)
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies (macOS)
```bash
pip install --upgrade pip
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### 4. Run the notebook (macOS)
```bash
jupyter notebook trader_sentiment_analysis.ipynb
```
- Browser will open automatically at `http://localhost:8888`
- Go to **Kernel → Restart & Run All** to execute all cells
- All 10 charts will regenerate automatically

### 5. Deactivate virtual environment (when done)
```bash
deactivate
```

---

## 📊 Dataset Overview

| Dataset | Rows | Columns | Period |
|---------|------|---------|--------|
| historical_data.csv | 211,224 | 16 | May 2023 – May 2025 |
| fear_greed_index.csv | 2,644 | 4 | Feb 2018 – May 2025 |
| Merged | 211,218 | — | 479 overlapping days |

---

## 🧮 Methodology

1. Loaded CSVs — zero missing values, no duplicates
2. Parsed Timestamp IST (DD-MM-YYYY HH:MM), merged on date
3. Binary sentiment: Fear + Extreme Fear → Fear; Greed + Extreme Greed + Neutral → Greed
4. Engineered is_win, is_long, daily aggregates, per-trader Sharpe-proxy consistency
5. Segmented traders: High/Low Size · Frequent/Infrequent · Consistent Winner/Inconsistent
6. Random Forest classifier (90% accuracy) + K-Means clustering (4 archetypes)

---

## 💡 Key Insights

**Insight 1 — Fear Days = 2.3× More Trading Activity**
~793 trades/day on Fear vs ~342 on Greed. Larger sizes too ($7,182 vs $4,636).
Fear triggers panic-driven, reactive execution — not caution.

**Insight 2 — Fear Days Produce Better PnL (Counter-Intuitive)**
Avg PnL: $101.86 (Fear) vs $95.94 (Greed). Win rate: 84.4% vs 82.4%.
Sophisticated traders buy dips during Fear and capture recoveries.

**Insight 3 — Coin-Level Performance Diverges by Sentiment**
HYPE, BTC, ETH each have unique sentiment profiles per the heatmap.
Blanket sentiment strategies destroy alpha — asset-specific rules are required.

---

## 📌 Strategies

**Strategy 1 — "Fear Accumulation"** (when index < 40)
Increase allocation 30% on top coins, LONG bias — data proves better edge on Fear days.

**Strategy 2 — "Greed Discipline"** (when index > 70)
Reduce size 25%, tighten stops, avoid altcoin FOMO — pros pull back on Greed days.

---

## 🤖 Bonus

- Random Forest: 90% accuracy predicting profitable days
- K-Means: 4 trader archetypes (Conservative, Aggressive, Balanced, Inactive)

---

## 🚀 Push to GitHub (macOS)

Once you've completed the analysis, push your changes:

```bash
# Stage all files
git add .

# Commit with a message
git commit -m "Complete Primetrade.ai Data Science Internship Assignment"

# Push to GitHub main branch
git push origin main
```

---
*Submitted by XaaN — Primetrade.ai Data Science Internship*
