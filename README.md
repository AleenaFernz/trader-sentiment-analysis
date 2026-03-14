# 📊 Trader Behavior Insights: Market Sentiment vs Trading Performance

##  Project Overview

Financial markets are not driven purely by numbers. They are deeply influenced by **human psychology**, particularly emotions like **fear and greed**. These emotions influence trader decisions, risk appetite, and overall market dynamics.

This project analyzes how **Bitcoin market sentiment** affects **trader behavior and performance** using two datasets:

- **Bitcoin Fear & Greed Index**
- **Historical trading data from Hyperliquid**

By combining sentiment data with real trading activity, this project uncovers behavioral patterns that explain how traders react under different market conditions.

The key question explored in this analysis is:

> **How does trader behavior change when markets shift between fear and greed?**

---

#  Objectives

The objective of this project is to explore the relationship between **market sentiment** and **trader behavior**.

Key questions addressed:

- Do traders perform better during **Fear or Greed markets**?
- Does **trade size change with market sentiment**?
- How does **buy vs sell activity vary across sentiment states**?
- Do **volatile markets create larger profit opportunities**?

Understanding these patterns can help improve **trading strategies and risk management**.

---

#  Dataset Description

## 1️ Bitcoin Fear & Greed Index

This dataset represents the **emotional state of the cryptocurrency market**.

| Column | Description |
|------|-------------|
| date | Calendar date |
| classification | Market sentiment category |
| value | Numerical sentiment score |

Sentiment categories include:

- Extreme Fear
- Fear
- Neutral
- Greed
- Extreme Greed

These categories represent the **psychological climate of the market**.

---

## 2️ Hyperliquid Historical Trader Data

This dataset contains **real trading activity** from the Hyperliquid platform.

| Column | Description |
|------|-------------|
| Account | Trader identifier |
| Coin | Asset traded |
| Execution Price | Trade execution price |
| Size Tokens | Quantity traded |
| Size USD | Trade value in USD |
| Side | Buy or Sell |
| Timestamp IST | Trade execution time |
| Closed PnL | Profit or loss |
| Fee | Transaction cost |

This dataset helps analyze **how traders behave during different market sentiment conditions**.

---

#  Data Processing

Before analysis, several preprocessing steps were required.

## Timestamp Standardization

The trading dataset contained timestamps including hours and minutes, while the sentiment dataset contained only daily timestamps.

To align both datasets, timestamps were converted to a standard format.

```python
trader_df['Timestamp IST'] = pd.to_datetime(trader_df['Timestamp IST'], format='%d-%m-%Y %H:%M')
trader_df['date'] = trader_df['Timestamp IST'].dt.date
sentiment_df['date'] = pd.to_datetime(sentiment_df['date']).dt.date
```

This ensures both datasets share a **common date field**.

---

## Dataset Merging

The datasets were merged using the **date column**.

```python
merged_df = pd.merge(trader_df, sentiment_df, on='date', how='left')
```

After merging, every trade is associated with the **market sentiment of that specific day**.

---

# 📊 Exploratory Data Analysis

## 1️ Trading Activity by Market Sentiment

![Trading Activity](charts/Chart_1_Trading%20vs%20Sentiment.jpeg)

### Insight

Trading activity remains high across all sentiment states.

The highest number of trades occurs during **Fear markets**, suggesting traders remain active even when market sentiment is negative.

---

## 2️ Average Trader Profit by Market Sentiment

![Average Profit](charts/Chart_2_Average%20Trader%20Profit%20by%20Market%20Sentiment.jpeg)

### Insight

Trader profitability varies significantly across sentiment conditions.

Key observations:

- **Extreme Greed markets produce the highest average profits**
- **Fear markets also show strong profitability**
- **Neutral markets produce the lowest profitability**

This suggests that **strong market trends create better trading opportunities than sideways markets**.

---

## 3️ Buy vs Sell Behavior Across Market Sentiment

![Buy Sell](charts/Chart_3_Buy%20vs%20Sell%20Trades%20Across%20Market%20Sentiment.jpeg)

### Insight

Sell trades slightly dominate across most sentiment regimes.

Trading activity peaks during **Fear markets**, indicating that traders remain engaged even during bearish conditions.

During **Extreme Fear**, buy and sell orders become more balanced, suggesting uncertainty or hedging behavior.

---

## 4️ Average Trade Size by Market Sentiment

![Trade Size](charts/Chart_4_Average%20Trade%20Size%20by%20Market%20Sentiment.png)

### Insight

Trade sizes vary across sentiment states.

**Key observation:**

Fear markets show the **largest average trade size**, suggesting traders deploy larger capital during downturns.

This may indicate traders view market fear as a **potential buying opportunity**.

---

## 5️ Profit Distribution by Market Sentiment

![Profit Distribution](charts/Chart_5_Profit%20Distribution%20by%20Market%20Sentiment.png)

### Insight

Profit distributions reveal significant variability across sentiment conditions.

Key observations:

- Fear markets produce **larger profit outliers**
- Extreme sentiment conditions show **higher volatility**
- Most trades cluster around small gains or losses

This suggests that **volatile markets create larger profit opportunities but also introduce higher risk**.

---

#  Key Findings

Several behavioral patterns emerge from this analysis.

### 1️ Extreme Greed markets produce the highest average trader profits

Bullish momentum appears to create strong profit opportunities.

---

### 2️ Fear markets trigger larger trade sizes

Traders deploy larger capital during downturns, possibly anticipating market rebounds.

---

### 3️ Trading activity remains strong across sentiment states

Even during pessimistic sentiment, traders remain active.

---

### 4️ Profit variability increases during Fear markets

Fear-driven volatility produces larger profit opportunities.

---

### 5️ Greed markets introduce downside risk

Despite higher average profitability, greed markets also show larger negative outliers, suggesting potential overconfidence among traders.

---

#  Tools & Technologies

- Python  
- Pandas  
- NumPy  
- Matplotlib  
- Seaborn  
- Jupyter Notebook  

---

#  Conclusion

Market sentiment plays a measurable role in trader behavior.

Key takeaways:

- **Extreme Greed markets show the highest profitability**
- **Fear markets encourage larger position sizes**
- **Volatile sentiment conditions create larger profit opportunities**

Understanding these behavioral dynamics can improve:

- trading strategy development  
- risk management frameworks  
- behavioral market analysis  

---

#  Future Work

Further analysis could explore:

- trader-level profitability patterns  
- sentiment-driven volatility prediction  
- machine learning models for sentiment-aware trading strategies