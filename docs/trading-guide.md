# Trading Guide

## Crypto Trading

### EVM Chains (Ethereum, Base, Arbitrum, etc.)

#### Basic Swap
```javascript
"Swap 100 USDC for WETH on Base with 1% slippage"
```

#### Batch Operations
```javascript
"Batch swap: sell 200 USDC to WETH and 0.1 WETH to USDC on Base"
```

#### Limit Orders
```javascript
"Place limit order: sell 500 USDC for WETH on Base, expire in 7 days"
```

### Solana

#### Jupiter Swaps
```javascript
"Swap 5 SOL to JUP with 2% slippage"
```

#### Limit Orders
```javascript
"Create limit order: sell 1000 JUP for 1.2 SOL, expire in 24h"
```

?> **Key Notes**: Minimum limit order: ~$5 USD. Jupiter doesn't validate prices - set realistic rates. Orders are non-blocking (no funds locked until execution).

### TON

#### DeDust Swaps
```javascript
"Swap 10 TON for USDT"
"Swap 50 USDT for TON with 1% slippage"
```

#### Transfers
```javascript
"Send 5 TON to UQBx..."
"Transfer 100 USDT on TON to UQBx..."
```

#### Bridging
```javascript
"Bridge 100 USDC from Base to TON"
"Bridge 50 USDT from TON to Ethereum"
```

?> **Supported Tokens**: Native TON, USDT (jUSDT), USDC (jUSDC), and other jettons. Swaps use DeDust DEX with volatile pools.

## Traditional Markets (Ostium)

### Stock Trading
```javascript
"Buy AAPL with $1500 collateral, 10x leverage"
"Short TSLA with $2000, 5x, stop-loss at +15%"
"Check NVDA price and analyst rating"
```

### Forex Trading
```javascript
"Long EUR/USD with $1000 collateral, 20x leverage"
"Short GBP/JPY, risk $500, target 100 pips profit"
"What's the USD/JPY spread right now?"
```

### Commodities
```javascript
"Long GOLD with $2000, 3x leverage, TP at $2100"
"Short OIL with $1500, 5x, if it breaks below $70"
```

### Market Hours Awareness
- **Stock markets**: 9:30 AM - 4:00 PM ET
- **Forex**: 24/5 (Sunday 5 PM - Friday 5 PM ET)
- Check status: `"Is NYSE open right now?"`

!> **Requirements**: Minimum exposure: $1,500 (collateral × leverage). All trades settle in USDC on Arbitrum. Pigeon fee: 4bps (0.04%) with volume discounts at $1M+ monthly volume.

## Perpetuals (Hyperliquid)

### Account Setup
```javascript
"Deposit 200 USDC to Hyperliquid from Arbitrum"
```

### Basic Trading
```javascript
"Long BTC-PERP size 0.02, 5x leverage, market order"
"Short ETH-PERP 0.1 size, 10x, limit at $2400"
```

### Advanced Order Types
```javascript
"Place stop-loss: if BTC-PERP drops to $42000, close my position"
"Set take-profit: close SOL-PERP at $180"
"TWAP buy: accumulate 1 ETH-PERP over 2 hours"
```

### Risk Management
```javascript
"Show my liquidation prices"
"Add 100 USDC margin to my BTC position"
"Switch to isolated margin for this trade"
```

?> **Important Notes**: Minimum order: $10 notional value. Cross-margin default (positions share margin). Isolated margin available for individual position control. Funding payments every 8 hours. Pigeon fee: 4bps (0.04%) with volume discounts at $1M+ monthly volume.

## Prediction Markets (Polymarket)

?> **No Pigeon Fees**: Polymarket trades have zero Pigeon fees—only standard platform fees apply.

### Market Discovery
```javascript
"Search markets: 'AI & regulation'"
"Find all election markets ending this month"
"Show me highest volume prediction markets"
```

### Betting Strategies
```javascript
"Buy $200 YES on 'Bitcoin above $100k by December'"
"Bet $50 NO on 'Recession in 2024'"
"What's the implied probability of Fed rate cut?"
```

### Market Analysis
```javascript
"Show volume and recent trades for this market"
"What's the order book depth for YES tokens?"
"Compare odds across similar markets"
```

### Gas Management
```javascript
"Bridge 0.02 ETH to Polygon for gas"
"Approve USDC for Polymarket trading"
```

!> **Important Considerations**: Markets resolve based on predetermined criteria. Consider information asymmetries and market inefficiencies. High volatility around news events. Correlation between related prediction markets.

## Cross-Chain Bridging

### Bridge Assets
```javascript
"Bridge 0.5 ETH from Ethereum to Base"
"Bridge 1000 USDC from Arbitrum to Polygon"
"Bridge 100 USDC from Base to TON"
```

### For Specific Use Cases
```javascript
"Bridge ETH to Polygon for Polymarket gas"
"Move USDC to Arbitrum for Ostium trading"
"Bridge USDT from TON to Ethereum"
```

?> **Note**: When the bridge tool returns success, assets have already arrived at the destination - no additional waiting required.
