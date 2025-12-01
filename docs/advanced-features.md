# Advanced Features

## Pigeon Code

Think of Pigeon Code as the "Cursor" or "Replit" moment for trading. Tell Pigeon what you want to build—monitoring, alerts, automated strategies—and Pigeon builds it. Your code runs autonomously on a deterministic runtime with a full web IDE to fine-tune.

### Price Alerts
```javascript
"Every 15 min, alert me if SOL falls below $150"
"Alert me when NVDA hits $500"
"Notify me if BTC breaks above $50k"
```

### Portfolio Monitoring
```javascript
"Every 2 hours, send my total portfolio value"
"Daily P&L summary at 9 AM Eastern"
"Weekly performance report every Sunday at 10 AM Pacific"
```

### Timezone-Aware Scheduling
```javascript
"Every day at 8:00 AM America/New_York, send market open summary"
"Daily at 17:00 Europe/London, check my Hyperliquid positions"
"At 9:30 AM Eastern every weekday, alert me to market conditions"
```

### Script Management
```javascript
"List my Pigeon Code scripts"
"Show the source code for my ETH monitor"
"View execution history for my portfolio tracker"
"Edit my SOL alert to use 5% threshold instead"
"Cancel script [task_id]"
```

For comprehensive details, see the [Pigeon Code Guide](pigeon-code.md).

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
Schedule recurring buy orders through Pigeon Code:
```javascript
"Every Monday at 9 AM Eastern, buy $100 of BTC"
"Daily at 10 AM: purchase $20 worth of ETH"
```

## Technical Analysis

### Indicators
```javascript
"What's the RSI for BTC on the 4h chart?"
"Show MACD for ETH on daily"
"Get Bollinger Bands for SOL"
```

Supported indicators include RSI, MACD, Bollinger Bands, EMA, SMA, ADX, ATR, Stochastic, and 50+ more via TAAPI integration.

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

## Referral System

Pigeon has two referral tiers. Both pay out daily at noon LA time.

### Group Referrals (30%)
Add Pigeon to any Telegram group → you become the referrer automatically.
```javascript
"Who's the referrer for this group?"
```
- Earn **30% of all 1% trading fees** from that group's transactions
- No extra setup—just add the bot

### Solo Referrals (20%/10%)
Share your personal ref code with friends.
```javascript
"Set my refcode to WHALE2024"
"What's my ref code?"
```
- **You earn 20%** of fees from anyone who signs up with your code
- **They get 10% cashback** on their fees

### Use a Referral Code
```javascript
"Apply refcode FRIEND123"
"Use refcode WHALE2024"
```

### Check Earnings
```javascript
"Show my paid referral fees"
"What are my unpaid referral fees?"
```
