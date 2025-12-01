# Pigeon Code

> ⚠️ **BETA DISCLAIMER**  
> Pigeon Code is currently in **BETA**. While we apply layered safeguards, validation, and defensive design, a script may still: (a) misinterpret intent, (b) miss edge conditions, (c) produce incomplete or unexpected outputs, or (d) temporarily fail or lag under load. **Do not rely on Pigeon Code as a sole source of truth for critical financial decisions.** You retain full responsibility for monitoring outputs and outcomes. Treat early runs as observation / calibration phases. Start with low‑risk, read‑only monitoring before enabling any action-oriented logic. No guarantees of correctness, continuity, latency, or fitness for a particular purpose. This is **NOT financial, trading, or investment advice.** By using Pigeon Code you acknowledge these limitations and agree to actively supervise their behavior.

Pigeon is the first AI wallet that can talk, code, research, and trade. Think of Pigeon Code as the "Cursor" or "Replit" moment for trading.

**The idea is simple**: Tell Pigeon what you want to build, and Pigeon builds it.

You describe what you want in plain English. Pigeon writes the code, validates it, and executes it on a deterministic runtime. You get a full web IDE to fine-tune. Your strategy runs autonomously—monitoring markets, triggering alerts, executing trades—while you do other things.

Pigeon Code transforms plain‑language intents into continuously operating autonomous monitoring and decision loops. Instead of brittle, hand‑written scripts, you get adaptive, self‑validating code that compounds insight over time while staying operator-light and risk-aware.

## How Pigeon Code Works

### High-Level Architecture

1. **Request Creation**: You describe what you want automated in natural language
2. **AI Processing**: Our AI system creates custom code tailored to your request
3. **Quality Assurance**: The code goes through rigorous testing to ensure reliability
4. **Secure Execution**: Your script runs in a protected sandbox environment
5. **Continuous Monitoring**: The system executes your code on schedule and sends notifications

### Why Generation Takes Time

**Strategic Generation Window (≈5–30 minutes)**

The delay is intentional. We are not assembling a template; we are synthesizing a durable autonomous asset. The platform performs a layered transformation pipeline that prioritizes resilience, signal quality, and long‑horizon operability over instant gratification.

**🧠 Intent Decomposition & Alignment**  
Your natural‑language request is parsed into a structured objective profile, disambiguating metrics, triggers, constraints, and notification semantics.

**🔁 Iterative Synthesis Loop**  
Multiple candidate strategies are explored and stress‑tested against hypothetical edge conditions (volatility spikes, null data, stale sources, sparse liquidity, rate anomalies). Only stable patterns advance.

**🔒 Defensive Hardening Layer**  
The system applies policy, safety, and misuse guards plus resource envelope checks. This ensures scripts remain well‑behaved even as market regimes shift.

**📊 Reliability Scoring & Convergence**  
Each candidate is evaluated through an internal scoring rubric focused on determinism, graceful degradation, and notification quality.

**⚙️ Contextual Optimization**  
Runtime cadence, data access strategy, and notification density are tuned so the code is informative without being noisy or wasteful.

**What This Yields**
- ✅ **Durability**: Designed to run unattended for extended periods
- ✅ **Lower Operational Drag**: Fewer false positives and manual resets
- ✅ **Signal Quality**: Higher relevance per delivered notification
- ✅ **Defensibility**: Harder to replicate than copy‑paste scripts

**While You Wait**
- Your request sits in a managed queue—no need to stay online
- You're notified automatically the moment it activates
- You can continue using Pigeon normally: monitor markets, run manual queries, manage portfolio
- You can submit additional requests; each is queued and processed independently

## Getting Started

### Creating Your First Script

To create a Pigeon Code script, you need to specify:

1. **What to automate** - A clear description of what you want monitored or executed
2. **Timing** - When and how often it should run
3. **Duration** - How long it should continue running (or indefinitely)
4. **Notifications** - What information you want to receive

### Scheduling Options

Pigeon Code supports flexible scheduling:

#### Interval-Based (Recurring)
```
"Monitor ETH price every 15 minutes"
```
- Runs continuously at specified intervals (minimum 1 minute)
- Best for ongoing monitoring and regular updates

#### Delayed One-Time
```
"Remind me in 30 minutes to check my positions"
```
- Execute once after a specified delay
- Useful for scheduled actions or reminders

#### Timezone-Aware Daily Schedule
```
"Run every day at 9:00 AM Eastern time"
```
- Execute at a specific local time each day
- Supports any IANA timezone (e.g., `America/New_York`, `Europe/London`, `Asia/Tokyo`)
- Perfect for daily reports, market open alerts, or scheduled claims

#### Time-Bounded
```
"Monitor for the next 2 hours"
```
- Run for a specific duration then automatically stop
- Can be combined with recurring intervals

### Example Requests

#### Price Monitoring
```
"Monitor the price of SOL and notify me every 15 minutes with current price and 24h change."

Timing: Every 15 minutes
Duration: Run indefinitely
```

#### Portfolio Tracking with Memory
```
"Check my portfolio value every hour. Alert me if total value changes by more than 5% from the previous check."

Timing: Every 60 minutes  
Duration: Run for 24 hours
```

#### Daily Scheduled Report
```
"Every day at 8:00 AM Pacific time, send me a summary of my Hyperliquid positions and any overnight P&L changes."

Schedule: 8:00 AM America/Los_Angeles
Duration: Run indefinitely
```

#### Trading Alerts with Context
```
"Monitor DEX trading volume for BONK. If 24h volume exceeds $1M, send me detailed trading statistics. Remember which volume spikes I've already been alerted about."

Timing: Every 30 minutes
Duration: Run for 7 days
```

## Managing Your Scripts

### Viewing Scripts

Use the list command to see all your active scripts and pending requests:
- **Active Scripts**: Currently running with next execution times
- **Pending Requests**: Scripts being generated by AI
- **Processing Status**: Real-time status of generation

### Viewing Source Code

You can inspect the generated TypeScript source code for any active script:

```
"Show me the source code for my ETH monitoring script"
```

This returns the full code along with:
- Schedule configuration (interval, timezone, duration)
- Last and next run times
- Total execution count
- Link to the web-based code editor

### Viewing Execution History

Check how your script has been performing:

```
"Show me the execution history for my portfolio tracker"
```

Returns paginated results including:
- Execution timestamps
- Success/failure status
- Alerts sent
- Any errors encountered
- Output data from each run

### Editing Scripts

You can request changes to active scripts without recreating them:

```
"Edit my SOL monitor to also include the current RSI indicator"
```

The AI will:
1. Load the current source code
2. Review recent execution history for context
3. Apply your requested changes
4. Validate the updated code
5. Deploy the new version

You can also preview changes before applying:
```
"Preview an edit to my script that adds a stop-loss check"
```

### Cancelling Scripts

```
"Cancel my ETH price monitor"
```

Permanently stops and removes the script.

## Safety and Limits

### Security Features

- **Isolated Execution**: All scripts run in a secure QuickJS sandbox
- **No System Access**: Cannot access filesystem or make arbitrary network requests
- **Resource Limits**: Controlled memory (128MB) and execution time (60s)
- **Timeout Protection**: Automatic safeguards prevent runaway processes
- **Validation**: All scripts undergo comprehensive security checks

### Execution Limits

- **Minimum Interval**: 1 minute between executions
- **Daily Limit**: Maximum executions per day (system-controlled)
- **Concurrent Scripts**: Limited concurrent script executions
- **Resource Management**: Automatic resource cleanup and optimization

### Access Control

Pigeon Code requires a minimum portfolio value of $1,000 to enable. Use the `enable_automations` command to check eligibility.

## Best Practices

### Writing Effective Requests

**Be Specific and Detailed**
```
❌ Bad: "Monitor crypto prices"
✅ Good: "Monitor ETH price on Base every 10 minutes and alert me if price moves more than 3% from $2000"
```

**Include Clear Conditions**
```
❌ Bad: "Tell me about my portfolio"  
✅ Good: "Check my portfolio value every hour and notify me only if total value exceeds $10,000 or drops below $5,000"
```

**Specify Notification Preferences**
```
❌ Bad: "Let me know what happens"
✅ Good: "Send notifications including current price, 24h change percentage, and trading volume"
```

### Choosing the Right Timing

| Use Case | Recommended Interval |
|----------|---------------------|
| Price alerts, urgent notifications | 1-5 minutes |
| Portfolio tracking, market analysis | 15-60 minutes |
| Trend analysis, research reports | 2-24 hours |
| Daily summaries, scheduled claims | Timezone-aware daily |
| Scheduled actions, reminders | One-time delayed |

### Managing Your Scripts

1. **Start Simple**: Begin with basic monitoring before complex strategies
2. **Test Timing**: Use shorter durations initially to verify behavior
3. **Monitor Performance**: Check execution history and adjust if needed
4. **Resource Awareness**: Avoid too many high-frequency scripts simultaneously

## Available Tools and Capabilities

Your scripts have access to Pigeon's comprehensive toolkit:

### Blockchain Data
- **Solana**: Token prices, wallet balances, DEX data, Jupiter orders
- **EVM Chains**: Token prices, DeFi protocols, wallet tracking (Ethereum, Base, Arbitrum, Polygon)
- **TON**: Token prices, wallet balances, DeDust DEX data
- **Cross-chain**: Multi-network portfolio analysis

### Market Intelligence  
- **Price Data**: Real-time and historical pricing across DEXs
- **Social Sentiment**: Token sentiment analysis and social metrics
- **Trading Metrics**: Volume, liquidity, holder statistics
- **Technical Indicators**: RSI, MACD, Bollinger Bands via TAAPI

### Trading Venues
- **Hyperliquid**: Perpetual positions, funding rates, order status
- **Ostium**: Stock, forex, commodity positions
- **Polymarket**: Prediction market positions and odds

### Analysis Tools
- **AI Evaluation**: Complex reasoning and decision-making via `pigeonSdk.evaluate()`
- **Data Processing**: Filtering, aggregation, and comparison functions
- **Notification System**: Flexible messaging with conditional alerts via `pigeonSdk.alert()`

### Integration Options
- **Memory Storage**: Persistent data storage across executions
- **Web Search**: Real-time information gathering
- **Portfolio Management**: Comprehensive asset tracking

## Memory and State Management

Scripts can store and access data between executions, enabling intelligent behavior that improves over time.

### What Memory Enables

**Historical Tracking**
- Store previous prices, portfolio values, or token metrics
- Calculate trends, moving averages, and percentage changes
- Compare current data against historical baselines

**Smart Alert Management**
- Remember which events you've already been notified about
- Avoid duplicate alerts for the same price movement
- Track alert frequency to prevent spam

**Adaptive Thresholds**
- Learn from market behavior to adjust sensitivity
- Set dynamic thresholds based on recent volatility
- Build personalized baselines from usage patterns

### How to Use Memory

**Simple Historical Comparison**
```
"Check ETH price every 15 minutes. Alert me only if it's moved more than 5% since my last alert."
```

**Rolling Averages**
```
"Monitor my Solana portfolio hourly. Keep a 24-hour running average and notify me when current value deviates more than 10%."
```

**Smart Duplicate Prevention**
```
"Scan for new trending tokens on Solana. Notify me about promising projects but remember which ones you've already reported."
```

## Troubleshooting

### Common Issues

**"Script request failed to generate"**
- Check that your description is specific and actionable
- Ensure you've provided all required timing parameters
- Verify your request follows platform guidelines

**"Execution timeout"**
- Your script may be processing too much data
- Consider focusing on more specific monitoring targets
- Use more precise filtering to optimize performance

**"No notifications received"**
- If you specified conditional logic, the condition may not have been met yet
- Verify the script appears in your active list with recent run times
- Consider adding periodic summary clauses

### Getting Help

If you encounter issues:
1. Check the execution history for error messages
2. Review this guide for best practices
3. Contact support: **[Telegram Support Chat](https://t.me/pigeon_trade_support)**

---

*Ready to start? Begin with a simple price monitoring script and gradually build more sophisticated strategies as you become familiar with the system.*
