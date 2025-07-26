# FundMe Contract

[![Solidity](https://img.shields.io/badge/Solidity-0.8.19-blue)](https://soliditylang.org/)
[![Foundry](https://img.shields.io/badge/Framework-Foundry-orange)](https://getfoundry.sh/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A decentralized funding contract that accepts ETH contributions with a minimum USD threshold, powered by Chainlink Price Feeds.

## Contract Address (Sepolia Testnet)
sepolia-eth: [`0xC3f5e8Eb8aAb1fEA59D3aF9C929A29FcEE98B7D6`](https://sepolia.etherscan.io/address/0xC3f5e8Eb8aAb1fEA59D3aF9C929A29FcEE98B7D6)

sepolia-zksync: [0x017577610aCD41303AD7A83fe819a7f976F8Cc13](https://sepolia.explorer.zksync.io/address/0x017577610aCD41303AD7A83fe819a7f976F8Cc13#contract)

## Features
- Accepts ETH contributions with a minimum $5 USD equivalent
- Tracks funders and their contributions
- Owner-only withdrawal functionality
- Gas-optimized withdrawal function (`cheaperWithdraw`)
- Chainlink Price Feed integration for real-time ETH/USD conversion
- Immutable owner and price feed addresses

## Technical Documentation

### Contracts

#### `FundMe.sol`
Main contract that handles:
- Accepting and tracking funds
- Enforcing minimum contribution ($5 USD)
- Owner-restricted withdrawals
- Price feed interactions

Key functions:
- `fund()` - Accepts ETH contributions
- `withdraw()`/`cheaperWithdraw()` - Owner withdrawal functions
- View functions for contract state

#### `PriceConverter.sol`
Library that handles:
- ETH/USD price conversions
- Interface with Chainlink AggregatorV3

### Development Setup

#### Prerequisites
- [Foundry](https://getfoundry.sh/) (recommended version: nightly)

#### Installation
```bash
git clone https://github.com/williamhjc/foundry-found-me
cd fundme-foundry
```

#### Environment Variables

Create a .env file:

```
RPC_URL=http://127.0.0.1:8545
SEPOLIA_RPC_URL=https://sepolia.infura.io/v3/YOUR_KEY
PRIVATE_KEY=0xYourPrivateKey
ETHERSCAN_API_KEY=YourEtherscanKey
```

#### deploy

```bash
make install
make test

deployed on sepolia testnet：make deploy ARGS="--network sepolia"
deployed on anvil testnet（default）：make deploy
```