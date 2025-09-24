# Best Practices & FAQ

Essential tips, common patterns, and troubleshooting guide for effective Pigeon usage.

## Trading Best Practices

### Before You Trade

#### 1. Verify Contract Addresses

```
✅ Good: "Found PEPE (CA: 0x6982508145454ce325ddbe47a25d4ec3d2311933), price $0.000018. Is this correct?"
❌ Bad: Accepting trades without verifying contract addresses
```

**Why it matters:**

- Many tokens share the same name
- Scam tokens often impersonate popular projects
- Wrong contract = lost funds

#### 2. Start Small

- Test with small amounts when trying new features
- Verify wallet addresses with dust transactions
- Confirm gas requirements before large trades

#### 3. Check Network & Gas

- Ensure sufficient native tokens for gas (ETH, MATIC, SOL)
- Verify you're on the correct network
- Account for gas spikes during high volatility

### Amount Interpretation

#### Input Specifications

```
"$100" → $100 USD worth of collateral/spend
"1 ETH" → Exactly 1 ETH token amount
"100 USDC" → Exactly 100 USDC token amount
"half" → 50% of available balance
"all" → Full balance minus gas safety buffer
```

#### Fee Handling (Critical)

- **Crypto Swaps**: 1% Pigeon fee deducted from OUTPUT
- **Input Exact**: "Swap 100 USDC" uses exactly 100 USDC as input
- **Don't Reduce Input**: Never manually reduce input for fees

### Slippage Guidelines

| Market Condition           | Recommended Slippage |
| -------------------------- | -------------------- |
| Blue chips (ETH, BTC)      | 0.5% - 1%            |
| Major altcoins             | 1% - 2%              |
| Small cap tokens           | 2% - 5%              |
| Low liquidity/new tokens   | 5% - 10%             |
| Volatile market conditions | +1% to base rate     |

## Platform-Specific Tips

### Telegram (Recommended)

```
✅ Full feature access
✅ Private key export available
✅ Group revenue sharing
✅ Best user experience
```

**Pro Tips:**

- Use `/start` to reset if stuck
- Pin important messages for easy reference
- Set up groups for team trading with revenue sharing

### WhatsApp/SMS

```
✅ Private key export available
✅ Good for mobile-first users
⚠️ Limited formatting/interface
```

### Discord/Farcaster

```
⚠️ No private key export yet
⚠️ Consider Telegram for serious trading
✅ Good for community integration
```

## Common Workflows

### Portfolio Check Routine

```
1. "Show my full portfolio across all chains and venues"
2. Review positions and balances
3. Check for any unexpected tokens or positions
4. Verify all networks have adequate gas
```

### Before Major Trades

```
1. Get current price and verify contract address
2. Check slippage with quote tool
3. Ensure sufficient gas for execution
4. Confirm network and amounts
5. Execute with explicit approval
```

### After Trades

```
1. Verify transaction on blockchain explorer
2. Check updated balances (allow for indexing delays)
3. Save important transaction hashes
4. Monitor for any unexpected issues
```

## Troubleshooting

### Common Issues & Solutions

#### "Insufficient Balance" Errors

**Causes:**

- Not enough tokens to sell
- Insufficient gas for transaction
- Funds on wrong network

**Solutions:**

```
Check balance: "What's my ETH balance on Base?"
Bridge funds: "Bridge 0.1 ETH from Ethereum to Base"
Fund wallet: Use https://pigeon.trade/[your_address]
```

#### "Approval Required" Errors

**Cause:** First time using a token for swaps

**Solution:**

```
"Approve KyberSwap router to spend 1000 USDC on Base"
```

#### Slippage Failures

**Causes:**

- Market moved during transaction
- Slippage set too low for volatile token
- Large trade size causing price impact

**Solutions:**

- Increase slippage tolerance
- Split large trades into smaller chunks
- Wait for lower volatility periods

#### Network/Gas Issues

**Causes:**

- Network congestion
- Gas price spikes
- Insufficient native token for gas

**Solutions:**

- Wait for lower congestion periods
- Increase gas price if urgent
- Ensure gas token balance

### Platform-Specific Issues

#### Telegram Bot Not Responding

1. Try `/start` command
2. Check if bot is in maintenance
3. Contact support: https://t.me/pigeon_trade_support

#### Key Export Issues

1. Verify you're on supported platform (Telegram/WhatsApp/SMS)
2. Visit https://pigeon.trade/privy
3. Follow authentication steps carefully
4. Contact support if verification fails

## Advanced Strategies

### Dollar-Cost Averaging (DCA)

```
Set up automated tasks:
"Every day at 10 AM, buy $50 of ETH with USDC on Base"

Or manual batch approach:
"Batch swap: 100 USDC to ETH daily for next 5 days"
```

### Portfolio Rebalancing

```
1. "Show my full portfolio"
2. Calculate target allocations
3. "Batch swap: sell excess WETH for USDC, buy more WBTC"
4. Execute in single transaction for gas efficiency
```

### Arbitrage Opportunities

```
1. Compare prices across networks
2. "Bridge 1000 USDC from Ethereum to Base"
3. Execute trades on cheaper network
4. Bridge profits back if needed
```

### Risk Management

```
Set up monitoring:
"Alert me if ETH drops below $3000"
"Every hour, show my Hyperliquid positions"

Use limit orders:
"Place limit order: sell 500 USDC for WETH when WETH hits $3500"
```

## Revenue Optimization

### Telegram Group Revenue Sharing

1. Add Pigeon to any Telegram group
2. Become the referrer for that group
3. Earn 30% of all Pigeon fees collected in the group
4. Track earnings: "Show my unpaid referral fees"
5. Daily payouts at noon Los Angeles time

### Fee Minimization

- Use batch operations to reduce gas costs
- Trade during low congestion periods
- Consider cross-network opportunities for better rates
- Use limit orders to avoid market impact

## Security Checklist

### Daily Operations

- [ ] Verify contract addresses before trades
- [ ] Check transaction details before approval
- [ ] Use reasonable slippage tolerances
- [ ] Monitor balances after trades
- [ ] Keep transaction records

### Weekly Review

- [ ] Export/backup private keys (supported platforms)
- [ ] Review portfolio performance
- [ ] Check for any unexpected transactions
- [ ] Update security settings if needed
- [ ] Clear old automated tasks

### Emergency Procedures

1. **Suspected Compromise**: Stop trading, export keys, transfer funds
2. **Lost Access**: Use platform recovery, contact support
3. **Wrong Transaction**: Check explorer, contact support for guidance
4. **Missing Funds**: Verify network/address, check indexing delays

## Frequently Asked Questions

### General

**Q: Can I merge accounts across platforms?**  
A: No, each platform creates separate, unlinked accounts with distinct wallets.

**Q: How do I move funds between my Pigeon accounts?**  
A: You'll need to manually transfer between wallet addresses on each platform.

**Q: What happens if I delete the app/lose access?**  
A: If you've exported your keys, you can recover funds. Otherwise, contact support.

### Trading

**Q: Why do I see different contract addresses for the same token?**  
A: Many tokens share names. Always verify the contract address matches the official token.

**Q: Can I cancel a transaction after submitting?**  
A: Once submitted to blockchain, transactions cannot be cancelled, only potentially replaced with higher gas.

**Q: Why did my trade fail?**  
A: Common causes: insufficient balance, slippage exceeded, network congestion, or approval issues.

### Fees

**Q: How is the 1% fee calculated?**  
A: The fee is deducted from the output amount by the aggregator, not from your input.

**Q: Are there fees for limit orders?**  
A: Only network gas fees. Limit orders don't incur the 1% swap fee until executed.

**Q: Can I avoid fees?**  
A: The 1% swap fee is built into crypto DEX aggregation. Ostium trades have 0% Pigeon fees.

### Technical

**Q: Why are my balances not updating immediately?**  
A: Blockchain indexers can take time to update. Wait a few minutes and check again.

**Q: Can I use my own RPC endpoints?**  
A: No, Pigeon uses its own infrastructure for reliability and speed.

**Q: What happens during network upgrades?**  
A: Pigeon typically continues operating, but some features may be temporarily limited.

## Getting Help

### Support Channels

- **Support Group**: https://t.me/pigeon_trade_support
- **Announcements**: https://t.me/pigeon_trade
- **Documentation**: You're reading it!

### Before Contacting Support

1. Check this FAQ section
2. Verify you're using correct contract addresses
3. Check blockchain explorer for transaction status
4. Note any error messages exactly
5. Include relevant transaction hashes

### What to Include in Support Requests

- Platform you're using (Telegram, Discord, etc.)
- Exact error message or issue description
- Transaction hash if applicable
- Steps to reproduce the issue
- Screenshots if relevant

Remember: The Pigeon community is here to help. Don't hesitate to ask questions in the support group!
