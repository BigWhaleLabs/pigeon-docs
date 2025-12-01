# Pigeon: Your AI Quant for Infinite Markets

Pigeon is your AI quant for infinite markets. Make money in any market. Trade strategies across crypto, stocks, perps, predictions, and memes all in one chat.

Pigeon is a multi-agent system that pairs world-class AI, Pigeon Code, and protocols that digests everything onchain so users can navigate easily.

### Supported Markets

- **Crypto** (EVM, Solana, and TON — spot and limit, DEX aggregators)
- **Traditional markets** via Ostium (stocks, forex, commodities, indices)
- **Perpetuals** on Hyperliquid (with full order/trigger/TWAP control)
- **Prediction markets** via Polymarket
- **Cross-chain bridging**
- **Social/news sentiment**
- **Pigeon Code** for autonomous monitoring and execution

This comprehensive guide explains everything you can do with Pigeon, including tool coverage, workflows, examples, and best practices.

---

## Table of Contents

1. [Overview](#1-overview)
   - Platforms, Accounts, and Wallets
   - Security and Key Management
   - Supported Networks and Venues
   - Fees and Revenue Sharing
2. [Core Behavior and Safety Protocols](#2-core-behavior-and-safety-protocols)
   - Execution Mandate
   - Contract Address Verification
   - Transaction Hash Formatting
   - Amount Interpretation and Fees
   - Tool Hierarchy and Routing
   - Error Handling and Retries
3. [Quick Start](#3-quick-start)
   - Funding Your Wallet
   - Checking Prices
   - Swapping Tokens
   - Opening a Stock/Forex Trade
   - Placing a Perps Order on Hyperliquid
   - Buying a Polymarket YES/NO Token
   - Bridging Assets Cross-Chain
   - Setting Up Pigeon Code Scripts
4. [Tool Reference (All Tools)](#4-tool-reference-all-tools)
   - Market Data & Discovery
   - Portfolio & Wallet Analytics
   - EVM Trading (KyberSwap Aggregator)
   - Solana Trading (Jupiter)
   - Cross-Chain Bridging (Relay)
   - EVM Limit Orders
   - Wrapping, Transfers, Batch Ops
   - Token Launch & Deployment
   - Social & News Sentiment
   - Pigeon Code
   - Messaging, Identity, and Security
   - Hyperliquid (Perps & Spot)
   - Ostium (Stocks/Forex/Commodities/Indices)
   - Polymarket (Prediction Markets)
   - Unified Portfolio
   - Web Search
   - Utilities
5. [End-to-End Playbooks](#5-end-to-end-playbooks)
   - Full EVM Swap Flow With Approvals
   - Solana DEX Swap and Limit Order Flow
   - Arbitrum USDC → Hyperliquid Deposit + Order + Withdraw
   - Ostium Multi-Step: Open → Update SL/TP → Add Collateral → Close
   - Cross-Chain Bridge to Polygon for Polymarket Gas
   - Portfolio Audit: EVM + Solana + Perps + Ostium + Polymarket
6. [Best Practices and FAQ](#6-best-practices-and-faq)
   - Confirming Ambiguous Assets
   - Slippage and Order Minimums
   - Gas Requirements
   - Rate Limits and Indexing Delays
   - Revshare and Group Operations
   - Support and Announcements

---

## 1) Overview

### Platforms, Accounts, and Wallets

Pigeon runs across multiple platforms:
- **Telegram**: https://t.me/pigeon_trade_bot
- **WhatsApp**: https://wa.me/17813300607
- **Discord**: https://discord.com/oauth2/authorize?client_id=1390098020598550559&permissions=1126176932482112&integration_type=0&scope=bot
- **Messenger**: https://www.facebook.com/profile.php?id=61578109435276
- **Farcaster**: https://farcaster.xyz/pigeontrade
- **XMTP**: https://xmtp.chat/0xC410943B356321a3bBDFBC150D743480BF123370 (Decentralized messaging protocol for secure, private communication)
- **Base App**: https://join.base.app/ (Coinbase's Base Wallet App)
- **SMS**: +1 888 655 8732

**Important**: Each platform creates a separate, unlinked account (and wallets) with distinct balances and history. There is currently no way to merge accounts across platforms.

### Wallet Generation and Custody

- Pigeon uses **Privy (Stripe) MPC wallets**. Private keys are split and managed securely; Pigeon does not have access to your private key. Wallets are fully self-custodial and exportable.
- **Private key export** is available for Telegram, SMS, and WhatsApp at: https://pigeon.trade/privy
- Other platforms (Discord, Farcaster, XMTP, Base App, etc.) are not yet supported for key export.

### Funding URLs

- **EVM**: https://pigeon.trade/[your_evm_address]
- **Solana**: https://pigeon.trade/[your_solana_address]
- Always share the full URL (no shorteners). These pages make it easy to fund your Pigeon wallets.

### Supported Networks and Venues

**EVM Chains**: Ethereum, Base, Arbitrum, Polygon, Optimism, Avalanche, Fantom, BSC
**Solana**: mainnet

**Venues**:
- **DEX Aggregation**: KyberSwap (EVM), Jupiter (Solana)
- **Traditional Markets**: Ostium (stocks, forex, commodities, indices; settled in USDC on Arbitrum)
- **Perpetuals**: Hyperliquid
- **Prediction Markets**: Polymarket (on Polygon, requires POL for gas)

### Fee Structure

- **Crypto DEX swaps**: 1% (automatically handled; do not reduce input amount)
- **Hyperliquid perps**: 4bps (0.04%) with volume discounts at $1M+ monthly volume
- **Ostium**: 4bps (0.04%) with volume discounts at $1M+ monthly volume
- **Polymarket**: No Pigeon fees (platform fees only)

### Referral Program

**Group Referrals (30%)**
- Add Pigeon to any Telegram group → you become the referrer
- Earn 30% of all 1% trading fees from that group's transactions
- No extra setup—just add the bot

**Solo Referrals (20%/10%)**
- Share your ref code with friends
- You earn 20% of fees from anyone who signs up with your code
- They get 10% cashback on their fees

Daily payouts at noon LA time.

---

## 2) Core Behavior and Safety Protocols

### Execution Mandate

- When you approve an action ("yes", "do it", "proceed"), Pigeon executes immediately with no pre-action commentary.
- Pigeon reports only actual results returned by tools.

### Contract Address Verification (Critical)

To prevent mistakes and scams, Pigeon always verifies and displays contract addresses (CAs) for token operations.

**Mandatory scenarios**:
- Any sell operation: show CA
- Any swap operation: show both token CAs (or Solana mint addresses)
- Allowance/approval errors: show CA
- Token searches: show CA next to token names
- Portfolio displays: show CAs for unfamiliar tokens

If the CA looks different from what you expect, Pigeon pauses and asks you to confirm.

**Example**: "Found PEPE (CA: 0x6982508145454ce325ddbe47a25d4ec3d2311933), price $0.000018. Is this the one?"

### Transaction Hash Formatting

- **EVM Base**: https://basescan.org/tx/[hash]
- **Ethereum**: https://etherscan.io/tx/[hash]
- **Solana**: https://solscan.io/tx/[signature]

Pigeon always shares explorer links, not raw hashes.

### Amount Interpretation and Fee Handling

- **"$100"** means $100 USD worth of collateral or spend
- **"1 ETH"** or **"100 USDC"** means exactly that token amount
- **"half"** means 50% of balance; **"all"** means full available balance minus network gas safety
- **Critical for swaps**: If you say "swap 100 USDC", Pigeon inputs exactly 100 USDC. The 1% Pigeon fee is deducted from the output by the aggregator (not from the input).

### Tool Hierarchy and Routing

- **Traditional assets** (e.g., NVDA, GOLD, EUR/USD):
  - Always searches traditional markets first
- **Crypto prices and token info** (e.g., SOL, ETH, PEPE):
  - Always searches crypto markets first
- **News and analysis**:
  - Uses web search only when specialized tools don't cover the need

### Error Handling and Retries

- Pigeon validates parameters, confirms ambiguous assets, and retries once with refined parameters if needed
- Uses a sleep/backoff (15–300 seconds) for transient issues or indexing delays
- Explains failures clearly and suggests next steps

---

## 3) Quick Start

### Funding Your Wallet

Send assets to your Pigeon wallets:
- **EVM**: https://pigeon.trade/[your_evm_address]
- **Solana**: https://pigeon.trade/[your_solana_address]

**Gas Requirements**:
- For EVM swaps: ensure you have the tokens you want to sell and enough native gas (ETH on Ethereum/Base; MATIC/POL on Polygon; etc.)
- For Polymarket: you need POL (Polygon gas) to approve USDC and trade
- For Ostium: you need USDC on Arbitrum

### Check a Price

**Traditional**: "What's the price of Gold?"
- Pigeon uses `ostium_get_available_pairs` to return XAU price

**Crypto**: "Get SOL price"
- Pigeon uses `gecko_search_tokens_and_pools` to return SOL price

### Swap Tokens (EVM Example)

**Prompt**: "Swap 100 USDC for WETH on Base"

**Pigeon process**:
1. Finds the tokens and shows contract addresses for verification
2. Gets a quote with slippage and gas estimates
3. Handles any required approvals automatically
4. Executes the swap with exactly 100 USDC input
5. Returns transaction link and updated balances

### Open a Stock/Forex Trade (Ostium)

**Prompt**: "Buy 1 share of NVDA with 10x leverage"

**Pigeon process**:
1. Finds NVDA and gets current price
2. Places the leveraged trade order
3. Returns order details and fees (Ostium fees only)

### Perps on Hyperliquid

**Prompt**: "Long SOL-PERP, 2 size, 5x leverage, market"

**Pigeon process**:
1. Verifies market availability and price
2. Places the perpetual order with specified leverage
3. Returns order details and open positions

### Polymarket Example

**Prompt**: "Buy $50 of YES for 'Will BTC be above $100k by Dec 31?'"

**Pigeon process**:
1. Finds the prediction market
2. Confirms the market condition and tokens
3. Handles required approvals (needs POL for gas)
4. Places the market order

### Bridge Assets Cross-Chain

**Prompt**: "Bridge 0.5 ETH from Ethereum to Base"

**Pigeon process**:
1. Gets a bridge quote with rates and fees
2. Executes the cross-chain transfer
3. Returns completion details when bridging is done

### Pigeon Code (Autonomous Scripts)

**Prompt**: "Every 10 min, alert me if SOL falls below $150 and include contract/mint"

Pigeon creates an autonomous script that runs checks on your specified schedule. You can also use timezone-aware scheduling like "Every day at 9 AM Eastern, send me a portfolio summary".

---

## 4) Tool Reference (All Tools)

This section documents all tools available to Pigeon. Each entry includes purpose, parameters, and typical use cases with example prompts.

### A) Market Data & Discovery

#### gecko_search_tokens_and_pools
**Purpose**: Primary crypto price source. Search tokens by name/symbol/address across networks and get live price/pool info.

**Parameters**:
- `queries`: array of token queries (e.g., ["SOL"])
- `network`: "all" or a specific network if constrained
- `include`: "base_token,quote_token,dex,network"
- `page`: results page

**Use cases**:
- Verify token CA and price before swaps
- Find the correct token when multiple exist

**Example prompt**: "Price of SOL" (Pigeon searches for crypto prices first)

**Notes**: Always used first for crypto price queries.

#### gecko_discover_trending_tokens_global
**Purpose**: Trending tokens globally to find momentum plays.

**Parameters**: 
- `include`: fields
- `page`: (1–10)
- `duration`: ("5m", "1h", "6h", "24h")

**Use**: Alpha hunting and early discovery

**Example**: "Show me trending tokens globally for the last hour."

#### gecko_discover_trending_tokens_by_chain
**Purpose**: Trending tokens on a specific chain (ETH, Solana, Base, etc.)

**Parameters**: `network`, `include`, `page`, `duration`

**Example**: "What's trending on Solana over the past 5 minutes?"

#### gecko_analyze_multiple_tokens
**Purpose**: Batch analyze multiple ERC-20s on one network with top pools info.

**Parameters**: `network`, `token_addresses[]`, `include` ("top_pools")

**Example**: "Compare these 5 Base tokens and show their best pools."

#### moralis_get_top_tokens_by_market_cap
**Purpose**: Top ERC-20s by global market cap.

**Use**: Quick discovery of blue chips for on-chain strategies.

#### lunarcrush_get_crypto_social_sentiment
**Purpose**: Social sentiment and viral posts for a token/project.

**Parameters**: `topic` (name/ticker), `limit` of posts

**Use**: Gauge community hype and potential catalysts

**Example**: "Show me sentiment and top 10 viral posts for WIF."

#### lunarcrush_get_crypto_news_sentiment
**Purpose**: News sentiment for a topic

**Parameters**: `topic`

**Use**: Track news-driven risk for tokens

**Example**: "News sentiment for Solana?"

#### web_search_duckduckgo
**Purpose**: General research and current events when specialized tools lack data.

**Parameters**: `queries[]`, `limit`, `fetch`

**Use**: Macro news, company updates, or non-crypto topics

**Rule**: Use specialized tools first for prices.

---

### B) Portfolio & Wallet Analytics

#### unified_portfolio_analysis
**Purpose**: Complete multi-chain, multi-venue portfolio snapshot
- Solana token balances + Jupiter limit orders
- EVM balances (multiple chains)
- 1inch limit orders
- Hyperliquid perps, spot balances, orders, TWAP fills
- Ostium positions
- Polymarket open orders; USDC approvals

**Parameters**:
- `evm_wallet_address`, `solana_wallet_address`

**Use**:
- "What's my net worth?"
- "List my open orders and positions everywhere."

#### moralis_get_wallet_history
**Purpose**: Decoded EVM wallet transactions (with internal txs optionally)

**Parameters**: `address`, `chain`, `date/block` range, `pagination`, `order`, `limit`, `include_internal_transactions`, `nft_metadata`

**Use**: Compliance, accounting, and audit trails

#### moralis_get_token_transfers
**Purpose**: ERC-20 transfer history for a wallet

**Use**: Track inflows/outflows per token

#### moralis_get_wallet_swaps
**Purpose**: DEX swap history for a wallet

**Use**: Analyze trading performance on EVM

#### moralis_evm_get_wallet_profitability
**Purpose**: Tokenized P&L overview over time

**Parameters**: `address`, `days` ("all", "7", "30", "60", "90"), `chain`, `token` filter

**Use**: "Show my P&L in the last 30 days on Base."

#### solana_get_transaction_history
**Purpose**: Solana transaction history (transfers, swaps, NFT trades, etc.)

**Parameters**: `address`, `before/until`, `commitment`, `limit`

**Use**: Forensic analysis and P&L reconstruction

#### solana_calculate_pnl
**Purpose**: Realized P&L in SOL for a specific token

**Parameters**: `wallet_address`, `token_address`

**Use**: Token-level performance on Solana

#### solana_get_token_holder_stats
**Purpose**: Holder counts and concentration for a token

**Use**: Assess whale risk and distribution health

---

### C) EVM Trading (KyberSwap Aggregator)

#### kyberswap_get_quote
**Purpose**: Get a swap quote without executing (routes, gas, est. output)

**Parameters**: `sellTokenAddress`, `buyTokenAddress`, `sellAmount`, `slippage` (%), `network` (chainId)

**Use**: Preview outcomes and slippage before executing

**Example**: "Quote 250 USDC to WETH on Base with 1% slippage."

#### batch_swap_kyberswap
**Purpose**: Execute multiple swaps in a single batch on the same network

**Parameters**: array of swaps (`sellTokenAddress`, `buyTokenAddress`, `sellAmount`, `slippage`), `network`

**Use**: Rebalance several tokens at once

#### approve_evm_token_spending
**Purpose**: Approve a spender to spend your ERC-20 (router, protocol)

**Parameters**: `tokenAddress`, `spenderAddress`, `approvalAmount`, `network`

**Use**: Required before swapping a token for the first time

#### wrap_eth / unwrap_weth
**Purpose**: Convert ETH to WETH and vice versa

**Parameters**: `amount`, `network`

**Use**: Needed for some protocols that require wrapped assets

#### batch_transfer
**Purpose**: Send multiple ERC-20/native transfers in one operation

**Parameters**: `transfers[]` (tokenAddress optional for native), `network`

**Use**: Airdrops, mass payouts, operational treasury moves

**Notes**:
- Always confirm token CAs before swapping
- Fees: 1% Pigeon swap fee baked into output; do not reduce input amount

---

### D) Solana Trading (Jupiter + Wallet Tools)

#### solana_actions_jupiterSwap
**Purpose**: Execute Solana swaps with Jupiter

**Parameters**: `outputMint`, `inputAmount`, `inputMint`, `slippageBps`

**Use**: SOL to SPL or cross-SPL swaps

**Notes**:
- Use `So11111111111111111111111111111111111111112` for SOL
- Slippage in basis points (e.g., 300 = 3%)

#### solana_actions_jupiter_limit_order_create
**Purpose**: Create non-blocking limit orders on Solana

**Parameters**: `inputMint`, `outputMint`, `makingAmount`, `takingAmount`, optional `expiredAt`, `slippageBps`

**Use**: Automated entries, take profits, and trailing strategies

**Warnings**:
- Minimum order value ~$5 USD
- Jupiter does not validate unrealistic prices; you must set sane rates
- 0% slippage by default on trigger; add slippage if fills stall

#### solana_actions_jupiter_limit_order_cancel
**Purpose**: Cancel one or more limit orders (pass empty array to cancel all)

**Parameters**: `orders[]` (order account addresses)

**Use**: Update any limit order by cancel → recreate with new params

#### solana_actions_jupiter_get_limit_order_history
**Purpose**: Fetch limit order history for accounting and monitoring

**Parameters**: `page`, `inputMint`, `outputMint`

#### solana_actions_transferTokens
**Purpose**: Transfer SOL or SPL tokens

**Parameters**: `to` (recipient), `amount`, optional `mint` (omit for native SOL)

#### solana_actions_unwrapSol
**Purpose**: Unwrap WSOL back to native SOL (close WSOL account)

#### solana_actions_closeEmptyTokenAccounts
**Purpose**: Close empty Token and Token-2022 accounts to reclaim rent

**Notes**:
- Always display mint addresses when swapping or selling
- Jupiter limit orders do not lock funds until they fill

---

### E) Cross-Chain Bridging (Relay)

#### relay_get_crosschain_quote
**Purpose**: Get cross-chain bridge quote (rates, fees, output estimates)

**Parameters**: `srcChainId`, `dstChainId`, `srcTokenAddress`, `dstTokenAddress`, `amount`, `fromAddress`, `recipient` (optional), `slippageTolerance` (bps)

**Use**: Compare bridging options before executing

**Example**: "Quote: 0.25 ETH from Ethereum to Base."

#### relay_bridge_tokens_cross_chain
**Purpose**: Execute bridging; completes when tool returns success

**Parameters**: `srcChainId`, `dstChainId`, `srcTokenAddress`, `dstTokenAddress`, `amount`, `fromAddress`, `recipient`, `slippageTolerance`

**Use**: Move assets to a destination chain for a trade or gas need

#### relay_check_bridge_status
**Purpose**: Check ongoing bridge operation by requestId

**Use**: Tracking long bridges if needed

---

### F) EVM Limit Orders

#### evm_place_limit_order
**Purpose**: Create EVM limit orders (non-blocking; tokens transfer only upon execution)

**Parameters**: `fromAddress`, `network` (1, 8453, 42161, 137), `makerAssetAddress`, `takerAssetAddress`, `makerAmount`, `takerAmount`, `expiresInSeconds`

**Use**: Stop losses, take profits, trailing (via cancel/recreate pattern)

**Notes**: Modify orders by cancel → re-place

#### evm_cancel_limit_order
**Purpose**: Cancel a specific EVM limit order

**Parameters**: `orderHash`, `network`, `makerTraits`

**Use**: Update strategy or prevent accidental fills

---

### G) Wrapping, Transfers, and Batch Ops

- `wrap_eth` / `unwrap_weth`: ETH↔WETH conversions
- `batch_transfer`: Multiple sends in one shot
- `approve_evm_token_spending`: Manage allowances

**Example**: "Send 100 USDC to Alice and 0.02 ETH to Bob, both on Base."

---

### H) Token Launch & Deployment

#### solana_launch_pumpfun_token
**Purpose**: Launch a token on Pump.fun with 0.001 SOL initial buy

**Parameters**: `name` (max 12), `symbol` (max 8), `description`, `imageUrl`, `amount`, `twitter`, `telegram`, `website`

**Use**: Spin up a meme token; market bootstrapping

#### deploy_clanker_token (Base)
**Purpose**: Deploy an ERC-20 token using Clanker on Base, with IPFS and 25% interface rewards to Pigeon

**Parameters**: `name`, `symbol`, `description`, `imageUrl`, `twitter`, `telegram`, `website`, `initialMarketCap` (ETH), `devBuyAmount` (ETH)

**Use**: Launch an EVM token with initial liquidity and dev buy

**Notes**: Token launches are high risk; ensure brand, compliance, and liquidity strategy

---

### I) Social & News Sentiment (LunarCrush)

- `lunarcrush_get_crypto_social_sentiment`: Viral posts and sentiment
- `lunarcrush_get_crypto_news_sentiment`: News sentiment

**Use**:
- Pre-trade sentiment check for momentum entries/exits
- Community health monitoring

---

### J) Pigeon Code

#### create_automated_task
**Purpose**: Create autonomous scripts to monitor or act on signals

**Parameters**:
- `description` (what you want monitored or reported)
- `interval_minutes` for recurring, or `delay_minutes` for one-time delayed
- `duration_minutes` how long to run (empty for indefinite)
- `run_at_local_time` for daily schedule (HH:MM format, e.g., "09:00")
- `run_timezone` IANA timezone (e.g., "America/New_York")

**Use**: Price alerts, position monitoring, portfolio reports, daily summaries

**Examples**: 
- "Every 2 minutes, send SOL price and contract address."
- "Every day at 9 AM Eastern, send portfolio summary."

#### list_automated_tasks
**Purpose**: View created scripts, next run time, execution history, status

#### get_automation_source_code
**Purpose**: Retrieve the generated TypeScript source code for an active script

**Parameters**: `automation_id`

#### get_automation_execution_history
**Purpose**: Paginated execution history for debugging and monitoring

**Parameters**: `automation_id`, `page`, `page_size`

#### request_automation_edit
**Purpose**: Request AI-powered changes to an existing script

**Parameters**: `automation_id`, `feedback`, `history_limit`, `preview_only`

#### cancel_automated_task
**Purpose**: Delete an existing script

---

### K) Messaging, Identity, and Security

#### pigeon_clear_message_history
**Purpose**: Reset conversation context completely (irreversible)

**Use**: Fresh start; remove stale context

#### pigeon_toggle_follow_up_messages / pigeon_get_follow_up_messages_status
**Purpose**: Enable/disable status updates during long operations

**Use**: "Stop sending status updates." / "Resume follow-ups."

#### pigeon_get_setup_totp_url / pigeon_finish_totp_setup / pigeon_remove_totp
**Purpose**: TOTP 2FA for sensitive actions

**Use**: Secure your account's MCP actions

#### Identity Lookups
- `pigeon_get_addresses_for_phone_number`
- `pigeon_get_addresses_for_telegram_username`
- `pigeon_get_addresses_for_farcaster_username`

**Use**: Find addresses associated with a known identifier (for routing transfers)

#### Telegram Group Tools
- `pigeon_get_telegram_messages`
- `pigeon_get_telegram_group_info`
- `pigeon_get_telegram_group_users`
- `pigeon_get_telegram_group_referrer`

**Use**: Group management, referrer lookup, and analytics

**Revenue Share**:
- `pigeon_get_paid_referral_fees`
- `pigeon_get_unpaid_referral_fees`

---

### L) Hyperliquid (Perps & Spot)

#### hyperliquid_get_perpetual_markets / hyperliquid_get_spot_markets
**Purpose**: Market discovery and live metrics

#### hyperliquid_get_order_book
**Purpose**: Order book snapshot (bids/asks)

#### hyperliquid_place_perp_order
**Purpose**: Place perps long/short orders (market/limit), set leverage, cross/isolated

**Parameters**: `asset`, `side`, `size`, `orderType`, `price` (0 for market), `reduceOnly`, `leverage`, `isCross`

**Notes**:
- Min notional $10 (price * size)
- To close a long: place short with same size (reduceOnly recommended)

#### hyperliquid_place_trigger_order
**Purpose**: Stop-loss / Take-profit trigger orders

**Parameters**: `asset`, `side`, `size`, `triggerPrice`, `orderType`, `limitPrice`, `reduceOnly`, `type` ("take_profit" | "stop_loss"), `leverage`, `isCross`

#### hyperliquid_place_twap_order
**Purpose**: Time-Weighted Average Price execution

**Parameters**: `asset`, `side`, `size`, `durationMinutes`, `randomize`, `reduceOnly`, `leverage`, `isCross`

#### hyperliquid_cancel_perp_order / hyperliquid_cancel_twap_order
**Purpose**: Cancel open orders/TWAPs

#### hyperliquid_update_isolated_margin
**Purpose**: Add/remove isolated margin

#### hyperliquid_schedule_cancel_all_orders
**Purpose**: Dead man's switch to cancel all at a future time

#### hyperliquid_get_user_open_orders / hyperliquid_get_user_twap_slice_fills / hyperliquid_get_user_history
**Purpose**: Account-level order history, open orders, and fills

#### hyperliquid_deposit_to_bridge / hyperliquid_withdraw_from_bridge
**Purpose**: On-ramp/off-ramp USDC between Arbitrum and Hyperliquid

**Notes**:
- Min deposit 5 USDC, otherwise funds are lost
- Withdrawals process in ~15 minutes

#### hyperliquid_deposit_to_staking / hyperliquid_withdraw_from_staking / hyperliquid_delegate_stake / hyperliquid_undelegate_stake
**Purpose**: Manage HYPE staking and delegation

**Notes**: Unstaking/delegation periods apply per platform rules

---

### M) Ostium (Stocks, Forex, Commodities, Indices)

All Ostium trades settle in USDC on Arbitrum. Pigeon fee: 4bps (0.04%) with volume discounts at $1M+ monthly volume.

#### ostium_get_available_pairs
**Purpose**: List all tradable pairs and live prices (mandatory for traditional price queries)

#### ostium_get_current_price / ostium_get_pair_analytics / ostium_get_pair_activity_stats
**Purpose**: Specific price, analytics (fees, OI, constraints), and activity stats

#### ostium_open_trade
**Purpose**: Open a leveraged trade

**Parameters**: `assetSymbol`, `side` (long/short), `collateral` (USDC), `leverage`, `orderType` (market/limit/stop), `price` (for limit/stop), `takeProfitPrice`, `stopLossPrice`, `slippagePercentage`

**Notes**:
- Minimum exposure requirement (collateral * leverage ≥ $1,500)
- Pigeon reports exact collateral, leverage, and fees

#### ostium_close_trade
**Purpose**: Close an open trade fully or partially

**Parameters**: `pairId`, `tradeIndex`, `percentage` (1–100)

#### ostium_update_sl_tp
**Purpose**: Update SL/TP on open trades

#### ostium_add_collateral / ostium_remove_collateral
**Purpose**: Adjust collateral on open trades

#### ostium_get_open_trades / ostium_get_limit_orders / ostium_get_trade_history / ostium_get_order_details
**Purpose**: Visibility and recordkeeping

---

### N) Polymarket (Prediction Markets on Polygon)

**Gas requirement**: You need POL to approve USDC and trade.

#### polymarket_search_markets
**Purpose**: Search markets via SIMPLE tsquery (use &, |, ! operators only)

**Parameters**: `query`, `conditionId` (exact match), `filters` (active/closed, category, volume range, end dates, tags), `sorting`, `pagination`

**Use**: Find precise markets to trade

#### polymarket_get_market
**Purpose**: Detailed market info by condition ID

#### polymarket_get_orderbook / polymarket_get_prices
**Purpose**: Orderbook and live prices for YES/NO tokens

#### polymarket_update_balance
**Purpose**: Update cached balances/allowances for USDC or conditional tokens

#### polymarket_ensure_approvals
**Purpose**: Ensure USDC approvals (CTF, Exchange, Neg Risk, Adapter) and CTF approvals

**Notes**: Requires POL for gas

#### polymarket_create_order (Limit)
**Purpose**: Place limit order to buy/sell YES/NO tokens

**Parameters**: `tokenId`, `side` (BUY/SELL), `price` (0.01–0.99), `size`, `orderType` (GTC/GTD), `expiration` (if GTD)

#### polymarket_create_market_order
**Purpose**: Market buy/sell

**Parameters**: `tokenId`, `side` (BUY/SELL), `amount` (USD to spend or tokens to sell), `orderType` (FOK/FAK)

#### polymarket_cancel_order / polymarket_cancel_all_orders
**Purpose**: Cancel specific or all open orders

#### polymarket_get_trades
**Purpose**: History filters by market, asset, maker address

---

### O) Memory Management

- `list_memories`: View stored memories
- `delete_memories`: Remove specific memories by ID
- `clear_all_memories`: Reset all stored memories

**Notes**: A background memory agent auto-saves relevant info (e.g., recurring alerts). Use these tools for explicit control.

---

### P) Web Search

- `web_search_duckduckgo`: Non-market or general research; optionally fetch page content
- Use when specialized tools do not apply

---

### Q) Utilities

#### sleep
**Purpose**: Wait between steps (15–300 seconds) for finality, rate limits, or backoff

#### multi_tool_use.parallel
**Purpose**: Run compatible tools in parallel to save time

**Use**: Portfolio aggregation across multiple sources concurrently

---

## 5) End-to-End Playbooks

### Playbook A: Full EVM Swap Flow with Approvals

1. **Identify tokens and CAs**:
   - Pigeon queries `gecko_search_tokens_and_pools` for both sell and buy tokens
   - Displays CAs for verification

2. **Get a quote**:
   - `kyberswap_get_quote` with sellTokenAddress, buyTokenAddress, sellAmount, slippage, network

3. **Approvals if needed**:
   - `approve_evm_token_spending` for sell token and aggregator router

4. **Execute swap**:
   - `batch_swap_kyberswap` (or single swap) with exact input amount
   - Pigeon fee 1% deducted from output; input remains unchanged

5. **Report**:
   - Transaction link on the appropriate explorer
   - Updated balances (note indexing delays)

**Example prompt**: "Swap 1 ETH to USDC on Base with 0.5% slippage."

---

### Playbook B: Solana DEX Swap and Limit Order Flow

1. **Identify mints**:
   - Pigeon shows mint addresses for input/output tokens

2. **Market swap**:
   - `solana_actions_jupiterSwap` with inputMint/outputMint, inputAmount, slippageBps

3. **Limit orders**:
   - `solana_actions_jupiter_limit_order_create` with makingAmount/takingAmount
   - Manage via cancel and recreate for updates
   - Optional `solana_actions_jupiter_limit_order_cancel` to stop execution

4. **Post-execution**:
   - Pigeon shares Solscan link and updated balances

**Example prompt**:
- "Swap 10 SOL to JUP with 2% slippage."
- "Place a limit order: sell 500 JUP for 2 SOL."

---

### Playbook C: Arbitrum USDC → Hyperliquid Deposit → Order → Withdraw

1. **Deposit**:
   - `hyperliquid_deposit_to_bridge` with min 5 USDC

2. **Place order**:
   - `hyperliquid_place_perp_order` (market/limit) with leverage, cross/isolated

3. **Triggers**:
   - `hyperliquid_place_trigger_order` for SL/TP

4. **TWAP**:
   - `hyperliquid_place_twap_order` for gradual execution

5. **Withdraw**:
   - `hyperliquid_withdraw_from_bridge` back to Arbitrum wallet

6. **Monitor**:
   - `hyperliquid_get_user_open_orders`, `hyperliquid_get_user_history`

**Example prompt**: "Deposit 200 USDC to Hyperliquid, then long BTC-PERP 0.01 size 5x market with SL at 3% below entry."

---

### Playbook D: Ostium Multi-Step Trade Management

1. **Discovery**:
   - `ostium_get_available_pairs` → verify asset

2. **Open**:
   - `ostium_open_trade` with collateral, leverage, orderType, SL/TP

3. **Manage**:
   - `ostium_update_sl_tp` to refine risk/reward
   - `ostium_add_collateral` / `ostium_remove_collateral` for risk adjustment

4. **Close**:
   - `ostium_close_trade` fully or partially

5. **Visibility**:
   - `ostium_get_open_trades`, `ostium_get_trade_history`, `ostium_get_order_details`

**Example prompt**: "Open 2x long on GOLD with $1,000 collateral, TP at 1%, SL at 0.5%."

---

### Playbook E: Bridge to Polygon for Polymarket Gas

1. **Gas prep**:
   - Bridge small ETH to Polygon (for POL, if needed) via `relay_get_crosschain_quote` + `relay_bridge_tokens_cross_chain`

2. **Approvals**:
   - `polymarket_ensure_approvals` (requires POL gas)

3. **Trade**:
   - `polymarket_search_markets` → pick condition
   - Get token IDs → `polymarket_create_market_order` (BUY)

4. **Manage**:
   - `polymarket_cancel_order` or `polymarket_cancel_all_orders`
   - `polymarket_get_trades` for recordkeeping

**Example prompt**: "Bridge 0.03 ETH to Polygon, then buy $50 of YES on the US election turnout market."

---

### Playbook F: Portfolio Audit

1. **unified_portfolio_analysis**:
   - Provide both EVM and Solana addresses
   - Pigeon collects balances, orders, and positions across:
     - Solana tokens + Jupiter orders
     - EVM balances across chains
     - 1inch limit orders
     - Hyperliquid perps/spot
     - Ostium positions
     - Polymarket orders and allowances

2. **Follow-ups**:
   - Chain-specific histories using Moralis and Solana tools
   - Profitability: `moralis_evm_get_wallet_profitability`, `solana_calculate_pnl`

**Example prompt**: "Show my entire portfolio, including open orders and P&L last 30 days."

---

## 6) Best Practices and FAQ

### Confirm Ambiguous Assets

Many tokens share names. Pigeon always shows CAs and asks to confirm if ambiguous. Always double-check the CA before approving a trade.

### Slippage and Order Minimums

- Set reasonable slippage for DEX swaps; too tight may fail
- Jupiter limit orders: min ~$5 USD; unrealistic prices will execute if they ever become valid

### Gas Requirements

- **EVM**: ensure native gas on the network you're transacting
- **Polygon/Polymarket**: you need POL for approvals and trades
- **Solana**: ensure enough SOL for network fees

### Rate Limits and Indexing Delays

Some explorers and indexers take time to update. Pigeon may sleep and retry to ensure accurate state.

### Referral Program

**Group Referrals (30%)**: Add Pigeon to a Telegram group → earn 30% of 1% trading fees from that group.

**Solo Referrals (20%/10%)**: Share your ref code → you earn 20% of their fees, they get 10% cashback.

Daily payouts at noon LA time.

### "Silly Pigeon" Recovery Strategy

If a tool is missing or not enabled, Pigeon will ask for confirmation and attempt again as soon as tools are ready:
- "Whoops, wrong toolset. Confirm you want me to long EUR/USD? Say 'yes'."

### Support and Announcements

- **Support**: https://t.me/pigeon_trade_support
- **Announcements**: https://t.me/pigeon_trade

---

## Prompt Examples Cheat Sheet

### Prices
- "What's the price of GOLD?"
- "Get SOL price."

### Swaps
- "Swap 100 USDC for WETH on Base at 1% slippage."
- "Batch swap: sell 200 USDC to WETH and 0.1 WETH to USDC on Base."

### Approvals
- "Approve router to spend 1000 USDC on Base."

### Solana
- "Swap 5 SOL to JUP with 2% slippage."
- "Create a limit order: sell 1000 JUP for 1.2 SOL, expire in 24h."

### Bridging
- "Bridge 0.5 ETH from Ethereum to Arbitrum."

### EVM Limit Orders
- "Place a limit order: sell 500 USDC for WETH on Base; expire in 7 days."

### Ostium (Traditional)
- "Open a 10x long on NVDA with $200 collateral, market, TP at +5%, SL at −2%."
- "Close 50% of my GOLD long."

### Hyperliquid
- "Long BTC-PERP size 0.02, 5x, isolated, market; set SL at 2%."
- "TWAP buy SOL-PERP size 1 over 60 minutes."

### Polymarket
- "Search: 'BTC & !ETH' ending after Dec 1."
- "Buy $25 of YES on condition 0xabc... FOK."

### Portfolio
- "Show my full portfolio across chains and venues."
- "P&L last 30 days on Base; top losing tokens?"

### Sentiment
- "Top 10 viral posts for WIF; sentiment score?"

### Automation
- "Every 15 min, DM me BTC price and 24h change."

### Referrals
- "Who added the bot to this Telegram group?"
- "What are my unpaid referral fees?"
- "Set my refcode to MYCODE"

---

## Security and Compliance Notes

- Privy (Stripe) MPC custody; Pigeon cannot access your private keys; fully self-custodial and exportable
- Telegram/SMS/WhatsApp users can export keys: https://pigeon.trade/privy
- Markets and tools are volatile and high risk; do your own research
- Respect venue-specific minimums and constraints (e.g., Hyperliquid min notional, Ostium min exposure, Jupiter min order value)

---

## Funding URLs (Examples)

- **EVM**: https://pigeon.trade/0x1234567890123456789012345678901234567890
- **Solana**: https://pigeon.trade/So11111111111111111111111111111111111111112

Replace with your own addresses on your platform account. Always share the complete URL.

---

## Changelog Highlights (Conceptual)

- Multi-venue aggregation in one portfolio call
- Full Hyperliquid integration (perps, triggers, TWAP, staking)
- Ostium traditional assets with 4bps fees (volume discounts available)
- Polymarket approvals automation and order management
- Cross-chain bridging with instant completion reporting
- Automation engine for recurring alerts and research
- Referral program: group (30%) and solo (20%/10%) with daily payouts

---

If you want this documentation tailored with your own favorite prompts, recurrent alerts, or branded visuals, just say:
"Create an onboarding doc for my team with our example prompts and workflows."
