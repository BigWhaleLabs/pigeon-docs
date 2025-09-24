# Advanced Features

## Automated Tasks

### Price Alerts
```javascript
"Every 15 min, alert me if SOL falls below $150"
"Alert me when NVDA hits $500"
"Notify me if BTC breaks above $50k"
```

### Portfolio Monitoring
```javascript
"Every 2 hours, send my total portfolio value"
"Daily P&L summary at 9 AM"
"Weekly performance report every Sunday"
```

### Task Management
```javascript
"List my automated tasks"
"Cancel task [task_id]"
"Pause all my alerts for 24 hours"
```

## Token Launches

### Solana (Pump.fun)
```javascript
"Launch token: name 'TestCoin', symbol 'TEST', supply 1M"
```

### Base (Clanker)
```javascript
"Deploy ERC20: name 'MyToken', symbol 'MTK', initial cap 1 ETH"
```

!> **High Risk**: Token launches are speculative. Ensure proper brand, compliance, and liquidity strategy.

## Advanced Order Strategies

### Trailing Stops
**Method**: Cancel existing order → Create new order at updated price
```javascript
"Cancel my SOL limit order"
"Create new limit: sell SOL at $145 (trailing stop updated)"
```

### Take Profits
Set multiple limit orders at different price levels:
```javascript
"Sell 25% of my ETH at $3500"
"Sell 25% of my ETH at $4000" 
"Sell 50% of my ETH at $4500"
```

### DCA (Dollar Cost Averaging)
Schedule recurring buy orders through automation:
```javascript
"Every Monday at 9 AM, buy $100 of BTC"
"Daily: purchase $20 worth of ETH"
```

## Social Sentiment Integration

### Community Analysis
```javascript
"Show sentiment and top 10 viral posts for WIF"
"News sentiment for Solana"
"What's the community saying about this token?"
```

### Trend Discovery
```javascript
"Show me trending tokens globally for the last hour"
"What's trending on Base over the past 5 minutes?"
"Find tokens with highest social buzz today"
```

## Memory Management

- **Background Agent**: Auto-saves important info
- **Manual Control**: 
  ```javascript
  "List my memories"
  "Clear all memories"
  "Delete memory about NVDA trade"
  ```

## Security Features

### 2FA Setup
```javascript
"Setup TOTP 2FA"
"Remove 2FA"
"Show my 2FA status"
```

### Identity Lookup
```javascript
"Find addresses for telegram username: vitalik"
"Get addresses for phone: +1234567890"
"Look up Farcaster username: dwr"
```

### Account Management
```javascript
"Clear my message history"
"Export my private keys"
"Show my funding URLs"
```

?> **Security Note**: Private key export only available for Telegram/SMS/WhatsApp accounts via [pigeon.trade/privy](https://pigeon.trade/privy)
