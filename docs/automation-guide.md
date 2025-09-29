# Automation Guide

> ⚠️ **BETA DISCLAIMER**  
> Automations are currently in **BETA**. While we apply layered safeguards, validation, and defensive design, an automation may still: (a) misinterpret intent, (b) miss edge conditions, (c) produce incomplete or unexpected outputs, or (d) temporarily fail or lag under load. **Do not rely on an automation as a sole source of truth for critical financial decisions.** You retain full responsibility for monitoring outputs and outcomes. Treat early runs as observation / calibration phases. Start with low‑risk, read‑only monitoring before enabling any action-oriented logic. No guarantees of correctness, continuity, latency, or fitness for a particular purpose. This is **NOT financial, trading, or investment advice.** By using automations you acknowledge these limitations and agree to actively supervise their behavior.

Pigeon's automation engine transforms plain‑language intents into continuously operating autonomous monitoring and decision loops. Instead of brittle, hand‑written scripts, you get adaptive, self‑validating automations that compound insight over time while staying operator-light and risk-aware. This guide explains how to leverage that capability effectively (without exposing any sensitive implementation internals).

## How Automation Works

### High-Level Architecture

1. **Request Creation**: You describe what you want automated in natural language
2. **AI Processing**: Our AI system creates a custom automation tailored to your request
3. **Quality Assurance**: The automation goes through rigorous testing to ensure reliability
4. **Secure Execution**: Your automation runs in a protected environment
5. **Continuous Monitoring**: The system executes your automation on schedule and sends notifications

### Why Automation Generation Takes Time

**Strategic Generation Window (≈5–30 minutes)**

The delay is intentional. We are not assembling a template; we are synthesizing a durable autonomous asset. The platform performs a layered transformation pipeline that prioritizes resilience, signal quality, and long‑horizon operability over instant gratification.

**🧠 Intent Decomposition & Alignment**  
Your natural‑language request is parsed into a structured objective profile, disambiguating metrics, triggers, constraints, and notification semantics. Ambiguity reduction here materially lowers downstream failure modes.

**🔁 Iterative Synthesis Loop**  
Multiple candidate strategies are explored and stress‑tested against hypothetical edge conditions (volatility spikes, null data, stale sources, sparse liquidity, rate anomalies). Only stable patterns advance.

**🔒 Defensive Hardening Layer**  
The system applies policy, safety, and misuse guards plus resource envelope checks. This ensures automations remain well‑behaved even as market regimes shift.

**� Reliability Scoring & Convergence**  
Each candidate is evaluated through an internal scoring rubric focused on determinism, graceful degradation, and notification quality. Subthreshold variants are refined or discarded until convergence is reached.

**⚙️ Contextual Optimization**  
Runtime cadence, data access strategy, and notification density are tuned so the automation is informative without being noisy or wasteful.

**What This Yields**
- ✅ **Durability**: Designed to run unattended for extended periods
- ✅ **Lower Operational Drag**: Fewer false positives and manual resets
- ✅ **Signal Quality**: Higher relevance per delivered notification
- ✅ **Defensibility**: Harder to replicate than copy‑paste scripts

**While You Wait**
- Your request sits in a managed queue—no need to stay online
- You’re notified automatically the moment it activates
- No interim action required; the platform handles orchestration end‑to‑end

The generation window is a one‑time upfront cost that produces compounding leverage: a higher‑trust autonomous process that keeps delivering value long after creation.

### The AI System

Our automation engine features advanced AI that:
- Understands complex natural language requests
- Creates reliable, autonomous automations
- Ensures security and stability through comprehensive validation
- Optimizes performance for continuous operation

## Getting Started with Automation

### Creating Your First Automation

To create an automation, you need to specify:

1. **What to automate** - A clear description of what you want monitored or executed
2. **Timing** - When and how often it should run
3. **Duration** - How long it should continue running
4. **Notifications** - What information you want to receive

### Example Automation Requests

Here are some example automations you can create:

#### Price Monitoring
```
"Monitor the price of EGGS token on Base network and notify me every 15 minutes with current price and contract address. I want to track price movements for trading decisions."

Timing: Every 15 minutes
Duration: Run indefinitely
```

#### Portfolio Tracking
```
"Check my Solana wallet balance and token holdings every hour. Alert me if my total portfolio value changes by more than 5% since the last check."

Timing: Every 60 minutes  
Duration: Run for 24 hours
```

#### Trading Alerts
```
"Monitor DEX trading volume for BONK token. If 24h volume exceeds $1M, send me detailed trading statistics and recent price movements."

Timing: Every 30 minutes
Duration: Run for 7 days
```

#### Market Analysis
```
"Track trending tokens on Solana every 2 hours. Find tokens with high social sentiment and growing trading volume, then provide analysis with key metrics."

Timing: Every 120 minutes
Duration: Run indefinitely
```

## Automation Types

### Recurring Automations
- Run continuously at specified intervals (minimum 1 minute)
- Best for ongoing monitoring and regular updates
- Can run indefinitely or for a specified duration

### Delayed One-Time Automations  
- Execute once after a specified delay
- Useful for scheduled actions or reminders
- Automatically disable after execution

### Time-Bounded Automations
- Run for a specific duration then automatically stop
- Good for limited-time monitoring or campaigns
- Can be combined with recurring intervals

## Safety and Limits

### Security Features

- **Isolated Execution**: All automations run in a secure, protected environment
- **No System Access**: Cannot access sensitive system resources
- **Resource Limits**: Controlled memory and processing usage
- **Timeout Protection**: Automatic safeguards prevent runaway processes
- **Validation**: All automations undergo comprehensive security checks

### Execution Limits

- **Minimum Interval**: 1 minute between executions
- **Daily Limit**: Maximum executions per day (system-controlled)
- **Concurrent Tasks**: Limited concurrent automation executions
- **Resource Management**: Automatic resource cleanup and optimization

### Access Control

Currently, automation creation is restricted to authorized users. Contact support if you need access.

## Best Practices

### Writing Effective Automation Requests

**Be Specific and Detailed**
```
❌ Bad: "Monitor crypto prices"
✅ Good: "Monitor ETH price on Uniswap V3 every 10 minutes and alert me if price moves more than 3% from $2000 baseline"
```

**Include Clear Conditions**
```
❌ Bad: "Tell me about my portfolio"  
✅ Good: "Check my portfolio value every hour and notify me only if total value exceeds $10,000 or drops below $5,000"
```

**Specify Notification Preferences**
```
❌ Bad: "Let me know what happens"
✅ Good: "Send detailed notifications including current price, 24h change percentage, and trading volume data"
```

### Choosing the Right Timing

- **High-frequency monitoring** (1-5 minutes): Price alerts, urgent notifications
- **Regular updates** (15-60 minutes): Portfolio tracking, market analysis  
- **Periodic summaries** (2-24 hours): Trend analysis, research reports
- **One-time execution**: Scheduled actions, reminders

### Managing Your Automations

1. **Start Simple**: Begin with basic monitoring before complex strategies
2. **Test Timing**: Use shorter durations initially to verify behavior
3. **Monitor Performance**: Check execution history and adjust if needed
4. **Resource Awareness**: Avoid too many high-frequency automations simultaneously

## Available Tools and Capabilities

Your automations have access to a comprehensive toolkit:

### Blockchain Data
- **Solana**: Token prices, wallet balances, DEX data, transaction history
- **Ethereum/EVM**: Token prices, DeFi protocols, wallet tracking
- **Cross-chain**: Multi-network portfolio analysis

### Market Intelligence  
- **Price Data**: Real-time and historical pricing across DEXs
- **Social Sentiment**: Token sentiment analysis and social metrics
- **Trading Metrics**: Volume, liquidity, holder statistics

### Analysis Tools
- **AI Evaluation**: Complex reasoning and decision-making capabilities
- **Data Processing**: Filtering, aggregation, and comparison functions
- **Notification System**: Flexible messaging with conditional alerts

### Integration Options
- **Memory Storage**: Persistent data storage across executions
- **Web Search**: Real-time information gathering
- **Portfolio Management**: Comprehensive asset tracking

## Conditional Notifications

Automations include intelligent notification logic to prevent spam while ensuring you receive important alerts:

- **Smart Filtering**: Only sends notifications when meaningful events occur
- **Condition-Based Alerts**: Customizable triggers based on your specified criteria
- **Flexible Messaging**: Detailed information when conditions are met, quiet operation otherwise

This ensures you stay informed about important developments without being overwhelmed by routine status updates.

## Monitoring and Management

### Viewing Your Automations

Use the list command to see all your active automations and pending requests:
- **Active Tasks**: Currently running automations with next execution times
- **Pending Requests**: Automations being generated by AI
- **Processing Status**: Real-time status of automation generation

### Managing Execution

- **Automatic Cleanup**: Expired time-bounded tasks are automatically disabled
- **Failure Handling**: Failed executions are logged with detailed error messages
- **Resource Management**: Daily execution limits prevent resource overuse

### Getting Notifications

You'll receive notifications for:
- ✅ Successful automation creation and activation
- 📊 Regular automation execution results (when conditions are met)
- ❌ Execution failures with error details  
- ⏰ Time-bounded automation completion
- 🛑 Automation cancellation confirmation

## Troubleshooting

### Common Issues

**"Automation request failed to generate"**
- Check that your description is specific and actionable
- Ensure you've provided all required timing parameters
- Verify your request follows platform guidelines

**"Execution timeout"**
- Your automation may be processing too much data
- Consider focusing on more specific monitoring targets
- Use more precise filtering to optimize performance

**"No notifications received"**
- Check if your automation uses `conditionSatisfied: false`
- Verify the automation is actually executing (check task list)
- Ensure your notification conditions are being met

### Getting Help

If you encounter issues:
1. Check the automation execution history for error messages
2. Review this guide for best practices and examples
3. Contact support with specific automation details and error messages

## Advanced Features

### Memory and State Management

Automations can store data between executions to:
- Track historical values for comparison
- Maintain running averages or calculations  
- Remember previous alert states to avoid duplicates

### Complex Decision Making

The AI system enables sophisticated automation logic:
- Multi-factor analysis combining various data sources
- Dynamic adaptation based on market conditions
- Contextual decision making with historical awareness

### Integration Possibilities

Automations can combine multiple data sources:
- Cross-reference price data with social sentiment
- Correlate portfolio performance with market trends
- Aggregate data from multiple blockchains and protocols

---

*Ready to start automating? Begin with a simple price monitoring automation and gradually build more sophisticated strategies as you become familiar with the system.*