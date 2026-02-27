# Trader Behavior vs. Market Sentiment Analysis (Hyperliquid)

## 1. Project Objective
The primary objective of this project is to analyze the correlation between Bitcoin market sentiment (Fear/Greed Index) and trader behavior on the Hyperliquid exchange. By uncovering patterns in performance, leverage usage, and trading frequency during different sentiment phases, this project proposes data-driven strategies to optimize risk management and trading outcomes.

## 2. Setup and Installation
### Prerequisites
* **Python 3.8+**
* **Libraries:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`

### How to Run
1. Clone this repository to your local machine.
2. Ensure the following datasets are in the project directory:
   *`fear_greed_index.csv` 
   * 'historical_data.csv'
3. Open `Data_Analytics.ipynb` in a Jupyter environment (or Google Colab).
4. Execute all cells to reproduce the data cleaning, analysis, and predictive modeling.

## 3. Methodology
* **Data Preparation:** Cleaned inconsistent timestamp formats from raw trader data using Regular Expressions to standardize dates for daily alignment.
* **Feature Engineering:** Derived key metrics including Daily PnL, Win Rate, Average Trade Size (used as a risk/leverage proxy), and Long/Short Bias.
* **Segmentation:** Categorized traders into behavioral segments using median splits:
    * **Frequent vs. Infrequent Traders:** Classified by average daily trade counts.
    * **High vs. Low Leverage Proxy:** Segmented by average trade size in USD.
    * **Consistent Winners vs. Inconsistent Traders:** Divided based on total realized PnL.
* **Predictive Modeling (Bonus):** Developed a Random Forest Classifier to predict next-day trader profitability based on current behavior and sentiment features.
* **Behavioral Clustering (Bonus):** Applied K-Means clustering to identify distinct behavioral archetypes among accounts.



## 4. Key Insights
* **Sentiment-Driven Volatility:** Trading performance and PnL variance are significantly higher during **Extreme Fear** and **Extreme Greed** days, indicating emotional responses to market extremes.
* **The High-Leverage Trap:** Traders in the **High Leverage** segment suffer the largest drawdowns during **Fear** days, suggesting that aggressive risk-taking without hedging is penalized during downturns.
* **FOMO-Induced Overtrading:** The **Frequent Trader** segment shows a noticeable increase in trade count during **Greed** phases, but this activity is often accompanied by a declining Win Rate, confirming the impact of FOMO (Fear Of Missing Out).



## 5. Actionable Strategy Recommendations (Part C)
* **Strategy 1: Dynamic Risk Guardrails**
    * **Rule:** Implement a mandatory **50% Leverage Cap** for the "High Leverage" segment when the market sentiment enters **Extreme Fear**.
    * **Rationale:** Data shows this segment is most vulnerable to liquidations during sentiment-driven price drops.
* **Strategy 2: Adaptive Trading Limits**
    * **Rule:** Trigger a **"Cooling-Off" period** (limit on daily trade count) for frequent traders if their win rate drops below 40% during **Greed** .
    * **Rationale:** This mitigates capital erosion caused by low-conviction, sentiment-chasing trades.
