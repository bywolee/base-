## 📖 Table of Contents

- [Overview](#-overview)
- [Why Base](#-why-base)
- [Base History](#-base-history)
- [Base Architecture](#-base-architecture)
- [Unified Stack](#-unified-stack)
- [Getting Started](#-getting-started)
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Environment Setup](#-environment-setup)
- [Network Configuration](#-network-configuration)
- [Connecting to Base](#-connecting-to-base)
- [Base Mainnet Details](#-base-mainnet-details)
- [Base Testnet Details](#-base-testnet-details)
- [Gas Fee Optimization](#-gas-fee-optimization)
- [Base Gas Model](#-base-gas-model)
- [L1 vs L2 Fees](#-l1-vs-l2-fees)
- [EIP-1559 on Base](#-eip-1559-on-base)
- [Security](#-security)
- [Contract Architecture](#-contract-architecture)
- [Smart Contract Overview](#-smart-contract-overview)
- [Deployment on Base](#-deployment-on-base)
- [Bridging to Base](#-bridging-to-base)
- [Base Bridge](#-base-bridge)
- [Third Party Bridges](#-third-party-bridges)
- [Cross Chain Messaging](#-cross-chain-messaging)
- [Token Standards](#-token-standards)
- [ERC-20 on Base](#-erc-20-on-base)
- [ERC-721 on Base](#-erc-721-on-base)
- [ERC-1155 on Base](#-erc-1155-on-base)
- [Access Control](#-access-control)
- [Role Management](#-role-management)
- [Ownership](#-ownership)
- [Pausable Contracts](#-pausable-contracts)
- [Reentrancy Protection](#-reentrancy-protection)
- [Integer Overflow Protection](#-integer-overflow-protection)
- [Flash Loan Protection](#-flash-loan-protection)
- [Oracle Integration](#-oracle-integration)
- [Chainlink on Base](#-chainlink-on-base)
- [Pyth Network on Base](#-pyth-network-on-base)
- [IPFS Integration](#-ipfs-integration)
- [Metadata Storage](#-metadata-storage)
- [Event Logging](#-event-logging)
- [Error Handling](#-error-handling)
- [Custom Errors](#-custom-errors)
- [Testing on Base](#-testing-on-base)
- [Unit Tests](#-unit-tests)
- [Integration Tests](#-integration-tests)
- [Fuzzing](#-fuzzing)
- [Code Coverage](#-code-coverage)
- [Audits](#-audits)
- [Known Issues](#-known-issues)
- [Bug Bounty](#-bug-bounty)
- [Upgradability](#-upgradability)
- [Proxy Pattern](#-proxy-pattern)
- [Storage Layout](#-storage-layout)
- [ABI](#-abi)
- [Interface Design](#-interface-design)
- [Modifiers](#-modifiers)
- [Libraries](#-libraries)
- [Multi-Sig on Base](#-multi-sig-on-base)
- [Timelock](#-timelock)
- [Governance on Base](#-governance-on-base)
- [Voting](#-voting)
- [Staking on Base](#-staking-on-base)
- [Rewards](#-rewards)
- [Liquidity on Base](#-liquidity-on-base)
- [Aerodrome Finance](#-aerodrome-finance)
- [Uniswap on Base](#-uniswap-on-base)
- [DEX Integration](#-dex-integration)
- [Layer 2 Benefits](#-layer-2-benefits)
- [Base Mainnet Addresses](#-base-mainnet-addresses)
- [Base Testnet Addresses](#-base-testnet-addresses)
- [Contract Verification](#-contract-verification)
- [Basescan](#-basescan)
- [Frontend Integration](#-frontend-integration)
- [OnchainKit](#-onchainkit)
- [ethers.js on Base](#-ethersjs-on-base)
- [viem on Base](#-viem-on-base)
- [wagmi on Base](#-wagmi-on-base)
- [WalletConnect](#-walletconnect)
- [Coinbase Wallet and Base App](#-coinbase-wallet-and-base-app)
- [MetaMask on Base](#-metamask-on-base)
- [Basenames](#-basenames)
- [Base Name Service](#-base-name-service)
- [Transaction Handling](#-transaction-handling)
- [Nonce Management](#-nonce-management)
- [Gas Estimation on Base](#-gas-estimation-on-base)
- [Signature Verification](#-signature-verification)
- [EIP-712 on Base](#-eip-712-on-base)
- [EIP-2612 Permits](#-eip-2612-permits)
- [Batch Transfers](#-batch-transfers)
- [Allowances](#-allowances)
- [Fee Structure](#-fee-structure)
- [Treasury](#-treasury)
- [Token Vesting](#-token-vesting)
- [Emergency Withdraw](#-emergency-withdraw)
- [Monitoring on Base](#-monitoring-on-base)
- [Changelog](#-changelog)
- [Contributing](#-contributing)
- [License](#-license)

## 🌐 Overview
A decentralized protocol deployed on Base — Coinbase's Ethereum Layer 2 network designed to bring the next billion users onchain. Built for low fees, high speed, and full EVM compatibility.

## 💡 Why Base
Base offers near-instant finality, fees far cheaper than Ethereum mainnet, and seamless access to Coinbase's ecosystem of millions of users. It is the largest L2 by daily active addresses with over 1 million users daily.

## 📜 Base History
Base launched on mainnet in August 2023, incubated by Coinbase. It was originally built on Optimism's OP Stack and was part of the Superchain ecosystem. On February 18, 2026, Base announced a transition to its own proprietary unified stack for greater autonomy and faster development.

## 🏛 Base Architecture
Base is an Ethereum Layer 2 using optimistic rollup technology. Transactions are executed on Base and batched to Ethereum mainnet for settlement, inheriting Ethereum's security. Base is transitioning from the OP Stack to its own unified, in-house stack built on open-source components like Reth.

## 🔧 Unified Stack
On February 18, 2026, Base confirmed a move away from the OP Stack to its own proprietary unified stack. All infrastructure is being consolidated into a single repository (`base/base`) built on open-source components like Reth. This gives Base full control over its roadmap and enables roughly six major upgrades per year — doubling its previous development pace.

## 🚀 Getting Started
Clone the repo, install dependencies, configure your `.env`, and deploy to Base. All contracts are EVM-compatible and work with standard Solidity tooling like Hardhat and Foundry.

## ✅ Prerequisites
Requires Node.js v18+, npm or yarn, and a wallet funded with ETH on Base. Hardhat or Foundry recommended. ETH can be bridged from Ethereum mainnet via the official Base Bridge.

## 📦 Installation
```bash
git clone https://github.com/your-repo.git
cd your-repo
npm install
```

## 🔧 Environment Setup
```bash
cp .env.example .env
```
Required variables: `PRIVATE_KEY`, `BASE_RPC_URL`, `BASESCAN_API_KEY`.


## 🌍 Network Configuration
Add Base to `hardhat.config.js`:
```js
base: {
  url: process.env.BASE_RPC_URL,
  chainId: 8453,
  accounts: [process.env.PRIVATE_KEY]
},
baseSepolia: {
  url: "https://sepolia.base.org",
  chainId: 84532,
  accounts: [process.env.PRIVATE_KEY]
}
```

## 🔗 Connecting to Base
Use the public RPC `https://mainnet.base.org` or a provider like Alchemy or QuickNode for higher rate limits and reliability.

## 📡 Base Mainnet Details
- **Chain ID:** 8453
- **RPC:** https://mainnet.base.org
- **Explorer:** https://basescan.org
- **Native Token:** ETH

## 🧪 Base Testnet Details
- **Chain ID:** 84532
- **Network:** Base Sepolia
- **RPC:** https://sepolia.base.org
- **Faucet:** https://faucet.quicknode.com/base/sepolia

## ⛽ Gas Fee Optimization
Base fees are a fraction of Ethereum mainnet. Uses packed structs, batched calls, and memory caching to further reduce on-chain costs. Off-chain computation minimizes unnecessary execution.

## 📊 Base Gas Model
Base uses a two-component fee model: L2 execution fee and L1 data fee. The L1 data fee covers the cost of posting transaction data to Ethereum and is typically the larger component.

## 💸 L1 vs L2 Fees
L2 execution fees on Base are ~10-100x cheaper than Ethereum mainnet. L1 data fees depend on calldata size and Ethereum gas prices at the time of batch submission.

## 🔥 EIP-1559 on Base
Base implements EIP-1559, meaning transactions include a base fee (burned) and optional priority fee (tip). Base fees adjust dynamically based on network demand.

## 🔒 Security
Follows checks-effects-interactions pattern. Access control via OpenZeppelin roles. Contracts tested with edge-case fuzzing and reviewed against Base-specific attack vectors.

## 🏗 Contract Architecture
Modular design with separated core logic, storage, and interfaces. Shallow inheritance keeps contracts readable and auditable. Deployed and verified on Basescan.

## 📄 Smart Contract Overview
Core contracts handle protocol logic, token management, and access control. All contracts are written in Solidity ^0.8.20 and optimized for Base's gas model.

## 🚀 Deployment on Base
```bash
npx hardhat deploy --network base
```
Verify automatically with:
```bash
npx hardhat verify --network base <CONTRACT_ADDRESS>
```

## 🌉 Bridging to Base
ETH and ERC-20 tokens can be bridged from Ethereum mainnet to Base using the official Base Bridge or third-party solutions. Withdrawals to L1 take ~7 days via the canonical bridge.

## 🔁 Base Bridge
The official bridge at https://bridge.base.org supports ETH and standard ERC-20 deposits and withdrawals. Deposits are fast (~1-2 mins). Withdrawals require a 7-day challenge period.

## 🔀 Third Party Bridges
Faster bridging available via Across, Stargate, Hop Protocol, and Relay. These use liquidity pools to offer instant withdrawals bypassing the 7-day challenge window.

## 📨 Cross Chain Messaging
Uses the OP Stack's native cross-domain messenger for L1↔L2 communication. Third-party options include LayerZero and Axelar for broader cross-chain support.

## 🪙 Token Standard
All tokens follow OpenZeppelin's battle-tested implementations. Custom extensions are minimal and clearly documented to reduce audit surface area.

## 💰 ERC-20 on Base
Standard ERC-20 tokens deploy and operate identically to Ethereum mainnet on Base. Transfer costs are significantly lower, enabling micro-transactions at scale.

## 🖼 ERC-721 on Base
NFTs on Base benefit from low mint and transfer costs. Base has a thriving NFT ecosystem with projects like Zora, OpenSea, and native Base collections.

## 🎮 ERC-1155 on Base
Multi-token standard ideal for gaming and batch operations. Lower fees on Base make ERC-1155 batch transfers economically viable for high-frequency use cases.

## 🛡 Access Control
Uses OpenZeppelin's `AccessControl` for granular role-based permissions. Roles are defined at deployment and can be granted or revoked by admins.

## 👥 Role Management
Roles include `ADMIN_ROLE`, `MINTER_ROLE`, and `PAUSER_ROLE`. Each role controls specific contract functions, minimizing risk of privilege escalation.

## 👤 Ownership
Ownership managed via OpenZeppelin `Ownable`. For production, ownership is transferred to a multi-sig wallet immediately after deployment on Base.

## ⏸ Pausable Contracts
Critical functions can be paused in emergencies using OpenZeppelin `Pausable`. Only addresses with `PAUSER_ROLE` can trigger a pause on Base mainnet.

## 🔄 Reentrancy Protection
All state-changing external calls follow checks-effects-interactions. `ReentrancyGuard` from OpenZeppelin is applied to sensitive functions as an additional layer.

## 🔢 Integer Overflow Protection
Solidity ^0.8.x has built-in overflow protection. All arithmetic is safe by default. `unchecked` blocks are only used in gas-critical loops with verified bounds.

## ⚡ Flash Loan Protection
Price-sensitive functions use time-weighted average prices (TWAP) and block-based checks to prevent flash loan manipulation on Base's DEX ecosystem.

## 🔮 Oracle Integration
External price data is fetched via Chainlink and Pyth Network oracles deployed on Base. Staleness checks ensure data is not older than a defined threshold.

## 🔗 Chainlink on Base
Chainlink Price Feeds are live on Base mainnet. Supported pairs include ETH/USD, BTC/USD, and USDC/USD. Aggregator addresses available at docs.chain.link.

## 📈 Price Feeds on Base
Both Chainlink and Pyth provide low-latency price feeds on Base. Pyth offers sub-second updates suitable for high-frequency DeFi protocols.

## 📁 IPFS Integration
Off-chain metadata and assets are stored on IPFS via Pinata or NFT.Storage. Only content hashes are stored on-chain to minimize gas costs on Base.

## 🗄 Metadata Storage
Token metadata follows the ERC-721/1155 metadata standard. URIs point to IPFS-hosted JSON files containing name, description, image, and attributes.

## 📋 Event Logging
All significant state changes emit events. Events are indexed for efficient filtering on Base via Basescan or The Graph subgraphs deployed on Base.

## ❌ Error Handling
Reverts use descriptive messages for clarity. Custom errors are preferred over string reverts for gas efficiency. This is especially important on Base where high-frequency contract calls make per-call gas savings compound quickly.

## 🚨 Custom Errors
```solidity
error Unauthorized(address caller);
error InsufficientBalance(uint256 required, uint256 available);
error InvalidAddress();
error ContractPaused();
```
Custom errors save ~50 gas per revert over string messages.

## 🧪 Testing on Base
Tests run locally via Hardhat Network with Base fork support. Use the `--fork` flag with Base mainnet RPC to test against live state including Aerodrome liquidity pools and Chainlink feeds.
```bash
npx hardhat test --network hardhat
```
## 🔬 Unit Tests
Each contract function has isolated unit tests covering happy paths, edge cases, and revert conditions. Run all tests with:
```bash
npx hardhat test
```
## 🔗 Integration Tests
Integration tests simulate full user flows across multiple contracts using a forked Base mainnet. Covers bridging, DEX swaps on Aerodrome, staking, and governance scenarios end-to-end with real on-chain state.

## 🎲 Fuzzing
Foundry fuzzing (`forge test --fuzz-runs 10000`) discovers edge cases. Invariant tests verify that core protocol properties like solvency and correct accounting hold under arbitrary user inputs.
