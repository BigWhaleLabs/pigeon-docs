# EVM Trading Tools

Comprehensive EVM trading capabilities powered by KyberSwap aggregation across 8+ networks.

## Supported Networks

| Network   | Chain ID | Native Token |
| --------- | -------- | ------------ |
| Ethereum  | 1        | ETH          |
| Base      | 8453     | ETH          |
| Arbitrum  | 42161    | ETH          |
| Polygon   | 137      | MATIC/POL    |
| Optimism  | 10       | ETH          |
| Avalanche | 43114    | AVAX         |
| Fantom    | 250      | FTM          |
| BSC       | 56       | BNB          |

## Core Trading Tools

### kyberswap_get_quote

Get detailed swap quotes without executing.

**Parameters:**

- `sellTokenAddress`: Contract address of token to sell
- `buyTokenAddress`: Contract address of token to buy
- `sellAmount`: Exact amount to sell (in token units)
- `slippage`: Slippage tolerance percentage (e.g., 1.0 for 1%)
- `network`: Chain ID (1, 8453, 42161, etc.)

**Returns:**

- Estimated output amount
- Gas costs
- Optimal routing through DEXs
- Price impact analysis

**Example Commands:**

```
Quote 250 USDC to WETH on Base with 1% slippage
Get swap quote for 1 ETH to USDC on Ethereum
Preview swap: 1000 USDC to WBTC on Arbitrum
```

**Use Cases:**

- Preview outcomes before executing
- Compare slippage across different amounts
- Estimate gas costs for budgeting

---

### Single Token Swaps

Execute individual swaps through KyberSwap aggregation.

**Key Features:**

- **1% Pigeon Fee**: Automatically deducted from output (don't reduce input)
- **Best Price Routing**: Aggregates across multiple DEXs
- **Slippage Protection**: Configurable slippage tolerance
- **Gas Optimization**: Optimized for minimal gas usage

**Example Commands:**

```
Swap 100 USDC for WETH on Base
Swap 0.5 ETH to USDC on Ethereum with 0.5% slippage
Trade 1000 USDC for WBTC on Arbitrum
```

**Important Notes:**

- Input amount is EXACT (100 USDC means exactly 100 USDC)
- 1% fee deducted from output by aggregator
- Contract addresses always verified before execution

---

### batch_swap_kyberswap

Execute multiple swaps in a single transaction.

**Parameters:**

- Array of swaps, each containing:
  - `sellTokenAddress`: Token to sell
  - `buyTokenAddress`: Token to buy
  - `sellAmount`: Amount to sell
  - `slippage`: Individual slippage tolerance
- `network`: Target chain ID

**Benefits:**

- **Gas Efficient**: Multiple swaps in one transaction
- **Atomic Execution**: All swaps succeed or all fail
- **Portfolio Rebalancing**: Perfect for adjusting multiple positions

**Example Commands:**

```
Batch swap on Base: sell 200 USDC to WETH and 0.1 WETH to USDC
Rebalance portfolio: swap 500 USDC to WETH, 500 USDC to WBTC on Ethereum
Multi-swap: 100 USDC each to WETH, WBTC, and LINK on Arbitrum
```

**Use Cases:**

- Portfolio rebalancing
- Dollar-cost averaging across multiple assets
- Arbitrage opportunities
- Mass position entries/exits

---

## Token Management

### approve_evm_token_spending

Approve smart contracts to spend your ERC-20 tokens.

**Parameters:**

- `tokenAddress`: ERC-20 contract address
- `spenderAddress`: Address to approve (usually router/protocol)
- `approvalAmount`: Amount to approve (or max for unlimited)
- `network`: Target chain

**When Required:**

- First time swapping a token
- After previous approval is exhausted
- When switching to new protocols
- For limit order placement

**Example Commands:**

```
Approve KyberSwap router to spend 1000 USDC on Base
Set unlimited approval for WETH on Ethereum
Approve 500 USDC spending on Arbitrum
```

**Security Notes:**

- Approvals are permanent until revoked
- Consider limited approvals for security
- Pigeon shows exact spender addresses for verification

---

### wrap_eth / unwrap_weth

Convert between native ETH and wrapped WETH.

**Parameters:**

- `amount`: Amount to wrap/unwrap
- `network`: Target chain

**Use Cases:**

- Prepare ETH for protocols requiring WETH
- Unwrap WETH back to native ETH
- DeFi protocol interactions

**Example Commands:**

```
Wrap 0.5 ETH on Ethereum
Unwrap 1 WETH to ETH on Base
Convert 0.1 ETH to WETH on Arbitrum
```

---

## Batch Operations

### batch_transfer

Send multiple ERC-20 or native token transfers in one transaction.

**Parameters:**

- `transfers[]`: Array of transfers
  - `tokenAddress`: ERC-20 address (omit for native)
  - `recipient`: Destination address
  - `amount`: Transfer amount
- `network`: Target chain

**Use Cases:**

- **Airdrops**: Distribute tokens to multiple recipients
- **Payouts**: Team/contributor payments
- **Treasury Operations**: Multi-recipient transfers
- **Gas Optimization**: Reduce transaction costs

**Example Commands:**

```
Send 100 USDC to Alice and 0.02 ETH to Bob, both on Base
Batch transfer: 50 USDC each to 5 different addresses on Polygon
Airdrop 1000 tokens to 10 addresses on Ethereum
```

---

## Fee Structure & Economics

### Pigeon Fees

- **Swap Fee**: 1% of output (handled automatically by aggregator)
- **No Input Reduction**: Your specified input amount is exact
- **Transparent**: Fee clearly shown in transaction details
- **No Hidden Costs**: Only network gas fees additional

### Gas Management

- **Estimation**: Accurate gas estimates before execution
- **Optimization**: Routes optimized for gas efficiency
- **Network Native**: Gas paid in native token (ETH, MATIC, etc.)
- **Safety Buffer**: Small buffer added to prevent failures

### Slippage Handling

- **Configurable**: Set slippage per trade (default: 1%)
- **Protection**: Transactions revert if slippage exceeded
- **Market Impact**: Higher amounts may require higher slippage
- **Volatile Tokens**: Consider higher slippage for low-liquidity tokens

---

## Safety Protocols

### Contract Address Verification

- **Always Displayed**: Contract addresses shown for every token
- **Scam Protection**: Verification against known malicious contracts
- **User Confirmation**: Pause and confirm if addresses look suspicious
- **Clear Labeling**: Token names with addresses for clarity

### Transaction Safety

- **Approval Required**: Explicit confirmation before execution
- **Parameter Validation**: All inputs validated before submission
- **Explorer Links**: Every transaction gets blockchain explorer link
- **Clear Reporting**: Exact amounts, fees, and outcomes reported

### Error Handling

- **Graceful Failures**: Clear explanations when transactions fail
- **Retry Logic**: Automatic retry for network issues
- **Debugging Info**: Detailed error messages for troubleshooting
- **Recovery Options**: Suggestions for resolving common issues

---

## Common Workflows

### First-Time Token Swap

1. **Find Token**: Use market data tools to get contract address
2. **Check Balance**: Ensure sufficient token and gas balance
3. **Get Quote**: Preview swap with `kyberswap_get_quote`
4. **Approve Token**: Use `approve_evm_token_spending` if needed
5. **Execute Swap**: Perform swap with desired slippage
6. **Verify**: Check transaction on blockchain explorer

### Portfolio Rebalancing

1. **Current Holdings**: Check portfolio across networks
2. **Plan Swaps**: Determine target allocations
3. **Batch Execution**: Use `batch_swap_kyberswap` for efficiency
4. **Monitor Results**: Verify all swaps executed correctly

### Cross-Network Strategy

1. **Bridge Assets**: Use cross-chain tools to move funds
2. **Network-Specific Trades**: Execute optimal swaps per network
3. **Gas Management**: Ensure native tokens for fees
4. **Consolidation**: Bridge profits back if needed

Need help with EVM trading? Check out the [EVM Swap Playbook](../playbooks/evm-swap.md) for detailed workflows or [Best Practices](../best-practices.md) for optimization tips.
