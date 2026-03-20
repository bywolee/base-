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
