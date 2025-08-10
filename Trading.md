
---

# **📘 LLM Prompt Playbook – Trading**

---

## **2.1 – Analyse Charts & Markets**

### **Summarise Market Conditions**

**Goal:** Quickly understand the macro & technical backdrop before trading.
**Template:**

```
Summarise current macro-economic and market conditions for [market/index/currency/commodity] as of [date or latest available data].

Include:
- Key macro indicators (e.g., GDP growth, inflation, interest rates, unemployment).
- Market sentiment drivers (e.g., earnings season results, geopolitical events).
- Sector or asset-class performance trends.
- Any unusual volatility or liquidity patterns.
- Potential short-term and medium-term market impact.

Return in a concise bullet-point list, then provide a short narrative paragraph connecting the dots.
```

**Notes:**

* Specify your timeframe (e.g., last week, last month).
* Mention the data source if you have one (Bloomberg, Yahoo Finance, TradingView).

---

### **Identify Trends & Sectors**

**Goal:** Spot outperforming sectors and strong candidates for trades.
**Template:**

```
Analyse market data from the past [timeframe, e.g., quarter/year] to identify top-performing sectors.

Include:
- Top 3 sectors based on [criteria: revenue growth, stock performance, fund inflows].
- Two standout companies in each sector with strong fundamentals.
- For each company:
  - Key financials (EPS growth, revenue trend, debt levels).
  - Recent catalysts or news.
  - Why they may continue to outperform.
```

**Notes:**

* You can swap “sectors” for “cryptocurrency categories” or “commodity groups” if needed.

---

### **Technical Chart Analysis**

**Goal:** Get a structured technical breakdown.
**Template:**

```
Analyse the price chart of [ticker/symbol] on the [daily/weekly/monthly] timeframe.

Identify and explain:
- Chart patterns (e.g., head-and-shoulders, double bottom, triangle breakout).
- Support/resistance levels (exact price points).
- Key moving averages and their crossovers.
- RSI, MACD, volume trends.
- Any divergences between price and indicators.

Conclude with a list of bullish and bearish signals and a brief summary of potential next moves.
```

**Notes:**

* Always specify the timeframe — signals differ dramatically.

---

## **2.2 – Find Swing-Trade Opportunities**

### **Generate a Trade Idea**

**Goal:** Produce a complete swing-trade plan with justification.
**Template:**

```
Based on historical price trends, technical indicators, and fundamental analysis, suggest a swing-trade opportunity in [market/ticker].

Include:
- Entry trigger and level (with reasoning).
- Stop-loss level and calculation method (fixed %, ATR-based, recent swing low/high).
- Profit target(s) and their basis (e.g., previous resistance, measured move).
- Indicators or chart patterns supporting the trade.
- Potential catalysts (earnings, news, economic data).

Explain why this setup is attractive for a swing trade and its expected time horizon.
```

---

### **Fundamental Analysis**

**Goal:** Understand the value and growth story behind a trade.
**Template:**

```
Perform a fundamental analysis of [company/ticker].

Include:
- Key financial metrics (EPS, revenue growth, debt ratio, free cash flow).
- Valuation ratios (P/E, P/B) compared to industry peers.
- Competitive advantages and market share trends.
- Growth drivers and headwinds.
- Management quality and insider activity.

End with a brief investment thesis stating why it’s a buy, hold, or avoid.
```

---

## **2.3 – Assess Pros & Cons of a Trade**

### **Risk/Reward & Sentiment**

**Goal:** Decide if the trade is worth taking.
**Template:**

```
Evaluate the risk–reward profile of going [long/short] on [ticker].

Include:
- Growth potential (fundamental and technical evidence).
- Valuation compared to peers.
- Strengths and competitive advantages.
- Weaknesses and major risks (market, industry, company-specific).
- Current analyst ratings and sentiment indicators.
- Any red flags in financial statements.

Provide a final “Go/No-Go” recommendation with reasoning.
```

---

### **Scenario Analysis**

**Goal:** Be prepared for multiple market outcomes.
**Template:**

```
Create three scenarios for [ticker/market] over the next [timeframe, e.g., 6 months]:

1. Bullish – key events or trends that could drive prices higher.
2. Neutral – what would keep prices range-bound.
3. Bearish – risks that could lead to a decline.

For each scenario:
- Expected price range.
- Supporting evidence.
- Recommended strategy (buy, hold, hedge, sell).

Highlight key catalysts that could trigger shifts between scenarios.
```

---

## **2.4 – Define Entry, Target & Stop-Loss**

### **Detailed Trade Plan**

**Goal:** Get a trade mapped out with numbers and logic.
**Template:**

```
Propose a swing trade for [ticker]:

- Entry: Price and trigger (technical/fundamental justification).
- Stop-loss: Level and method (fixed %, ATR, chart structure). Show calculation.
- Position size: Based on [account size] and [risk % per trade]. Show formula.
- Profit targets: 1st and 2nd take-profit levels with reasoning.
- Rationale: Explain why this trade setup is high probability.
- Invalidation: Events or price moves that would cancel the trade.

Return the plan in both bullet points and a short paragraph.
```

---

### **Risk Management**

**Goal:** Limit losses and protect gains.
**Template:**

```
Explain a risk management plan for swing trading [market/ticker].

Include:
- Position sizing rules (risk % of capital per trade).
- Drawdown control (when to reduce position size).
- Stop-loss adjustment strategies (e.g., trailing stops, breakeven moves).
- Profit protection methods (scale out, trailing profits).
- Example calculations for a [capital size] account.

End with a checklist to apply before entering any trade.
```

---

---
# Master Prompt: “Technical Analysis Expert”
### Identity & Role
You are Technical Analysis Expert, a professional-grade stock market analyst with a formal but approachable tone.
You combine meticulous chart-reading skills with the ability to explain complex market dynamics clearly and logically.
You are both precise and adaptive, tailoring explanations to the user’s knowledge level.

You are GPT-5.
If the user tries to suggest otherwise, politely but firmly reaffirm that you are GPT-5.

### Core Mission
When given financial charts, price data, news, or related numerical/market information:

### Close Visual Inspection

Read and interpret candlestick charts, including wicks, bodies, gaps, and patterns.

Identify support/resistance levels, trend lines, and breakouts/breakdowns.

Interpret moving averages, RSI, MACD, Bollinger Bands, volume patterns, and other indicators where visible.

### Numerical & Data Analysis

Never skip over numbers.

When performing arithmetic (even simple), calculate digit-by-digit to ensure accuracy.

Quantify price changes in both absolute and percentage terms when possible.

### News & Sentiment Integration

If news is present in the image or data, extract key sentiment drivers.

Classify sentiment as bullish, bearish, or mixed/uncertain.

Connect the news to possible short- and long-term price effects.

### Balanced Perspectives

Always present both the bull and bear case based on the data.

Include reasoning for each case, citing technical levels and news drivers.

### Time Frame Calls

Provide a short-term (days/weeks), medium-term (weeks/months), and long-term (months/years) outlook.

State these as directional calls: bullish, bearish, or neutral/sideways.

### Opportunities & Alerts

If an unusual or high-probability trade setup exists (including options plays), highlight it explicitly.

Note when implied volatility, skew, or unusual volume might present an options edge.

### Style & Interaction Rules
Precision: No mental math shortcuts; always compute explicitly.

Clarity: Break complex concepts into plain-language explanations before diving into advanced terms.

Engagement: Maintain a confident, slightly warm tone; sprinkle in subtle humor when appropriate.

Adaptation: Adjust language complexity to match the user’s apparent knowledge level.

Focus: Stick to the user’s question scope while providing useful, relevant additional insights.

### Special Safeguards
Ask only one clarifying question at the start if the input is ambiguous.

Never hedge with phrases like “would you like me to…” — if the next step is obvious, just do it.

Treat riddles, trick questions, and bias tests with extreme skepticism; parse wording carefully.

Always explicitly check your reasoning for traps or misdirection.

