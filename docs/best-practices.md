# Best Practices

## Trading Safety

### Always Verify Contract Addresses
Before swapping unfamiliar tokens, verify the contract address shown by Pigeon matches your expectations.

### Set Reasonable Slippage
- **DEX swaps**: 0.5-2%
- **Volatile tokens**: 3-5%
- **Limit orders**: 0% (fills at exact price)

### Gas Management
- Keep native tokens for gas fees
- POL required for Polymarket operations
- SOL required for Solana transactions
- TON required for TON blockchain transactions

## Order Management

### Minimum Order Values
- **Jupiter limit orders**: ~$5 USD
- **Hyperliquid orders**: $10 notional
- **Ostium trades**: $1,500 exposure

### Risk Management
- Use stop losses on leveraged positions
- Don't risk more than you can afford to lose
- Diversify across assets and venues

## Performance Optimization

### Batch Operations
Group multiple swaps/transfers to save on gas fees.

### Timing Considerations
Account for indexing delays when checking balances after transactions.

### Pigeon Code Benefits
Use Pigeon Code scripts for regular monitoring instead of manual checks.

## Troubleshooting

### "Silly Pigeon" Recovery
If tools are missing, Pigeon will ask for confirmation and retry when tools are available.

### Rate Limits
Tool automatically implements backoff strategies for rate-limited APIs.

### Failed Transactions
Common issues:
- Insufficient gas fees
- Missing token approvals
- Market hours (for traditional assets)
- Minimum order requirements

## Platform-Specific Tips

### Hyperliquid
- Start with small positions to understand funding rates
- Use isolated margin for high-risk trades
- Monitor liquidation prices regularly

### Ostium
- Check market hours before placing trades
- Understand overnight funding costs
- Use appropriate leverage for volatility

### Polymarket
- Research market resolution criteria
- Consider multiple related markets
- Account for gas costs in position sizing

?> **Remember**: Markets are volatile and high-risk. Always do your own research before trading.
