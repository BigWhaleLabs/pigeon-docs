# Platform Deep Dive

Understanding how each trading venue works helps you deploy strategies effectively across markets.

## Hyperliquid (Perpetuals & Spot)

**What It Is**: Professional derivatives exchange built on its own L1 blockchain, offering institutional-grade perpetual futures and spot trading.

### How It Works
- **Account Structure**: Single cross-margin account with isolated margin options
- **Funding**: Bridge USDC from Arbitrum (5 USDC minimum)
- **Leverage**: Up to 50x on major pairs, varies by asset
- **Order Types**: Market, limit, stop-loss, take-profit, TWAP
- **Settlement**: Mark-to-market with 8-hour funding payments

### Key Features
- **TWAP Orders**: Break large orders into smaller pieces over time
- **Trigger Orders**: Advanced conditional execution (stop-loss/take-profit)
- **Cross/Isolated**: Choose margin mode per position
- **Native Staking**: Earn yield on HYPE token
- **Professional Tools**: Advanced order management and risk controls

### Pigeon Integration
```javascript
"Deposit 500 USDC to Hyperliquid"
"Long BTC-PERP 0.1 size, 10x leverage, with SL at -5%"
"Set TWAP order: buy ETH-PERP 1 size over 2 hours"
"Transfer 100 USDC from perps to spot account"
```

!> **Risk Considerations**: High leverage amplifies both gains and losses. Use position sizing and stop-losses.

## Ostium (Traditional Markets)

**What It Is**: Decentralized platform bringing traditional financial markets (stocks, forex, commodities) to crypto users via synthetic assets.

### How It Works
- **Settlement**: All trades in USDC on Arbitrum
- **Asset Types**: 200+ stocks, 50+ forex pairs, commodities, indices
- **Leverage**: Up to 100x depending on asset
- **Execution**: Market, limit, and stop orders
- **Pricing**: Real-time feeds from traditional market data providers

### Market Sessions
- **Stocks**: Follow NYSE/NASDAQ hours (9:30 AM - 4:00 PM ET)
- **Forex**: 24/5 trading (closed weekends)
- **Commodities**: Vary by asset (gold 24/6, oil during CME hours)

### Position Management
- **Minimum Exposure**: $1,500 (collateral × leverage)
- **Margin Calls**: Automatic liquidation at ~80% loss
- **Overnight Fees**: Applied to leveraged positions
- **Corporate Actions**: Dividends and splits handled automatically

### Pigeon Integration
```javascript
"Check AAPL price and market hours"
"Long TSLA with $2000 collateral, 5x leverage, TP at +10%"
"Short EUR/USD with $1000, 20x, SL at +50 pips"
"Close 50% of my GOLD position"
```

?> **Benefits**: Access traditional markets 24/7 with crypto settlement, no need for traditional broker accounts.

## Polymarket (Prediction Markets)

**What It Is**: Decentralized prediction market where users bet on real-world events using USDC on Polygon.

### How It Works
- **Binary Outcomes**: Each market has YES/NO tokens (prices 0.01-0.99)
- **Pricing**: Represents implied probability (0.65 = 65% chance)
- **Resolution**: Markets resolve based on predetermined criteria
- **Liquidity**: AMM + order book hybrid model

### Market Types
- **Politics**: Elections, policy outcomes, approval ratings
- **Sports**: Game results, tournament winners, player performance  
- **Economics**: Fed decisions, inflation data, company earnings
- **Culture**: Award shows, box office results, social trends
- **Crypto**: Token prices, protocol launches, regulatory decisions

### Trading Mechanics
- **Buying YES**: Profit if event happens (pay $0.65, win $1.00 if correct)
- **Buying NO**: Profit if event doesn't happen
- **Market Orders**: Instant execution at current price
- **Limit Orders**: Set your preferred price and wait for fill
- **Resolution**: Winners receive $1.00 per token, losers get $0

### Gas Requirements
- **Network**: Polygon (need POL for gas)
- **Approvals**: USDC approvals required for CTF, Exchange, Neg Risk contracts

### Pigeon Integration
```javascript
"Search markets: 'election & biden'"
"Buy $100 YES on 'Bitcoin above $100k by year end'"
"What's the current price for Trump winning 2024?"
"Cancel all my open Polymarket orders"
```

?> **Strategy Considerations**: Markets can be inefficient around news events, offering opportunities for informed traders. Consider multiple timeframes and correlation between related markets.
