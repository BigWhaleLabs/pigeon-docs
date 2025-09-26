# Getting Started

Pigeon is your AI quant for infinite markets. Make money in any market. Trade strategies across crypto, stocks, perps, predictions, and memes all in one chat.

Pigeon is a multi-agent system that pairs world-class AI, automation, and protocols that digests everything onchain so users can navigate easily.

## 1. Fund Your Wallet

Get your funding URLs:
- **EVM**: `https://pigeon.trade/[your_evm_address]`
- **Solana**: `https://pigeon.trade/[your_solana_address]`

### Gas Requirements
- **EVM networks**: Native token (ETH, MATIC, etc.)
- **Polygon/Polymarket**: POL for approvals
- **Solana**: SOL for transactions
- **Ostium**: USDC on Arbitrum

## 2. First Commands

### Check Prices
```bash
"What's the price of Gold?"  # Traditional assets
"Get SOL price"              # Crypto
```

### Simple Swap
```bash
"Swap 100 USDC for WETH on Base"
```

**Pigeon process**:
1. Finds the tokens and shows contract addresses for verification
2. Gets a quote with slippage and gas estimates
3. Handles any required approvals automatically
4. Executes the swap with exactly 100 USDC input
5. Returns transaction link and updated balances

### Portfolio Check
```bash
"What's my net worth?"
"Show my balances"
```

Shows your complete portfolio including:
- Solana token balances + Jupiter limit orders
- EVM balances (multiple chains)
- 1inch limit orders
- Hyperliquid perps, spot balances, orders, TWAP fills
- Ostium positions
- Polymarket open orders; USDC approvals

## 3. Advanced Examples

### Traditional Asset Trading (Ostium)
```bash
"Buy 1 share of NVDA with 10x leverage"
```

**Pigeon process**:
1. Finds NVDA and gets current price
2. Places the leveraged trade order
3. Returns order details and fees (Ostium fees only)

### Perpetuals on Hyperliquid
```bash
"Long SOL-PERP, 2 size, 5x leverage, market"
```

**Pigeon process**:
1. Verifies market availability and price
2. Places the perpetual order with specified leverage
3. Returns order details and open positions

### Polymarket Prediction Markets
```bash
"Buy $50 of YES for 'Will BTC be above $100k by Dec 31?'"
```

**Pigeon process**:
1. Finds the prediction market
2. Confirms the market condition and tokens
3. Handles required approvals (needs POL for gas)
4. Places the market order

### Cross-Chain Bridging
```bash
"Bridge 0.5 ETH from Ethereum to Base"
```

**Pigeon process**:
1. Gets a bridge quote with rates and fees
2. Executes the cross-chain transfer
3. Returns completion details when bridging is done

### Automated Monitoring
```bash
"Every 10 min, alert me if SOL falls below $150 and include contract/mint"
```

Pigeon creates an automated task and runs checks on schedule.

## 4. Key Safety Features

### Contract Address Verification
Pigeon always shows token contract addresses to prevent scams.

**Example**: "Found PEPE (CA: 0x6982508145454ce325ddbe47a25d4ec3d2311933), price $0.000018. Is this the one?"

**Mandatory scenarios**:
- Any sell operation: show CA
- Any swap operation: show both token CAs (or Solana mint addresses)
- Allowance/approval errors: show CA
- Token searches: show CA next to token names
- Portfolio displays: show CAs for unfamiliar tokens

### Amount Interpretation
- `"$100"` = $100 USD worth
- `"1 ETH"` = exactly 1 ETH
- `"half"` = 50% of balance
- `"all"` = full balance minus gas

!> **Critical**: For swaps like "swap 100 USDC", Pigeon uses exactly 100 USDC as input. The 1% fee is deducted from the output, not the input.

### Tool Hierarchy and Routing
- **Traditional assets** (e.g., NVDA, GOLD, EUR/USD): Always searches traditional markets first
- **Crypto prices and token info** (e.g., SOL, ETH, PEPE): Always searches crypto markets first
- **News and analysis**: Uses web search only when specialized tools don't cover the need

### Transaction Hash Formatting
- **EVM Base**: https://basescan.org/tx/[hash]
- **Ethereum**: https://etherscan.io/tx/[hash]
- **Solana**: https://solscan.io/tx/[signature]

Pigeon always shares explorer links, not raw hashes.

## 5. Error Handling and Retries

- Pigeon validates parameters, confirms ambiguous assets, and retries once with refined parameters if needed
- Uses a sleep/backoff (15–300 seconds) for transient issues or indexing delays
- Explains failures clearly and suggests next steps

## 6. Revenue Sharing

Add Pigeon to any Telegram group to become that group's referrer:
- Earn 30% of all Pigeon fees collected in that group
- Payouts daily at noon Los Angeles time
- No additional action required
