## SolChat: Multi-Chain WhatsApp Payment System

---

### Project Story

**SolChat** is a multi-chain WhatsApp payment system designed to make cryptocurrency as easy as sending a message. It replaces complex wallet addresses with familiar phone numbers, allowing users to send and receive crypto through WhatsApp while maintaining decentralized, cross-chain interoperability between Solana and Ethereum.

By combining the **Solana blockchain**, **Wormhole Bridge** and **WhatsApp** SolChat demonstrates real-world usability of **Cryptocurrency** for billions of WhatsApp users — without compromising decentralization or user sovereignty.

---

## Overview

SolChat provides:
- Phone number to wallet mapping on-chain
- WhatsApp integration for easy crypto transactions
- Solana-based payments with cross-chain compatibility via Wormhole
- Secure backend management with Twilio API integration
- Cypherpunk Values: Decentralized, permissionless, user-sovereign

**Core Idea:** A decentralized bridge between traditional messaging (WhatsApp) and on-chain finance.

---

## Key Features

- **Phone-as-Wallet**: Send/receive crypto using just a phone number.
- **Cross-Chain Bridge**: Transfer assets between Solana and Ethereum using Wormhole.
- **Check Balances**: View Solana and Ethereum wallet balances
- **WhatsApp Integration**: Execute transactions via Twilio sandbox.
- **Decentralized Registry**: On-chain phone number mapping.
- **Secure Custody**: Server-managed wallets with private key encryption.

---

## Architecture

```
┌─────────────┐      ┌──────────────┐       ┌─────────────────┐
│  WhatsApp   │ ───▶ |   Backend    │ ───▶ │  Solana Program │
│  (Twilio)   │      │ (Node.js)    │       │ (Phone Registry)│
└─────────────┘      └──────────────┘       └─────────────────┘
                          │
                          ▼
                 │- **Solana**: Primary settlement layer (Anchor Framework 0.30.1)

                               ├──────────▶ Wormhole Bridge ─────▶ Ethereum- **Ethereum**: Secondary chain for cross-chain compatibility

                               │- **Wormhole**: Cross-chain bridge protocol
                 
```

**Components:**
- **Solana Program**: On-chain phone registry (Anchor) (`program/src/lib.rs`) .
- **Backend Server**: Node.js with Express + Twilio  (`backend/whatsappServer.js`).
- **Bridge Handler**: Cross-chain operations (Wormhole) (`backend/crossChainHandler.js`) .
- **WhatsApp Handler**: Command parsing and message flow (`backend/whatsappHandler.js`).

---

## Prerequisites

| Tool | Version | Purpose |
|------|----------|----------|
| Node.js | 16+ | Backend runtime |
| npm | 8+ | Package manager |
| Rust | 1.75+ | Compile Solana program |
| Solana CLI | 1.18+ | Program deployment |
| Anchor CLI | 0.30.1 | Solana framework |
| Twilio | WhatsApp API | Communication layer |
| WSL (Windows) | Ubuntu 20.04+ | Linux environment |

---

## Setup & Installation

### 1. Clone Repository
```bash
git clone https://github.com/yourusername/solchat.git
cd solchat
```

### 2. Install Dependencies
```bash
npm install
cd backend && npm install
```

### 3. Configure Environment
```bash
cp backend/.env.example backend/.env
```
Edit `.env` with your Twilio, Solana, and Wormhole credentials.

**Example:**
```env
SOLANA_RPC_URL=https://api.devnet.solana.com
PROGRAM_ID=BZ5Z67xFRgyCaobqDnRw2p2NDPu8EoqMFwV55rENVsBR
TWILIO_ACCOUNT_SID=your_sid
TWILIO_AUTH_TOKEN=your_auth
TWILIO_WHATSAPP_NUMBER=your_twilio_whatsapp_number

PORT=3000
```

# Twilio WhatsApp Setup

## 1. Create Twilio Account
- Sign up at [Twilio Console](https://www.twilio.com/console)
- Navigate to **"Messaging" → "Try it out" → "Send a WhatsApp message"**

## 2. WhatsApp Sandbox Setup
- Get your sandbox WhatsApp number  
- Configure webhook URL: `https://your-domain.com/webhook`  
- For local development, use ngrok: `https://ngrok.com/`

## 3. Get Twilio Credentials
- Account SID and Auth Token from Twilio Console Dashboard  
- WhatsApp sandbox phone number

### 4. Start Backend
```bash
cd backend
npm run whatsapp
```

### 5. Set  Setup WhatsApp Webhook (for local development)

```bash
# Install ngrok globally
npm install -g ngrok

# Expose local server to internet
ngrok http 3000

# Copy the https URL and configure it in Twilio Console
# Webhook URL: https://your-ngrok-url.ngrok.io/webhook
```

## Smart Contract Setup

### 1. Install Solana & Anchor
```bash
sh -c "$(curl -sSfL https://release.solana.com/stable/install)"
cargo install --git https://github.com/coral-xyz/anchor avm --locked
avm install 0.30.1 && avm use 0.30.1
```

### 2. Build and Deploy
```bash
cd program
cargo build-sbf
solana program deploy target/deploy/solchat_solana.so --url devnet
```

Update `PROGRAM_ID` in `.env` and `Anchor.toml` with the new program ID.

---

## Usage via WhatsApp

Once Twilio is configured:
1. Join WhatsApp Sandbox via Twilio.
2. Send the following messages:
   - `register` → Creates your Solana & Ethereum wallets.
   - `balance` → Checks wallet balances.
   - `send 1 sol to +1234567890` → Sends SOL.
   - `bridge 1 sol to ethereum` → Cross-chain transfer.

---

## API Reference

### `POST /api/register`
Registers a user with phone number and wallet mapping.
```json
{
  "privateKeyHex": "0x...",
  "phone": "+1234567890"
}
```

### `POST /api/send`
Send tokens to another user.
```json
{
  "privateKeyHex": "0x...",
  "recipientPhone": "+1234567890",
  "amount": "0.01"
}
```

### `POST /webhook`
WhatsApp message webhook endpoint used by Twilio.

---

## Tech Stack

**Blockchain:** Solana (Anchor, Rust), Ethereum (Ethers.js)  
**Cross-Chain:** Wormhole SDK  
**Backend:** Node.js, Express, Twilio API, bs58, dotenv  
**Dev Tools:** ngrok, Anchor CLI, Solana CLI

---
## 🔍 Troubleshooting

Common issues and solutions based on development challenges encountered during SolChat's build.

---

### 🧩 Common Issues

**1. Anchor Build Errors (Invalid Base58 String)**  
Cause: Version mismatch between Anchor CLI and Solana tools.  
Solution: Ensure Anchor 0.30.1 is installed (avm use 0.30.1). Clear target and rebuild with anchor build.  
Prevention: Use cargo build-sbf as an alternative for faster builds.  

**2. Solana Program Not Found (Program Not on Chain)**  
Cause: Program not deployed or wrong program ID.  
Solution: Verify deployment with solana address -k target/deploy/solchat_solana-keypair.json. Update PROGRAM_ID in .env.  
Prevention: Test on devnet first; use anchor deploy --provider.cluster devnet.  

**3. RPC Connection Timeouts**  
Cause: Solana devnet congestion or rate limits.  
Solution: Switch RPC endpoints (e.g., to Helius or GenesysGo). Add retries in solanaService.js.  
Prevention: Monitor with solana validators and use paid RPCs for production.  

**4. WhatsApp Webhook Not Working**  
Cause: Incorrect ngrok URL or Twilio config.  
Solution: Expose port 3000 with ngrok http 3000, update Twilio webhook URL, and check logs.  
Prevention: Use HTTPS in production; verify with Twilio debugger.  

**5. Insufficient SOL Balance for Deployment/Transactions**  
Cause: Devnet account lacks funds.  
Solution: Fund with solana airdrop 2 (devnet only). For testnet, use faucets like https://faucet.solana.com/.  
Prevention: Keep devnet accounts topped up; monitor with solana balance.  

**6. Insufficient ETH Balance for Bridging/Transactions**
Cause: Sepolia testnet account lacks ETH for gas fees during bridging, deployments, or transactions.
Solution: Fund with Sepolia faucets like https://sepoliafaucet.com/ or https://faucet.quicknode.com/ethereum/sepolia. Request 0.1-0.5 ETH for testing.
Prevention: Monitor balance via https://sepolia.etherscan.io/; keep accounts topped up before bridging operations.

**7. Cross-Chain Bridge Failures (Wormhole VAA Issues)**  
Cause: Testnet delays (~30 minutes) or invalid tokens.  
Solution: Check Wormhole status at https://wormholescan.io/. Use USDC for reliable bridging.  
Prevention: Implemented progress callbacks and user notifications.  

**Debug Commands:**
```bash
# Check Solana CLI and Anchor versions
solana --version
anchor --version

# Check account balance and program status
solana balance
solana program show BZ5Z67xFRgyCaobqDnRw2p2NDPu8EoqMFwV55rENVsBR

# View deployed SolChat program
solana program show --programs

# Test Solana connection
solana cluster-version

# Verify IDL loading
node -e "const idl = require('./target/idl/solchat_solana.json'); console.log('IDL loaded:', idl.name);"

# Check pending bridges
cat backend/pending_bridges.json
```
---
**Project Structure**
```bash
SolChat/
├── backend/                 # Node.js/Express server for WhatsApp & Solana integration
│   ├── whatsappServer.js   # Main server and Twilio webhook handler
│   ├── whatsappHandler.js  # Message parsing and command execution
│   ├── solanaService.js    # Solana blockchain interactions (PDAs, transactions)
│   ├── crossChainHandler.js # Wormhole bridging and Jupiter swaps
│   ├── wormholeTokenBridge.js # Wormhole NTT integration
│   ├── testWhatsApp.js     # Local testing script (bypasses Twilio limits)
│   ├── testCrossChain.js   # Cross-chain functionality tests
│   ├── reregisterUsers.js  # User re-registration helper
│   ├── wallets/            # User wallet storage (phone-based PDAs)
│   ├── package.json        # Backend dependencies (Twilio, Solana libs)
│   ├── .env                # Environment variables (API keys, program IDs)
│   └── .env.example        # Template for secure config
├── program/                # Solana smart contract (Rust/Anchor)
│   ├── src/lib.rs          # PDA-based phone registry logic
│   ├── Cargo.toml          # Rust dependencies and metadata
│   └── Xargo.toml          # Cross-compilation config
├── target/                 # Build artifacts (generated)
│   ├── deploy/             # Deployment keypairs and binaries
│   ├── idl/                # Interface Definition Language (IDL)
│   └── types/              # TypeScript types from IDL
├── docs/                   # Documentation
│   ├── README.md           # Project overview and setup
│   └── setup/SETUP.md      # Detailed installation guide
├── .cargo/                 # Rust/Cargo configuration
├── Anchor.toml             # Anchor framework config
├── package.json            # Root dependencies (if any)
└── README.md               # This file
```

---

## Security

- Private keys encrypted at rest.
- Phone number hashed before on-chain storage.
- Custodial wallets for demo purposes.
- Production use should migrate to MPC or HSM-secured wallets.

---
## 🚀 Next Steps

Roadmap for evolving **SolChat** beyond the hackathon:

- **Mainnet Deployment:** Migrate from devnet to Solana mainnet with audited contracts and production RPCs.  
- **Non-Custodial Wallets:** Integrate MPC or WalletConnect for user-controlled keys, eliminating custodial risks.  
- **Enhanced Cross-Chain:** Add more chains (e.g., Polygon, BSC) via Wormhole; support native tokens beyond USDC.  
- **Advanced Features:** Transaction history via WhatsApp, recurring payments, and merchant integrations.  
- **Web Dashboard:** Build a React/Vue frontend for account management and transaction viewing.  
- **Monetization:** Introduce transaction fees (0.1–0.5%), premium subscriptions, or affiliate swaps via Jupiter.  
- **Jupiter Swap Restrictions:** Currently limited to established tokens due to liquidity pool requirements; new coins cannot be swapped.

---

## License

This project is licensed under the **MIT License**.

---

**SolChat** — Bridging decentralized finance and global communication, one message at a time.

