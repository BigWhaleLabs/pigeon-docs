# Security & Wallets

Pigeon prioritizes security while maintaining ease of use. Understanding how your assets are protected and managed is crucial for confident trading.

## Wallet Technology

### Privy (Stripe) MPC (Multi-Party Computation)

- **Distributed Keys**: Your private key is split across multiple secure parties
- **No Single Point of Failure**: No one entity (including Pigeon) has access to your complete private key
- **Secure Computation**: Transactions are signed through cryptographic protocols without key reconstruction
- **Self-Custody**: Wallets are fully self-custodial and exportable
- **Industry Standard**: Privy (Stripe) is a leading Web3 infrastructure provider trusted by major protocols

### Wallet Generation

- **Automatic**: Wallets are generated automatically when you first interact with Pigeon
- **Platform Specific**: Each platform (Telegram, WhatsApp, Discord, Messenger, Farcaster, XMTP, Base App, SMS) creates separate wallets
- **Multi-Chain**: You receive both EVM and Solana addresses
- **Deterministic**: Your wallets are consistent and recoverable

## Private Key Management

### Key Export Availability

| Platform  | Key Export           | Export URL                 |
| --------- | -------------------- | -------------------------- |
| Telegram  | ✅ Available         | https://pigeon.trade/privy |
| WhatsApp  | ✅ Available         | https://pigeon.trade/privy |
| SMS       | ✅ Available         | https://pigeon.trade/privy |
| Discord   | ❌ Not yet supported | -                          |
| Farcaster | ❌ Not yet supported | -                          |
| Messenger | ❌ Not yet supported | -                          |
| XMTP      | ❌ Not yet supported | -                          |
| Base App  | ❌ Not yet supported | -                          |

### Self-Custody Options

- **Export Process**: Visit the export URL and follow authentication steps
- **Standard Formats**: Keys exported in standard wallet formats (seed phrase, private key)
- **Import to Wallets**: Compatible with MetaMask, Phantom, and other popular wallets
- **Backup Responsibility**: Once exported, you're responsible for secure storage

## Security Protocols

### Transaction Safety

- **Contract Address Verification**: Pigeon always displays and confirms token contract addresses
- **Scam Protection**: Built-in verification against known malicious contracts
- **Amount Confirmation**: Clear display of exact amounts and fees before execution
- **Explorer Links**: Every transaction includes a blockchain explorer link for verification

### Execution Safeguards

- **Approval Required**: Explicit user confirmation before any trade execution
- **Parameter Validation**: All inputs are validated before submission
- **Error Handling**: Graceful handling of failed transactions with clear explanations
- **Retry Logic**: Smart retry mechanisms for network issues

### Access Control

- **Platform Isolation**: Accounts on different platforms are completely separate
- **Session Management**: Secure session handling across messaging platforms
- **Rate Limiting**: Protection against spam and abuse
- **TOTP Support**: Optional two-factor authentication for additional security

## Best Practices

### Wallet Security

1. **Keep Platforms Separate**: Don't rely on cross-platform account linking
2. **Export Keys**: Use the export feature for important accounts
3. **Backup Securely**: Store exported keys using proper backup practices
4. **Monitor Activity**: Regularly check your transaction history
5. **Use Test Amounts**: Start with small amounts when learning

### Operational Security

1. **Verify Addresses**: Always double-check contract addresses before confirming trades
2. **Check Explorers**: Verify transactions using blockchain explorers
3. **Monitor Balances**: Keep track of your balances across networks
4. **Stay Informed**: Follow security announcements and updates
5. **Report Issues**: Contact support immediately if you notice suspicious activity

### Platform-Specific Considerations

#### Telegram

- **Most Features**: Full access to key export and all trading features
- **Group Security**: Be cautious in public groups
- **Bot Security**: Only interact with the official @pigeon_trade_bot

#### Discord/Farcaster

- **Limited Export**: Key export not yet available
- **Consider Migration**: For serious trading, consider Telegram/WhatsApp
- **Backup Strategy**: Plan for potential key export in the future

#### SMS/WhatsApp

- **Phone Security**: Ensure your phone number is secure
- **SIM Protection**: Use SIM locks and carrier security features
- **Key Export**: Take advantage of the available key export feature

## Funding Security

### Funding URLs

- **Unique Addresses**: Each user gets unique funding URLs
- **No Shorteners**: Always use the full https://pigeon.trade/[address] format
- **Verification**: The funding page displays your exact wallet address
- **Multiple Networks**: Separate addresses for EVM and Solana networks

### Safe Funding Practices

1. **Verify Addresses**: Cross-check addresses shown in Pigeon with funding pages
2. **Start Small**: Test with small amounts first
3. **Network Matching**: Ensure you're sending to the correct network
4. **Gas Reserves**: Always maintain gas for transactions
5. **Regular Monitoring**: Check balances after funding

## Incident Response

### If You Suspect Compromise

1. **Stop Trading**: Immediately cease all trading activity
2. **Export Keys**: If available, export your keys to a secure wallet
3. **Transfer Funds**: Move assets to a known secure wallet
4. **Contact Support**: Reach out via https://t.me/pigeon_trade_support
5. **Document Everything**: Keep records of suspicious activity

### If You Lose Access

1. **Platform Recovery**: Use platform-specific account recovery
2. **Key Export**: If previously exported, use your backup keys
3. **Support Contact**: Reach out for assistance with account recovery
4. **New Account**: As a last resort, create a new account on a different platform

## Compliance & Regulations

### KYC/AML

- **No KYC Required**: Pigeon doesn't require identity verification
- **Platform Compliance**: Some integrated venues may have their own requirements
- **Jurisdiction Awareness**: Be aware of your local trading regulations
- **Tax Responsibility**: Users are responsible for tax compliance

### Data Privacy

- **Minimal Data**: Pigeon stores only necessary operational data
- **Platform Data**: Messaging platforms have their own data policies
- **Transaction Privacy**: Blockchain transactions are public by nature
- **Export Rights**: You can export or delete your data on request

Remember: While Pigeon provides robust security, you are ultimately responsible for your assets. Always follow best practices and never trade with funds you can't afford to lose.
