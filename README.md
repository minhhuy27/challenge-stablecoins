# Stablecoins Challenge (SpeedRunEthereum)

This project is a implementation of a decentralized, algorithmic stablecoin system pegged to the USD. It is built using the **Scaffold-ETH 2** framework and allows users to collateralize ETH to mint stablecoins (MyUSD), manage debt positions, and participate in ecosystem stability through liquidations and interest rate mechanisms.

This repository serves as a submission for the **SpeedRunEthereum Stablecoin Challenge**.

## 🏗 Project Architecture

The system is composed of several interacting smart contracts:

- **MyUSDEngine.sol**: The core logic handling collateral deposits (ETH), minting/burning MyUSD, and managing solvency (health factor).
- **MyUSD.sol**: The ERC20 stablecoin token.
- **MyUSDStaking.sol**: Allows users to stake MyUSD to earn yield, creating buy pressure.
- **RateController.sol**: Adjusts borrow and savings rates to maintain the $1 peg.
- **DEX.sol**: A simple AMM for swapping ETH <> MyUSD to simulate market activity.
- **Oracle.sol**: Provides price feeds for the system.

## ✨ Key Features

- **Over-collateralization**: Users must maintain a Collateral Ratio > 150%.
- **Algorithmic Peg Maintenance**: Uses dynamic Borrow Rates and Savings Rates to control supply and demand.
- **Share-based Interest**: Efficient gas-optimized interest accrual system.
- **Liquidations**: Incentivized mechanism for third parties to liquidate unsafe positions to prevent bad debt.
- **Market Simulation**: Scripts to simulate market participants and automated rate controllers.

## 🚀 Quick Start

Follow these steps to set up the environment and run the project locally.

### Prerequisites

- [Node.js](https://nodejs.org/) (>= 20.18.3)
- [Yarn](https://yarnpkg.com/) (v1 or v2+)
- [Git](https://git-scm.com/)

### 1. Installation

Clone the repository and install dependencies:

```bash
git clone https://github.com/minhhuy27/challenge-stablecoins.git
cd challenge-stablecoins
yarn install

```

### 2. Start the Local Blockchain

In the first terminal, start the local Hardhat network:

```bash
yarn chain

```

### 3. Deploy Smart Contracts

In a second terminal, deploy the contracts to the local network:

```bash
yarn deploy

```

*Note: If you make changes to the contracts, run `yarn deploy --reset` to redeploy.*

### 4. Start the Frontend Application

In a third terminal, launch the Next.js frontend:

```bash
yarn start

```

Open your browser and navigate to `http://localhost:3000` to interact with the application.

---

## 🧪 Testing & Simulation

This project includes simulation scripts to demonstrate how the stablecoin maintains its peg under market pressure.

### Running Market Simulation

To simulate users depositing collateral, minting, selling, and repaying debt (creating volatility):

```bash
yarn simulate

```

### Running the Rate Controller

To run the "Central Bank" bot that automatically adjusts interest rates to stabilize the price:

```bash
yarn interest-rate-controller

```

### Running Unit Tests

To verify the logic of the smart contracts:

```bash
yarn test

```

## 📚 User Guide (Frontend)

1. **Faucet**: Grab some test ETH from the faucet in the top right corner.
2. **Deposit**: Go to the "Collateral" tab and deposit ETH.
3. **Mint**: Mint MyUSD against your collateral (ensure your Health Factor stays above 150%).
4. **Swap**: Use the internal DEX to swap MyUSD for ETH (simulating selling pressure).
5. **Rate Controls**: Manually adjust Borrow/Savings rates to see how they affect the peg (in the "Debug Contracts" or "Rate Controls" section).
6. **Liquidate**: Use a second account to liquidate positions that fall below the required collateral ratio.

## 🛠 Tech Stack

* **Solidity**: Smart Contracts.
* **Hardhat**: Development environment, testing, and deployment.
* **Next.js**: Frontend framework.
* **RainbowKit / Wagmi / Viem**: Wallet connection and blockchain interaction.
* **TypeScript**: Static typing.

## Live Demo

* **Live App (Vercel):** https://huy-challenge-stablecoins-60ljh15s2-huys-projects-d7f14f3b.vercel.app
* **Contract Address (Sepolia):** MyUSDEngine: https://sepolia.etherscan.io/address/0x5CAc94CBF6F5F7bCe3CbFD3066deC58815e53d1f