<div align="center">
  <img src="https://via.placeholder.com/900x180?text=SolChat:+Multi-Chain+WhatsApp+Payments" alt="SolChat Banner"/>
  
  <p>
    <a href="https://solana.com"><img src="https://img.shields.io/badge/Solana-Devnet-green?logo=solana" alt="Solana"/></a>
    <a href="#"><img src="https://img.shields.io/badge/Anchor-0.30.1-purple?logo=rust" alt="Anchor"/></a>
    <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue" alt="License"/></a>
    <a href="#"><img src="https://img.shields.io/badge/Node.js-16%2B-brightgreen?logo=node.js" alt="Node.js"/></a>
  </p>
</div>

---

## SolChat: Multi-Chain WhatsApp Payment System

**License:** MIT  •  **Blockchain:** Solana Devnet  •  **Framework:** Anchor 0.30.1  •  **Language:** Rust & Node.js

---

### Project Story

**SolChat** is a multi-chain WhatsApp payment system designed to make cryptocurrency as easy as sending a message. It replaces complex wallet addresses with familiar phone numbers, allowing users to send and receive crypto through WhatsApp while maintaining decentralized, cross-chain interoperability between Solana and Ethereum.

By combining the **Solana blockchain**, **Wormhole Bridge**, and **Jupiter DEX**, SolChat demonstrates real-world usability for billions of WhatsApp users — without compromising decentralization or user sovereignty.

---

## Overview

SolChat provides:
- Phone number to wallet mapping on-chain
- WhatsApp integration for easy crypto transactions
- Solana-based payments with cross-chain compatibility via Wormhole
- Token swaps using Jupiter DEX
- Secure backend management with Twilio API integration

**Core Idea:** A decentralized bridge between traditional messaging (WhatsApp) and on-chain finance.

---

## Key Features

- **Phone-as-Wallet**: Send/receive crypto using just a phone number.
- **Cross-Chain Bridge**: Transfer assets between Solana and Ethereum using Wormhole.
- **Token Swaps**: Swap SOL/USDC seamlessly with Jupiter aggregator.
- **WhatsApp Integration**: Execute transactions via Twilio sandbox.
- **Decentralized Registry**: On-chain phone number mapping.
- **Secure Custody**: Server-managed wallets with private key encryption.

---

## Architecture

```
┌─────────────┐      ┌──────────────┐      ┌─────────────────┐
│  WhatsApp   │ ───▶ │   Backend    │ ───▶ │  Solana Program │
│  (Twilio)   │      │ (Node.js)    │      │ (Phone Registry)│
└─────────────┘      └──────────────┘      └─────────────────┘
                          │
                          ▼
                 Wormhole ↔ Ethereum
                 Jupiter ↔ Token Swaps
```

**Components:**
- **Solana Program**: On-chain phone registry (Anchor).
- **Backend Server**: Node.js with Express + Twilio.
- **Bridge Handler**: Cross-chain operations (Wormhole).
- **Swap Handler**: Token swaps via Jupiter API.
- **WhatsApp Handler**: Command parsing and message flow.

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
TWILIO_WHATSAPP_NUMBER=whatsapp:+14155238886
```

### 4. Start Backend
```bash
cd backend
npm run whatsapp
```

### 5. Local Testing (Optional)
Expose the server using ngrok:
```bash
ngrok http 3000
```
Use the generated HTTPS URL as your Twilio webhook.

---

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
   - `swap 0.5 sol to usdc` → Swaps tokens.
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

## Testing

### Local Simulation
```bash
node testWhatsApp.js   # Simulate WhatsApp messages
node testCrossChain.js # Test Wormhole transfers
```

### Solana Program Tests
```bash
cd program
cargo test-sbf
```

---

## Tech Stack

**Blockchain:** Solana (Anchor, Rust), Ethereum (Ethers.js)  
**Cross-Chain:** Wormhole SDK, Jupiter API  
**Backend:** Node.js, Express, Twilio API, bs58, dotenv  
**Dev Tools:** ngrok, Anchor CLI, Solana CLI, Aptos CLI

---

## Security

- Private keys encrypted at rest.
- Phone number hashed before on-chain storage.
- Custodial wallets for demo purposes.
- Production use should migrate to MPC or HSM-secured wallets.

---

## Roadmap

**Phase 1 (MVP)**  
- ✅ Solana deployment  
- ✅ WhatsApp integration  
- ✅ Token swap (Jupiter)  
- ✅ Cross-chain bridge (Wormhole)

**Phase 2 (Mainnet)**  
- 🔒 Security audit  
- 💬 Multi-language support  
- 🌐 Web dashboard  
- 📱 Mobile app integration

**Phase 3 (Expansion)**  
- Merchant tools  
- Recurring payments  
- Payment analytics

---

## License

This project is licensed under the **MIT License**.

---

**SolChat** — Bridging decentralized finance and global communication, one message at a time.

