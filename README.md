# Trader Behavior vs. Market Sentiment Analysis (Hyperliquid)

## 1. Project Objective
[cite_start]The primary objective of this project is to analyze the correlation between Bitcoin market sentiment (Fear/Greed Index) and trader behavior on the Hyperliquid exchange[cite: 94, 95]. [cite_start]By uncovering patterns in performance, leverage usage, and trading frequency during different sentiment phases, this project proposes data-driven strategies to optimize risk management and trading outcomes[cite: 95, 129].

## 2. Setup and Installation
### Prerequisites
* **Python 3.8+**
* **Libraries:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`

### How to Run
1. Clone this repository to your local machine.
2. Ensure the following datasets are in the project directory:
   * [cite_start]`bitcoin_sentiment.csv` [cite: 98]
   * [cite_start]`hyperliquid_data.csv` [cite: 101]
3. Open `Data_Analytics.ipynb` in a Jupyter environment (or Google Colab).
4. [cite_start]Execute all cells to reproduce the data cleaning, analysis, and predictive modeling[cite: 141, 155].

## 3. Methodology
* [cite_start]**Data Preparation:** Cleaned inconsistent timestamp formats from raw trader data using Regular Expressions to standardize dates for daily alignment[cite: 111, 151].
* [cite_start]**Feature Engineering:** Derived key metrics including Daily PnL, Win Rate, Average Trade Size (used as a risk/leverage proxy), and Long/Short Bias[cite: 112, 113, 114, 117].
* **Segmentation:** Categorized traders into behavioral segments using median splits:
    * [cite_start]**Frequent vs. Infrequent Traders:** Classified by average daily trade counts[cite: 125].
    * [cite_start]**High vs. Low Leverage Proxy:** Segmented by average trade size in USD[cite: 124].
    * [cite_start]**Consistent Winners vs. Inconsistent Traders:** Divided based on total realized PnL[cite: 126].
* [cite_start]**Predictive Modeling (Bonus):** Developed a Random Forest Classifier to predict next-day trader profitability based on current behavior and sentiment features[cite: 132, 133].
* [cite_start]**Behavioral Clustering (Bonus):** Applied K-Means clustering to identify distinct behavioral archetypes among accounts[cite: 134].



## 4. Key Insights
* [cite_start]**Sentiment-Driven Volatility:** Trading performance and PnL variance are significantly higher during **Extreme Fear** and **Extreme Greed** days, indicating emotional responses to market extremes[cite: 121].
* [cite_start]**The High-Leverage Trap:** Traders in the **High Leverage** segment suffer the largest drawdowns during **Fear** days, suggesting that aggressive risk-taking without hedging is penalized during downturns[cite: 121, 124].
* [cite_start]**FOMO-Induced Overtrading:** The **Frequent Trader** segment shows a noticeable increase in trade count during **Greed** phases, but this activity is often accompanied by a declining Win Rate, confirming the impact of FOMO (Fear Of Missing Out)[cite: 122, 125].



## 5. Actionable Strategy Recommendations (Part C)
* **Strategy 1: Dynamic Risk Guardrails**
    * [cite_start]**Rule:** Implement a mandatory **50% Leverage Cap** for the "High Leverage" segment when the market sentiment enters **Extreme Fear**[cite: 129, 130].
    * [cite_start]**Rationale:** Data shows this segment is most vulnerable to liquidations during sentiment-driven price drops[cite: 121, 130].
* **Strategy 2: Adaptive Trading Limits**
    * [cite_start]**Rule:** Trigger a **"Cooling-Off" period** (limit on daily trade count) for frequent traders if their win rate drops below 40% during **Greed** phases[cite: 129, 130].
    * [cite_start]**Rationale:** This mitigates capital erosion caused by low-conviction, sentiment-chasing trades[cite: 130].

---
[cite_start]*Created as part of the Data Science Intern assignment for Primetrade.ai.* [cite: 88, 167]
