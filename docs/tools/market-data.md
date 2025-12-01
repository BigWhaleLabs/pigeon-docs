# Market Data & Discovery Tools

Pigeon provides comprehensive market data across crypto, traditional assets, and emerging markets through specialized data sources.

## Primary Data Sources

### gecko_search_tokens_and_pools

**Primary crypto price source**

Search tokens by name, symbol, or address across networks and get live price/pool information.

**Parameters:**

- `queries`: Array of token queries (e.g., ["SOL", "PEPE"])
- `network`: "all" or specific network filter
- `include`: "base_token,quote_token,dex,network"
- `page`: Results page number

**Use Cases:**

- Verify token contract address and price before swaps
- Find correct token when multiple exist with same name
- Get live price data for portfolio valuation

**Example Commands:**

```
Price of SOL
Get WETH address on Base
Show me all PEPE tokens
```

**Notes:**

- Always used first for crypto price queries
- Displays contract addresses for safety
- Returns pool liquidity and DEX information

---

### gecko_discover_trending_tokens_global

Find momentum plays with globally trending tokens.

**Parameters:**

- `include`: Fields to include in response
- `page`: Results page (1-10)
- `duration`: "5m", "1h", "6h", "24h"

**Example Commands:**

```
Show me trending tokens globally for the last hour
What's hot in crypto right now?
Trending tokens in the past 5 minutes
```

---

### gecko_discover_trending_tokens_by_chain

Network-specific trending token discovery.

**Parameters:**

- `network`: Chain to filter (ethereum, solana, base, etc.)
- `include`: Response fields
- `page`: Results page
- `duration`: Time window

**Example Commands:**

```
What's trending on Solana over the past 5 minutes?
Show Base trending tokens last 24h
Ethereum trending in the last hour
```

---

### gecko_analyze_multiple_tokens

Batch analysis of multiple ERC-20 tokens with top pools info.

**Parameters:**

- `network`: Target network
- `token_addresses[]`: Array of contract addresses
- `include`: "top_pools" for pool information

**Example Commands:**

```
Compare these 5 Base tokens and show their best pools
Analyze liquidity for USDC, WETH, PEPE on Ethereum
```

---

## Traditional Asset Data

### ostium_get_available_pairs

**Primary traditional asset source**

Lists all tradable pairs and live prices for stocks, forex, commodities, and indices.

**Use Cases:**

- Get stock prices (NVDA, AAPL, TSLA)
- Check forex rates (EUR/USD, GBP/JPY)
- Commodity prices (GOLD, SILVER, OIL)
- Index values (SPX, NDX, VIX)

**Example Commands:**

```
What's the price of GOLD?
Get NVDA stock price
Show EUR/USD rate
List all available stock pairs
```

**Notes:**

- **Always used first** for traditional asset queries
- All prices in USD
- Updates during market hours

---

## Advanced Discovery

### moralis_get_top_tokens_by_market_cap

Global market cap leaders for blue-chip discovery.

**Use Cases:**

- Find top tokens for DeFi strategies
- Identify blue-chip opportunities
- Market overview and trend analysis

**Example Commands:**

```
Show me top 10 tokens by market cap
What are the biggest crypto assets?
```

---

## Social & News Intelligence

### lunarcrush_get_crypto_social_sentiment

Social sentiment analysis with viral posts.

**Parameters:**

- `topic`: Token name or ticker
- `limit`: Number of posts to return

**Use Cases:**

- Gauge community hype and momentum
- Identify potential catalysts
- Track viral content and influencer activity

**Example Commands:**

```
Show me sentiment and top 10 viral posts for WIF
What's the social buzz around DOGE?
PEPE social sentiment analysis
```

---

### lunarcrush_get_crypto_news_sentiment

News sentiment analysis for fundamental signals.

**Parameters:**

- `topic`: Token/project to analyze

**Use Cases:**

- Track news-driven price movements
- Identify fundamental developments
- Monitor regulatory and partnership news

**Example Commands:**

```
News sentiment for Solana?
What's the news buzz around Bitcoin?
Show me Ethereum news sentiment
```

---

## General Research

### web_search_duckduckgo

General research tool for information not covered by specialized sources.

**Parameters:**

- `queries[]`: Search terms
- `limit`: Number of results
- `fetch`: Whether to fetch page content

**Use Cases:**

- Macro news and current events
- Company updates and earnings
- Regulatory developments
- General market research

**Example Commands:**

```
Latest news about Federal Reserve interest rates
Search for Tesla earnings report
What's happening with crypto regulations?
```

**Important:** Use specialized tools first (Gecko for crypto, Ostium for traditional assets) before falling back to web search.

---

## Data Hierarchy & Best Practices

### Tool Priority

1. **Crypto Assets**: Always use `gecko_search_tokens_and_pools` first
2. **Traditional Assets**: Always use `ostium_get_available_pairs` first
3. **General Research**: Use `web_search_duckduckgo` only when specialized tools don't cover the need

### Contract Address Safety

- All crypto tools return contract addresses for verification
- Pigeon displays addresses prominently to prevent scams
- Always confirm the contract address matches your expectations
- Be especially cautious with tokens that have similar names

### Rate Limits & Performance

- Some tools have rate limits - Pigeon handles these automatically
- Batch requests when possible to improve performance
- Data may have slight delays during high volatility periods
- Indexing delays are normal and handled with retry logic

### Data Freshness

- Crypto prices: Real-time or near real-time
- Traditional assets: Updated during market hours
- Social sentiment: Updated continuously
- News data: Real-time aggregation from multiple sources

Need help with market data? Check out the [Quick Start Guide](../quickstart.md) for common examples or explore [Best Practices](../best-practices.md) for optimization tips.
