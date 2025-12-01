# Tools Reference

## Market Data & Discovery

### gecko_search_tokens_and_pools
**Purpose**: Primary crypto price source. Search tokens by name/symbol/address across networks and get live price/pool info.

**Parameters**:
- `queries`: array of token queries (e.g., ["SOL"])
- `network`: "all" or a specific network if constrained
- `include`: "base_token,quote_token,dex,network"
- `page`: results page

**Use cases**: Verify token CA and price before swaps, find the correct token when multiple exist

**Example**: "Price of SOL" (Pigeon runs gecko_search_tokens_and_pools first)

### gecko_discover_trending_tokens_global
**Purpose**: Trending tokens globally to find momentum plays.

**Parameters**: `include` fields, `page` (1–10), `duration` ("5m", "1h", "6h", "24h")

**Use**: Alpha hunting and early discovery

### gecko_discover_trending_tokens_by_chain
**Purpose**: Trending tokens on a specific chain (ETH, Solana, Base, etc.)

**Parameters**: `network`, `include`, `page`, `duration`

### lunarcrush_get_crypto_social_sentiment
**Purpose**: Social sentiment and viral posts for a token/project.

**Parameters**: `topic` (name/ticker), `limit` of posts

**Use**: Gauge community hype and potential catalysts

### lunarcrush_get_crypto_news_sentiment
**Purpose**: News sentiment for a topic

**Parameters**: `topic`

**Use**: Track news-driven risk for tokens

### ostium_get_available_pairs
**Purpose**: List all tradable pairs and live prices (mandatory for traditional price queries)

**Use**: Traditional assets (stocks, forex, commodities, indices)

## Trading Execution

### EVM Trading (KyberSwap Aggregator)

#### kyberswap_get_quote
**Purpose**: Get a swap quote without executing (routes, gas, est. output)

**Parameters**: `sellTokenAddress`, `buyTokenAddress`, `sellAmount`, `slippage` (%), `network` (chainId)

#### batch_swap_kyberswap
**Purpose**: Execute multiple swaps in a single batch on the same network

**Parameters**: array of swaps (`sellTokenAddress`, `buyTokenAddress`, `sellAmount`, `slippage`), `network`

#### approve_evm_token_spending
**Purpose**: Approve a spender to spend your ERC-20 (router, protocol)

**Parameters**: `tokenAddress`, `spenderAddress`, `approvalAmount`, `network`

### Solana Trading (Jupiter)

#### solana_actions_jupiterSwap
**Purpose**: Execute Solana swaps with Jupiter

**Parameters**: `outputMint`, `inputAmount`, `inputMint`, `slippageBps`

**Notes**: Use `So11111111111111111111111111111111111111112` for SOL

#### solana_actions_jupiter_limit_order_create
**Purpose**: Create non-blocking limit orders on Solana

**Parameters**: `inputMint`, `outputMint`, `makingAmount`, `takingAmount`, optional `expiredAt`, `slippageBps`

**Warnings**: Minimum order value ~$5 USD, Jupiter does not validate unrealistic prices

### TON Trading (DeDust)

#### ton_swap
**Purpose**: Swap tokens on TON blockchain using DeDust DEX

**Parameters**: 
- `fromToken`: "TON" for native or jetton address (e.g., USDT: `EQCxE6mUtQJKFnGfaROTKOt1lZbDiiX1kCixRv7Nw2Id_sDs`)
- `toToken`: "TON" for native or jetton address
- `amount`: Human-readable amount (e.g., "10" for 10 TON)
- `slippageTolerance`: Percentage (e.g., "1" for 1%, empty string for default)

**Use**: Swap between native TON and jettons (USDT, USDC, etc.) or between different jettons

**Example**: "Swap 10 TON for USDT on TON"

#### ton_transfer
**Purpose**: Transfer TON or jettons to another address

**Parameters**: `toAddress`, `amount`, `token` (optional, defaults to native TON)

**Example**: "Send 5 TON to UQ..."

#### ton_bridge
**Purpose**: Bridge assets from EVM chains to TON

**Parameters**: `fromChain`, `amount`, `token`

**Example**: "Bridge 100 USDC from Base to TON"

#### ton_bridge_out
**Purpose**: Bridge assets from TON to EVM chains

**Parameters**: `toChain`, `amount`, `token`

**Example**: "Bridge 50 USDT from TON to Ethereum"

### Hyperliquid (Perps & Spot)

#### hyperliquid_place_perp_order
**Purpose**: Place perps long/short orders (market/limit), set leverage, cross/isolated

**Parameters**: `asset`, `side`, `size`, `orderType`, `price` (0 for market), `reduceOnly`, `leverage`, `isCross`

**Notes**: Min notional $10 (price * size)

#### hyperliquid_place_trigger_order
**Purpose**: Stop-loss / Take-profit trigger orders

**Parameters**: `asset`, `side`, `size`, `triggerPrice`, `orderType`, `limitPrice`, `reduceOnly`, `type` ("take_profit" | "stop_loss"), `leverage`, `isCross`

#### hyperliquid_place_twap_order
**Purpose**: Time-Weighted Average Price execution

**Parameters**: `asset`, `side`, `size`, `durationMinutes`, `randomize`, `reduceOnly`, `leverage`, `isCross`

### Ostium (Traditional Assets)

#### ostium_open_trade
**Purpose**: Open a leveraged trade

**Parameters**: `assetSymbol`, `side` (long/short), `collateral` (USDC), `leverage`, `orderType` (market/limit/stop), `price` (for limit/stop), `takeProfitPrice`, `stopLossPrice`, `slippagePercentage`

**Notes**: Minimum exposure requirement (collateral * leverage ≥ $1,500)

### Polymarket (Prediction Markets)

#### polymarket_create_market_order
**Purpose**: Market buy/sell

**Parameters**: `tokenId`, `side` (BUY/SELL), `amount` (USD to spend or tokens to sell), `orderType` (FOK/FAK)

#### polymarket_create_order
**Purpose**: Place limit order to buy/sell YES/NO tokens

**Parameters**: `tokenId`, `side` (BUY/SELL), `price` (0.01–0.99), `size`, `orderType` (GTC/GTD), `expiration` (if GTD)

## Portfolio Analytics

### unified_portfolio_analysis
**Purpose**: Complete multi-chain, multi-venue portfolio snapshot
- Solana token balances + Jupiter limit orders
- EVM balances (multiple chains)
- 1inch limit orders
- Hyperliquid perps, spot balances, orders, TWAP fills
- Ostium positions
- Polymarket open orders; USDC approvals

**Parameters**: `evm_wallet_address`, `solana_wallet_address`

### moralis_evm_get_wallet_profitability
**Purpose**: Tokenized P&L overview over time

**Parameters**: `address`, `days` ("all", "7", "30", "60", "90"), `chain`, `token` filter

### solana_calculate_pnl
**Purpose**: Realized P&L in SOL for a specific token

**Parameters**: `wallet_address`, `token_address`

## Order Management

### EVM Limit Orders

#### evm_place_limit_order
**Purpose**: Create EVM limit orders (non-blocking; tokens transfer only upon execution)

**Parameters**: `fromAddress`, `network` (1, 8453, 42161, 137), `makerAssetAddress`, `takerAssetAddress`, `makerAmount`, `takerAmount`, `expiresInSeconds`

#### evm_cancel_limit_order
**Purpose**: Cancel a specific EVM limit order

**Parameters**: `orderHash`, `network`, `makerTraits`

## Cross-Chain Bridging

### relay_bridge_tokens_cross_chain
**Purpose**: Execute bridging; completes when tool returns success

**Parameters**: `srcChainId`, `dstChainId`, `srcTokenAddress`, `dstTokenAddress`, `amount`, `fromAddress`, `recipient`, `slippageTolerance`

### relay_get_crosschain_quote
**Purpose**: Get cross-chain bridge quote (rates, fees, output estimates)

**Parameters**: `srcChainId`, `dstChainId`, `srcTokenAddress`, `dstTokenAddress`, `amount`, `fromAddress`, `recipient` (optional), `slippageTolerance` (bps)

## Pigeon Code (Automation)

### create_automated_task
**Purpose**: Create background scripts to monitor or act on signals

**Parameters**: 
- `description`: What you want monitored or automated
- `interval_minutes`: For recurring execution (min 1 minute)
- `delay_minutes`: For one-time delayed execution
- `duration_minutes`: How long to run (empty for indefinite)
- `run_at_local_time`: Daily schedule in HH:MM format (e.g., "09:00")
- `run_timezone`: IANA timezone (e.g., "America/New_York", "Europe/London")

### list_automated_tasks
**Purpose**: View created scripts, next run time, execution history, status

### get_automation_source_code
**Purpose**: Retrieve the generated TypeScript source code for an active script

**Parameters**: `automation_id`

**Returns**: Full source code, schedule configuration, execution stats, editor link

### get_automation_execution_history
**Purpose**: Paginated execution history for debugging and monitoring

**Parameters**: `automation_id`, `page`, `page_size`

**Returns**: Execution timestamps, success/failure status, alerts sent, errors, output data

### request_automation_edit
**Purpose**: Request AI-powered changes to an existing script

**Parameters**: 
- `automation_id`: Script to edit
- `feedback`: Detailed instructions for changes
- `history_limit`: Recent executions to include as context
- `preview_only`: Set to true to preview without saving

### cancel_automated_task
**Purpose**: Delete an existing script

**Parameters**: `task_id`

## Technical Analysis (TAAPI)

### taapi_get_indicator
**Purpose**: Get technical indicators for any trading pair

**Supported Indicators**:
- RSI (Relative Strength Index)
- MACD (Moving Average Convergence Divergence)
- Bollinger Bands
- EMA, SMA (Moving Averages)
- ADX, ATR, Stochastic, and 50+ more

**Parameters**: `indicator`, `exchange`, `symbol`, `interval`, `optionalParams`

**Exchanges**: Binance, Binance Futures, Bybit, Coinbase, Gate.io, Stocks

**Example**: "What's the RSI for BTC on the 4h chart?"

## Utilities

### batch_transfer
**Purpose**: Send multiple ERC-20/native transfers in one operation

**Parameters**: `transfers[]` (tokenAddress optional for native), `network`

### wrap_eth / unwrap_weth
**Purpose**: Convert ETH to WETH and vice versa

**Parameters**: `amount`, `network`

### sleep
**Purpose**: Wait between steps (15–300 seconds) for finality, rate limits, or backoff

## Token Launch & Deployment

### solana_launch_pumpfun_token
**Purpose**: Launch a token on Pump.fun with 0.001 SOL initial buy

**Parameters**: `name` (max 12), `symbol` (max 8), `description`, `imageUrl`, `amount`, `twitter`, `telegram`, `website`

### deploy_clanker_token (Base)
**Purpose**: Deploy an ERC-20 token using Clanker on Base, with IPFS and 25% interface rewards to Pigeon

**Parameters**: `name`, `symbol`, `description`, `imageUrl`, `twitter`, `telegram`, `website`, `initialMarketCap` (ETH), `devBuyAmount` (ETH)

## Messaging, Identity, and Security

### pigeon_clear_message_history
**Purpose**: Reset conversation context completely (irreversible)

### pigeon_toggle_follow_up_messages
**Purpose**: Enable/disable status updates during long operations

### pigeon_get_setup_totp_url / pigeon_finish_totp_setup / pigeon_remove_totp
**Purpose**: TOTP 2FA for sensitive actions

### Identity Lookups
- `pigeon_get_addresses_for_phone_number`
- `pigeon_get_addresses_for_telegram_username`
- `pigeon_get_addresses_for_farcaster_username`

### Telegram Group Tools
- `pigeon_get_telegram_messages`
- `pigeon_get_telegram_group_info`
- `pigeon_get_telegram_group_users`
- `pigeon_get_telegram_group_referrer`

### Referrals & Refcodes
- `pigeon_set_ref_code`: Create or set your custom refcode for sharing
- `pigeon_use_ref_code`: Apply a refcode to your account to link to a referrer
- `pigeon_get_paid_referral_fees`: View paid referral earnings
- `pigeon_get_unpaid_referral_fees`: View pending referral earnings

**Two Referral Tiers**:
- **Group (30%)**: Add Pigeon to a Telegram group → earn 30% of 1% trading fees from that group
- **Solo (20%/10%)**: Share your refcode → you get 20% of their fees, they get 10% cashback

Daily payouts at noon LA time.

## Memory Management

- `list_memories`: View stored memories
- `delete_memories`: Remove specific memories by ID
- `clear_all_memories`: Reset all stored memories

## Web Search

### web_search_duckduckgo
**Purpose**: Non-market or general research; optionally fetch page content

**Use**: When specialized tools do not apply

## Image & Charts

### pigeon_analyze_image
**Purpose**: Analyze images sent in chat (charts, screenshots, etc.)

**Use**: Get AI analysis of trading charts, portfolio screenshots, or any image

### pigeon_generate_chart
**Purpose**: Generate price charts for tokens

**Parameters**: `token`, `timeframe`, `indicators`

## Multi-Tool Operations

### multi_tool_use.parallel
**Purpose**: Run compatible tools in parallel to save time

**Use**: Portfolio aggregation across multiple sources concurrently
