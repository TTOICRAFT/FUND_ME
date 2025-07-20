# Foundry Fund Me

## About

This is a minimal smart contract project that allows users to fund the contract owner with ETH donations, priced in USD. Donations must meet a minimum USD threshold or they are rejected. The contract uses a Chainlink price feed to convert ETH to USD and keeps track of all donors — useful if rewards are ever introduced.

---

## 📦 Getting Started

### ✅ Requirements

- `git`
  Run `git --version` and you should see output like: `git version x.x.x`
- `foundry`
  Run `forge --version` and you should see output like: `forge 0.2.0 (816e00b 2023-03-16T00:05:26.396218Z)`

---

### ⚡ Quickstart

```bash
git clone https://github.com/TTOICRAFT/FUND_ME
cd FUND_ME
make
```

---

### 🌐 Optional Gitpod

If you don't want to run this repo locally, you can work with it in Gitpod. In that case, skip the cloning step.

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/Cyfrin/foundry-fund-me-cu)

---

## 🚀 Usage

### 🛠 Deploy

```bash
forge script script/DeployFundMe.s.sol
```

---

## ✅ Testing

We discuss four tiers of testing:

- Unit
- Integration
- Forked
- Staging

This repo covers **Unit** and **Forked** testing.

Run all tests:

```bash
forge test
```

Run a specific test:

```bash
forge test --match-test testFunctionName
```

Run forked test:

```bash
forge test --fork-url $SEPOLIA_RPC_URL
```

---

## 📈 Test Coverage

```bash
forge coverage
```

---

## 🌉 Local zkSync

To work with zkSync locally:

---

### Additional Requirements

- `foundry-zksync`
  Run `forge --version` and see something like `forge 0.0.2...`
- `npx` and `npm`
  Run `npm --version` and `npx --version` to confirm installation
- `docker`
  Run `docker --version` and `docker --info` to confirm daemon is running

---

### 🧪 Setup Local zkSync Node

```bash
npx zksync-cli dev config
```

> Select **In-memory node** and skip additional modules.

Then start:

```bash
npx zksync-cli dev start
```

You should see output like:

```
In memory node started v0.1.0-alpha.22:
- zkSync Node (L2)
- Chain ID: 260
- RPC URL: http://127.0.0.1:8011
```

---

### 🚀 Deploy to Local zkSync Node

```bash
make deploy-zk
```

This will deploy a mock price feed and FundMe contract locally.

---

## 🌍 Deploy to Testnet or Mainnet

### Set Environment Variables

Add a `.env` file similar to `.env.example`:

```env
PRIVATE_KEY=your_private_key
SEPOLIA_RPC_URL=https://sepolia.example.com
ETHERSCAN_API_KEY=your_etherscan_key (optional)
```

**⚠️ Use a dev account — never a real wallet with funds.**

---

### 🔄 Get Testnet ETH

Use [https://faucets.chain.link](https://faucets.chain.link) to get testnet ETH.

---

### 🚀 Deploy Script

```bash
forge script script/DeployFundMe.s.sol \
  --rpc-url $SEPOLIA_RPC_URL \
  --private-key $PRIVATE_KEY \
  --broadcast \
  --verify \
  --etherscan-api-key $ETHERSCAN_API_KEY
```

---

## 🧩 Scripts

Interact with deployed contracts:

### Fund Contract

```bash
cast send <FUNDME_CONTRACT_ADDRESS> "fund()" \
  --value 0.1ether \
  --private-key <PRIVATE_KEY>
```

or

```bash
forge script script/Interactions.s.sol:FundFundMe \
  --rpc-url sepolia \
  --private-key $PRIVATE_KEY \
  --broadcast
```

### Withdraw

```bash
cast send <FUNDME_CONTRACT_ADDRESS> "withdraw()" \
  --private-key <PRIVATE_KEY>
```

or

```bash
forge script script/Interactions.s.sol:WithdrawFundMe \
  --rpc-url sepolia \
  --private-key $PRIVATE_KEY \
  --broadcast
```

---

## ⛽ Estimate Gas

```bash
forge snapshot
```

Check `.gas-snapshot` file for the output.

---

## 🧹 Formatting

To format code:

```bash
forge fmt
```

---

## 📌 Summary

This project demonstrates:

- Writing and deploying secure smart contracts using Foundry
- Using Chainlink price feeds
- Working with zkSync locally
- Deploying to Ethereum testnets
- Writing unit and forked tests

---

## 🙏 Thank You!

Big thanks to [Cyfrin](https://github.com/Cyfrin) and [Patrick Collins](https://github.com/PatrickAlphaC) for their content and tutorials.
# FUND_ME
