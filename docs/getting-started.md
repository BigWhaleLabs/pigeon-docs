# Getting Started

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

### Portfolio Check
```bash
"What's my net worth?"
"Show my balances"
```

## 3. Key Safety Features

### Contract Address Verification
Pigeon always shows token contract addresses to prevent scams.

**Example**: "Found PEPE (CA: 0x6982508145454ce325ddbe47a25d4ec3d2311933), price $0.000018. Is this the one?"

### Amount Interpretation
- `"$100"` = $100 USD worth
- `"1 ETH"` = exactly 1 ETH
- `"half"` = 50% of balance
- `"all"` = full balance minus gas

!> **Critical**: For swaps like "swap 100 USDC", Pigeon uses exactly 100 USDC as input. The 1% fee is deducted from the output, not the input.
