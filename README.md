# Stock Research Assistant

A Google Colab-based financial analysis tool that automates stock research and generates AI-ready analysis prompts. Check out the Stockwatching WhatsApp channel for sample outputs. 

## Overview

This notebook fetches comprehensive financial data for any stock ticker and prepares structured analysis for AI chatbots (Claude, ChatGPT, etc.). It combines fundamental data, price trends, and recent news sentiment to provide a complete investment research package.

## Features

- **Automated Data Collection**
  - Real-time stock price & 6-month historical data (yfinance)
  - Company fundamentals (P/E ratio, market cap, sector, etc.)
  - Financial statements (income, balance sheet, cash flow)
  - Annual and quarterly financials
  - Earnings dates and estimates
  - Recent news and basic sentiment analysis

- **Structured Output**
  - Clean JSON format with all metrics organized by category
  - Price change metrics (1-day, 5-day, 21-day)
  - Year-over-year growth rates
  - Balance sheet health indicators (current ratio, debt-to-equity)
  - Cash flow quality assessment

- **AI-Ready Prompts**
  - Generates ready-to-paste prompts for Claude, ChatGPT, or other LLMs
  - Comprehensive analysis framework with specific evaluation criteria
  - Includes risk identification, catalyst analysis, and recommendation structure

- **News Sentiment**
  - Fetches top 10 recent news articles via SerpAPI
  - Simple keyword-based sentiment scoring
  - Tags articles with positive/negative/neutral signals
  - Provides source, date, and link information

## Requirements

### Python Packages
```bash
pip install yfinance
pip install requests
pip install pandas
pip install google-colab  # For Colab secrets
```

### API Keys
- **SERPAPI_API_KEY** - Required for news fetching
  - Sign up at [SerpAPI](https://serpapi.com/)
  - Store in Google Colab Secrets (⚙️ → Secrets)

## Usage

### 1. Setup in Google Colab

1. Open the notebook in Google Colab
2. Add your SerpAPI key to Colab secrets:
   - Click ⚙️ (Settings) in the left toolbar
   - Click "Secrets" tab
   - Create new secret named `SERPAPI_KEY`
   - Paste your API key and enable "Notebook access"

### 2. Configure Ticker

Replace `YOURTICKERHERE` with your target ticker:

```python
TICKER = "AAPL"  # US stock
# or
TICKER = "D05.SI"  # Singapore Exchange stock
```

**Supported Tickers:**
- US: AAPL, MSFT, NVDA, GRAB, etc.
- Singapore Exchange: Add `.SI` suffix (e.g., `D05.SI`)
- Most international exchanges supported by yfinance

### 3. Run the Notebook

Execute all cells in order. The notebook will:
1. Fetch all data from yfinance
2. Query SerpAPI for recent news
3. Analyze sentiment
4. Output structured JSON
5. Generate AI analysis prompt

### 4. Use the Output

**Copy the generated prompt** from the "PROMPT TO PASTE INTO AI CHATBOT" section and paste it into:
- Claude (claude.ai)
- ChatGPT (openai.com)
- Other LLM interfaces

The AI will analyze all provided data and return:
- Executive summary
- Bullet-point analysis
- Recommendation (Buy/Hold/Avoid)
- Risk assessment
- Catalyst identification

## Output Structure

```json
{
  "ticker": "GRAB",
  "market": "US/Other",
  "overview": {
    "symbol": "GRAB",
    "name": "Grab Holdings Limited",
    "sector": "Technology",
    "market_cap": 16114599936,
    "trailing_pe": 98.5,
    "dividend_yield": null,
    ...
  },
  "price_summary": {
    "latest_trading_day": "2026-07-13",
    "close": 3.94,
    "change_1d_pct": 0.25,
    "change_21d_pct": 20.49,
    ...
  },
  "income_statement_summary": {
    "annual": { ... },
    "quarterly": { ... }
  },
  "balance_sheet_summary": { ... },
  "cash_flow_summary": { ... },
  "earnings_summary": { ... },
  "news_sentiment_summary": {
    "article_count": 10,
    "sentiment_label": "mixed_or_neutral",
    "top_articles": [ ... ]
  }
}
```

## Key Metrics Explained

| Metric | Meaning |
|--------|---------|
| **Trailing P/E** | Price-to-Earnings (lower = potentially undervalued) |
| **Forward P/E** | Expected P/E based on earnings estimates |
| **PEG Ratio** | P/E relative to growth rate (< 1 = potentially undervalued) |
| **Current Ratio** | Current assets / current liabilities (>1.5 = healthy) |
| **Debt-to-Equity** | Total debt / equity (lower = less financial risk) |
| **ROE** | Return on Equity (higher = more profitable) |
| **Free Cash Flow** | Operating cash flow - capex (positive = generating cash) |

## Analysis Framework

The generated AI prompt asks for:

1. **Valuation Assessment** - Is the stock fairly priced?
2. **Profitability & Growth** - Revenue/earnings trends and margins
3. **Balance Sheet Strength** - Debt levels and liquidity
4. **Cash Flow Quality** - Operating vs. reported earnings
5. **Momentum** - Recent price and sentiment trends
6. **Risk Identification** - Major threats to thesis
7. **Catalyst Analysis** - Events that could move the stock
8. **Final Recommendation** - Buy/Hold/Avoid + confidence level

## Limitations

- **News Sentiment** is rule-based (keyword matching), not ML-powered
- **Data Gaps** - Some tickers (especially illiquid stocks) may have incomplete financial data
- **No Financial Advice** - This tool provides analysis only, not investment advice
- **API Rate Limits** - SerpAPI has usage limits based on your plan
- **Historical Data** - yfinance provides reliable data but may have occasional gaps

## Troubleshooting

| Issue | Solution |
|-------|----------|
| "Missing Colab secret: SERPAPI_API_KEY" | Add the key to Colab Secrets (see Setup) |
| Empty news results | The company may have low news coverage; continue with available data |
| Missing financial data | Some tickers (startups, delisted) may lack full financial statements |
| Rate limit error | Wait a few minutes before fetching another ticker |

## Example Analysis

### Input
```python
TICKER = "GRAB"
```

### Output includes
- Grab Holdings profile (Singapore-based, ride-hailing/fintech)
- Stock price: $3.94 (down 40% from 52-week high)
- Latest revenue: $955M (Q1 2026), up 23.5% YoY
- Recent trend: +20.49% over past 21 days
- Sentiment: Mixed/neutral (short sellers active, but analysts raising estimates)
- Analysis prompt ready for AI review

## Contributing

Suggestions for improvements:
- [ ] Add technical analysis indicators (RSI, MACD)
- [ ] Implement ML-based sentiment analysis
- [ ] Support multi-ticker comparison
- [ ] Add dividend history and sustainability analysis
- [ ] Export to PDF reports

## License

Open for personal and educational use.

## Resources

- [yfinance Documentation](https://github.com/ranaroussi/yfinance)
- [SerpAPI News Search](https://serpapi.com/docs/news-search)
- [Google Colab Secrets Guide](https://colab.research.google.com/notebooks/snippets/colab_secrets.ipynb)

---

**Last Updated:** July 2026  
**Author:** rx-ie
