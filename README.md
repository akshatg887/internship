# SolChat: Multi-Chain WhatsApp Payment System# SolChat: Multi-Chain WhatsApp Payment System

> **Solana Cypherpunk Hackathon 2025 Submission**> **Solana Cypherpunk Hackathon 2025** | [Hackathon Documentation](./HACKATHON_README.md) | [Command Reference](./COMMAND_REFERENCE.md)

![License](https://img.shields.io/badge/license-MIT-blue.svg)![SolChat Banner](https://via.placeholder.com/800x200?text=SolChat:+Multi-Chain+Payments+via+WhatsApp)

![Solana](https://img.shields.io/badge/Solana-Devnet-green.svg)

![Anchor](https://img.shields.io/badge/Anchor-0.30.1-purple.svg)## 🎯 Quick Links

![Node](https://img.shields.io/badge/Node.js-16%2B-brightgreen.svg)

- **[📖 Hackathon Submission Guide](./HACKATHON_README.md)** - Complete details for judges

## 🎯 What is SolChat?- **[⚡ Quick Command Reference](./COMMAND_REFERENCE.md)** - Demo script and examples

- **[✅ Cross-Chain Complete](./CROSS_CHAIN_COMPLETE.md)** - Implementation summary

SolChat is a **multi-chain WhatsApp payment bot** that makes cryptocurrency as easy as sending a text message. Users send payments using phone numbers instead of wallet addresses, leveraging Solana's speed and low fees with cross-chain bridging to Ethereum via Wormhole.- **[🧪 Test Results](./backend/testCrossChain.js)** - Cross-chain test suite

**Key Innovation:** Phone number → Wallet mapping stored on-chain in a Solana program, enabling true decentralized peer-to-peer payments through WhatsApp.---

### 🏆 Hackathon Highlights## 📱 What is SolChat?

- ⚡ **Solana-First**: Built with Anchor Framework, deployed on Solana DevnetSolChat is a **multi-chain WhatsApp payment bot** that enables users to send and receive cryptocurrency using just their phone number. Built on Solana with Ethereum compatibility, it showcases true decentralized interoperability.

- 🌉 **Cross-Chain Bridge**: Wormhole integration for Ethereum ↔ Solana transfers

- 🔄 **DEX Integration**: Jupiter aggregator for seamless token swaps**Revolutionary Features:**

- 📱 **Real UX Innovation**: 2 billion WhatsApp users can send crypto without knowing addresses

- 🔐 **Cypherpunk Values**: Decentralized, permissionless, user-sovereign- 🟣 **Solana Wallet** - Fast, cheap on-chain payments

- 🔵 **Ethereum Wallet** - Cross-chain compatibility

### ✨ Features- 📱 **Phone Number as Wallet** - No addresses to remember

- 🌉 **Cross-Chain Bridge** - Wormhole + Jupiter integration

- 💸 **Send SOL/USDC** via phone number (e.g., "send 1 sol to +1234567890")- 💬 **WhatsApp Interface** - Send crypto like a text message

- 🌍 **Cross-Chain Bridge**: Transfer assets between Solana and Ethereum- 🔒 **Secure & Private** - Decentralized phone number mapping

- 💱 **Token Swaps**: Use Jupiter to swap SOL ↔ USDC seamlessly

- 💰 **Check Balances**: View Solana and Ethereum wallet balances---

- 📞 **Phone Registry**: On-chain mapping of phone → Solana wallet

- 🔒 **Custodial Wallets**: Backend manages keys, users interact via WhatsApp## � Hackathon Highlights

---### Why SolChat Wins

## 🏗️ Architecture1. **Multi-Chain Innovation** - First WhatsApp bot with native Solana + Ethereum support

2. **Cypherpunk Ethos** - Decentralized, interoperable, user-sovereign

````3. **Solana Showcase** - Leverages speed, low fees, and ecosystem (Jupiter)

┌─────────────┐         ┌──────────────┐         ┌─────────────────┐4. **Real-World Utility** - Solves crypto UX problem for 2 billion WhatsApp users

│  WhatsApp   │────────▶│   Backend    │────────▶│  Solana Program │

│   (Twilio)  │         │  (Node.js)   │         │ (Phone Registry)│### Technology Stack

└─────────────┘         └──────────────┘         └─────────────────┘

                               │- **Solana**: Primary settlement layer (Anchor Framework 0.30.1)

                               ├──────────▶ Wormhole Bridge ─────▶ Ethereum- **Ethereum**: Secondary chain for cross-chain compatibility

                               │- **Wormhole**: Cross-chain bridge protocol

                               └──────────▶ Jupiter DEX ──────────▶ Swaps- **Jupiter**: DEX aggregator for token swaps

```- **Twilio**: WhatsApp Business API

- **Node.js**: Express backend with multi-chain handlers

**Components:**

1. **Solana Program** (`program/src/lib.rs`) - On-chain phone registry using PDAs---

2. **WhatsApp Handler** (`backend/whatsappHandler.js`) - Parses commands, manages wallets

3. **Cross-Chain Bridge** (`backend/crossChainHandler.js`) - Wormhole integration## 🚀 Quick Start

4. **Token Swaps** (`backend/swapHandler.js`) - Jupiter API integration

5. **Solana Service** (`backend/solanaService.js`) - RPC interactions, program calls### For Hackathon Judges



---1. **See the demo**: Read [COMMAND_REFERENCE.md](./COMMAND_REFERENCE.md)

2. **Understand the tech**: Read [HACKATHON_README.md](./HACKATHON_README.md)

## 🚀 Quick Start (For Judges)3. **Review the code**: Check `backend/crossChainHandler.js` and `backend/whatsappHandler.js`

4. **Run tests**: `cd backend && node testCrossChain.js`

### Option 1: Review the Code

```bash### For Developers

# Clone the repository

git clone https://github.com/yourusername/solchat.git#### Prerequisites

cd solchat

- Node.js v16+ and npm

# Check deployed program on Solana Devnet- Solana CLI tools (for program deployment)

solana program show BZ5Z67xFRgyCaobqDnRw2p2NDPu8EoqMFwV55rENVsBR --url devnet- Aptos CLI installed and configured

```- Twilio account with WhatsApp sandbox

- Aptos testnet account with APT tokens

**Deployed Program ID (Devnet):** `BZ5Z67xFRgyCaobqDnRw2p2NDPu8EoqMFwV55rENVsBR`

### Installation

### Option 2: Run the Backend Locally

```bash1. **Clone the repository**

# Install dependencies

npm install   ```bash

cd backend && npm install   git clone https://github.com/Parthkk90/ChatterPay.git

   cd ChatterPay

# Configure environment (see Setup section below)   ```

cp backend/.env.example backend/.env

# Edit .env with your Twilio credentials2. **Install Dependencies**



# Start the server   **Backend Dependencies:**

cd backend && npm run whatsapp

```   ```bash

   cd backend

### Option 3: Test Without WhatsApp   npm install

```bash   ```

# Use the test script to simulate WhatsApp messages

node testWhatsApp.js   **Contract Dependencies (Aptos CLI):**

````

````bash

---   # Install Aptos CLI if not already installed

# For Windows (using PowerShell as Administrator):

## 📋 Prerequisites   iwr "https://aptos.dev/scripts/install_cli.py" -useb | Select-Object -ExpandProperty Content | python3



### Required Software   # For macOS/Linux:

curl -fsSL "https://aptos.dev/scripts/install_cli.py" | python3

| Tool | Version | Purpose | Installation Guide |   ```

|------|---------|---------|-------------------|

| **Node.js** | 16+ | Backend runtime | [nodejs.org](https://nodejs.org) |3. **Environment Setup**

| **npm** | 8+ | Package manager | Comes with Node.js |

| **Rust** | Stable (1.75+) | Solana program compilation | [rustup.rs](https://rustup.rs) |   Create a `.env` file in the `backend` directory:

| **Solana CLI** | 1.18+ | Deployment and testing | See below |

| **Anchor CLI** | 0.30.1 | **CRITICAL VERSION** | See below |   ```bash

| **WSL** (Windows only) | Ubuntu 20.04+ | Linux environment for builds | See below |   cd backend

# Create .env file with the following variables:

### ⚠️ Version Requirements (CRITICAL)   ```



**Why these versions matter:**   **Required Environment Variables:**

- Anchor 0.30.1 is required to match `anchor-lang` and `anchor-spl` dependencies

- Newer Anchor CLI (0.32.1+) causes version conflicts with Solana SDK   ```env

- Using cargo build-sbf is more reliable than anchor build for this project   # Aptos Configuration

APTOS_NODE_URL=https://fullnode.testnet.aptoslabs.com/v1

```toml   CONTRACT_ADDRESS=0x8541b65e57d7744df2e81ace0c3e23fe598f77063fc8d2829a62726a8a7a29df

# program/Cargo.toml - DO NOT CHANGE THESE VERSIONS   SERVER_PRIVATE_KEY=your_server_private_key_here

[dependencies]

anchor-lang = "0.30.1"   # Twilio Configuration (for WhatsApp integration)

anchor-spl = "0.30.1"   TWILIO_ACCOUNT_SID=your_twilio_account_sid

```   TWILIO_AUTH_TOKEN=your_twilio_auth_token

TWILIO_PHONE_NUMBER=your_twilio_whatsapp_number

**Common Error:** If you see "Invalid Base58 string" errors during build, you have a version mismatch. Ensure Anchor CLI is exactly 0.30.1.

# Server Configuration

---   PORT=3000

````

## 🛠️ Installation (Step-by-Step)

### 🔑 Twilio WhatsApp Setup

### 1️⃣ Install WSL (Windows Users Only)

1. **Create Twilio Account**

````powershell

# Open PowerShell as Administrator   - Sign up at [Twilio Console](https://console.twilio.com/)

wsl --install -d Ubuntu-22.04   - Navigate to "Messaging" → "Try it out" → "Send a WhatsApp message"

wsl --set-default-version 2

2. **WhatsApp Sandbox Setup**

# Restart your computer

# Launch Ubuntu from Start Menu and create username/password   - Get your sandbox WhatsApp number

```   - Configure webhook URL: `https://your-domain.com/webhook`

   - For local development, use ngrok: `https://ngrok.com/`

**All subsequent commands should be run inside WSL (Ubuntu terminal).**

3. **Get Twilio Credentials**

### 2️⃣ Install Rust   - Account SID and Auth Token from Twilio Console Dashboard

   - WhatsApp sandbox phone number

**In WSL/Linux/macOS:**

```bash### 🚀 Smart Contract Deployment

curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

source $HOME/.cargo/env1. **Setup Aptos Account**



# Verify installation   ```bash

rustc --version   # Initialize Aptos configuration

cargo --version   aptos init

````

# This will create ~/.aptos/config.yaml with your account details

### 3️⃣ Install Solana CLI # Select testnet when prompted

````

```bash

sh -c "$(curl -sSfL https://release.solana.com/stable/install)"2. **Fund Your Account**



# Add to PATH (add this line to ~/.bashrc or ~/.zshrc)   ```bash

export PATH="$HOME/.local/share/solana/install/active_release/bin:$PATH"   # Get testnet APT tokens

source ~/.bashrc   aptos account fund-with-faucet --account default

````

# Verify

solana --version # Should be 1.18+3. **Deploy the Contract**

````

   ```bash

### 4️⃣ Install Anchor (⚠️ Version 0.30.1 REQUIRED)   cd contracts



```bash   # Compile the contract

# Install avm (Anchor Version Manager)   aptos move compile

cargo install --git https://github.com/coral-xyz/anchor avm --locked --force

   # Deploy to testnet

# Install Anchor 0.30.1   aptos move publish --named-addresses ChatterPay=default

avm install 0.30.1   ```

avm use 0.30.1

   **Note:** After deployment, update the `CONTRACT_ADDRESS` in your `.env` file with the deployed contract address.

# Verify

anchor --version  # Should show: anchor-cli 0.30.14. **Initialize the Registry**

```   ```bash

   # Run the initialization script

**Troubleshooting:**    cd ../

- If you have Anchor 0.32.1 already installed, use `avm use 0.30.1` to switch   node chatterPay.js

- If `avm` command not found, add to PATH: `export PATH="$HOME/.cargo/bin:$PATH"`   ```



### 5️⃣ Clone and Install Dependencies## 🏃‍♂️ Running the Application



```bash### Method 1: Manual Step-by-Step

# Clone repository

git clone https://github.com/yourusername/solchat.git1. **Start the Backend Server**

cd solchat

   ```bash

# Install Node.js dependencies (root)   cd backend

npm install   npm start

   # or for development with auto-reload:

# Install backend dependencies   npm run dev

cd backend   ```

npm install

cd ..   The server will start on `http://localhost:3000`

````

2. **Test the API Endpoints**

### 6️⃣ Environment Configuration

````bash

Create a `.env` file in the `backend/` directory:   # Test server status

curl http://localhost:3000/

```bash

cd backend   # Register a user (replace with actual private key and phone)

cp .env.example .env   curl -X POST http://localhost:3000/api/register \

# Edit .env with your credentials     -H "Content-Type: application/json" \

```     -d '{"privateKeyHex":"your_private_key", "phone":"+1234567890"}'



**Required Environment Variables:**   # Send payment

curl -X POST http://localhost:3000/api/send \

```env     -H "Content-Type: application/json" \

# Solana Configuration     -d '{"privateKeyHex":"your_private_key", "recipientPhone":"+0987654321", "amount":"0.01"}'

SOLANA_RPC_URL=https://api.devnet.solana.com   ```

PROGRAM_ID=BZ5Z67xFRgyCaobqDnRw2p2NDPu8EoqMFwV55rENVsBR

3. **Setup WhatsApp Webhook (for local development)**

# Server Configuration

PORT=3000   ```bash

# Install ngrok globally

# Server Private Key (Generate with: solana-keygen new)   npm install -g ngrok

# This is the backend's wallet for paying transaction fees

SERVER_PRIVATE_KEY=your_base58_private_key_here   # Expose local server to internet

ngrok http 3000

# Twilio Configuration (Get from Twilio Console)

TWILIO_ACCOUNT_SID=your_account_sid   # Copy the https URL and configure it in Twilio Console

TWILIO_AUTH_TOKEN=your_auth_token   # Webhook URL: https://your-ngrok-url.ngrok.io/webhook

TWILIO_WHATSAPP_NUMBER=whatsapp:+14155238886   ```



# Cross-Chain Configuration### Method 2: Using Docker (Optional)

ETHEREUM_RPC_URL=https://ethereum-sepolia-rpc.publicnode.com

WORMHOLE_GUARDIAN_RPC=https://wormhole-v2-testnet-api.certus.one1. **Create Dockerfile for Backend**

JUPITER_API_URL=https://lite-api.jup.ag

```   ```dockerfile

FROM node:18-alpine

**Getting Twilio Credentials:**   WORKDIR /app

1. Sign up at [twilio.com/try-twilio](https://www.twilio.com/try-twilio)   COPY backend/package*.json ./

2. Activate WhatsApp Sandbox: Console → Messaging → Try it out → WhatsApp   RUN npm install

3. Copy Account SID and Auth Token from Dashboard   COPY backend/ .

EXPOSE 3000

**Generating Server Private Key:**   CMD ["npm", "start"]

```bash   ```

# In WSL

solana-keygen new --outfile server_keypair.json2. **Build and Run**

# Copy the private key array and convert to base58 or use the keypair file   ```bash

```   docker build -t chatterpay-backend .

docker run -p 3000:3000 --env-file backend/.env chatterpay-backend

---   ```



## 🔨 Building the Solana Program## 📱 Using SolChat via WhatsApp



### Method 1: Using Cargo (Recommended)Once everything is set up and running:



This method is more reliable and avoids Anchor CLI version conflicts.1. **Join Twilio WhatsApp Sandbox**



```bash   - Send the join code to your Twilio WhatsApp number

# Navigate to program directory   - Example: Send "join <your-sandbox-code>" to +1 415 523 8886

cd program

2. **Register Your Phone Number**

# Build the program

cargo build-sbf   - First, you need to register your phone with a blockchain address

- Use the API or the provided script to register

# The compiled program will be at: target/deploy/solchat_solana.so

```3. **Send Payments via WhatsApp**



### Method 2: Using Anchor Build (If versions match)   - Use the command format: `PAY <recipient_phone> <amount>`

- Example: `PAY +1234567890 0.01`

Only use this if you have exactly Anchor CLI 0.30.1 installed.

4. **WhatsApp Commands**

```bash   ```

# From project root   PAY +1234567890 0.01    # Send 0.01 APT to +1234567890

anchor build   BALANCE                 # Check your balance (if implemented)

```   HELP                    # Get help message (if implemented)

````

**If you encounter errors:**

- "Invalid Base58 string" → Version mismatch, use cargo build-sbf## 🧪 Testing the System

- "failed to parse manifest" → Wrong Anchor version, ensure 0.30.1

- "dependency resolution failed" → Check Cargo.toml versions match exactly1. **Test Contract Functions**

--- ```bash

# Run the test script

## 🚀 Deployment node chatterPay.js

````

### Deploy to Solana Devnet

2. **Test WhatsApp Integration**

The program is already deployed at `BZ5Z67xFRgyCaobqDnRw2p2NDPu8EoqMFwV55rENVsBR`. To deploy your own instance:

- Send a test message to your WhatsApp sandbox number

```bash   - Check server logs for webhook activity

# 1. Configure Solana CLI for devnet

solana config set --url devnet3. **Test API Endpoints**

```bash

# 2. Create a new keypair for the program (or use existing)   # Test Twilio integration

solana-keygen new -o target/deploy/solchat_solana-keypair.json   curl http://localhost:3000/test-twilio

````

# 3. Airdrop SOL for deployment fees

solana airdrop 2 $(solana-keygen pubkey target/deploy/solchat_solana-keypair.json) --url devnet## 🔍 Troubleshooting

# 4. Deploy the program### Common Issues:

solana program deploy target/deploy/solchat_solana.so \

--program-id target/deploy/solchat_solana-keypair.json \1. **Contract Address Not Set**

--url devnet

- Make sure `CONTRACT_ADDRESS` in `.env` matches your deployed contract

# 5. Verify deployment

solana program show <PROGRAM_ID> --url devnet2. **Twilio Webhook Not Working**

````

   - Verify webhook URL is accessible (use ngrok for local development)

**Update Program ID in Configuration:**   - Check Twilio console for webhook logs



After deployment, update the program ID in:3. **Phone Number Format Issues**

1. `backend/.env` → `PROGRAM_ID=<your_new_program_id>`

2. `Anchor.toml` → Update all `solchat_solana` program IDs   - Use international format: +1234567890

3. `program/src/lib.rs` → Update `declare_id!("<your_new_program_id>")`   - Ensure consistent formatting across the system



---4. **Insufficient APT Balance**



## 🧪 Testing   - Fund your account using Aptos faucet: `aptos account fund-with-faucet --account default`



### 1. Test Solana Program5. **Move Compilation Errors**

   - Ensure Aptos CLI is properly installed and updated

```bash   - Check Move.toml configuration

# Run unit tests

cd program### Debug Commands:

cargo test-sbf

```bash

# Or with Anchor# Check Aptos CLI version

anchor testaptos --version

````

# Check account balance

### 2. Test Backend Without WhatsAppaptos account balance --account default

Use the test script to simulate WhatsApp messages:# View deployed contract

aptos account list --query modules --account your_contract_address

```bash

# From project root# Check server logs

node testWhatsApp.jstail -f backend/server.log

```

This script bypasses Twilio and directly calls the message handler with test phone numbers.## 📊 Project Structure

### 3. Test Cross-Chain Bridge```

SolChat/

````bash├── backend/                 # Node.js/Express server

cd backend│   ├── server.js           # Main server file

node testCrossChain.js│   ├── aptosService.js     # Aptos blockchain integration

```│   ├── package.json        # Backend dependencies

│   └── .env               # Environment variables

### 4. Test with WhatsApp Sandbox├── contracts/              # Move smart contracts

│   ├── sources/

1. Start the backend server:│   │   └── phone_registry.move

```bash│   ├── Move.toml          # Move project configuration

cd backend│   └── build/             # Compiled contracts

npm run whatsapp├── frontend/              # Frontend application (if needed)

```├── docs/                  # Documentation

├── solChat.js            # Main initialization script

2. Expose to internet using ngrok (for local testing):└── README.md             # This file

```bash```

ngrok http 3000

```## 🔒 Security Considerations



3. Configure Twilio Webhook:- **Private Keys**: Never commit private keys to version control

   - Go to Twilio Console → WhatsApp Sandbox Settings- **Environment Variables**: Use secure methods to store sensitive data

   - Set "When a message comes in" webhook to: `https://your-ngrok-url/webhook`- **Phone Number Hashing**: Phone numbers are hashed for privacy

   - Method: POST- **Testnet Only**: This setup is for testnet only - additional security needed for mainnet



4. Send WhatsApp message to your Twilio sandbox number:## 🚀 Next Steps

````

help1. **Add Balance Check Feature**: Implement balance checking via WhatsApp

```2. **Transaction History**: Add transaction history lookup

3. **Multi-coin Support**: Extend to support other Aptos tokens

### Test Commands4. **Web Dashboard**: Create a web interface for account management

5. **Security Audit**: Conduct thorough security review before mainnet deployment

Send these messages via WhatsApp:

## 📝 API Documentation

```

register # Create your wallets### Endpoints

balance # Check balances

send 0.1 sol to +1234567890#### `GET /`

swap 1 sol to usdc

bridge 0.5 sol to ethereum- **Description**: Health check endpoint

help # See all commands- **Response**: Server status and timestamp

````

#### `POST /api/register`

---

- **Description**: Register a phone number with blockchain address

## 📱 WhatsApp Commands Reference- **Body**:

  ```json

| Command | Example | Description |  {

|---------|---------|-------------|    "privateKeyHex": "0x...",

| `register` | `register` | Create Solana + Ethereum wallets |    "phone": "+1234567890"

| `balance` | `balance` | Check all wallet balances |  }

| `send` | `send 1 sol to +1234567890` | Send SOL to phone number |  ```

| `swap` | `swap 0.5 sol to usdc` | Swap tokens using Jupiter |

| `bridge` | `bridge 1 sol to ethereum` | Bridge to Ethereum via Wormhole |#### `POST /api/send`

| `bridge status` | `bridge status` | Check bridge transaction status |

| `help` | `help` | Show all commands |- **Description**: Send APT to a phone number

- **Body**:

---  ```json

  {

## 🐛 Troubleshooting    "privateKeyHex": "0x...",

    "recipientPhone": "+1234567890",

### Build Errors    "amount": "0.01"

  }

**Error: "Invalid Base58 string"**  ```

````

Caused by: Invalid Base58 string#### `POST /webhook`

````

**Solution:** Version mismatch. Ensure Anchor CLI is exactly 0.30.1:- **Description**: Twilio WhatsApp webhook

```bash- **Used by**: Twilio to forward WhatsApp messages

avm use 0.30.1

anchor --version## 🤝 Contributing

````

1. Fork the repository

**Error: Dependency resolution failed**2. Create a feature branch

````3. Make your changes

failed to select a version for `solana-program`4. Test thoroughly

```5. Submit a pull request

**Solution:** Use cargo build-sbf instead of anchor build:

```bash## 📄 License

cd program

cargo build-sbfThis project is licensed under the MIT License - see the LICENSE file for details.

````

---

**Error: "no such subcommand: build-sbf"**

```For more detailed setup instructions, check the `docs/setup/SETUP.md` file.

error: no such subcommand: `build-sbf`

````
**Solution:** Update Solana CLI or use full cargo path:
```bash
~/.cargo/bin/cargo build-sbf
````

### Deployment Errors

**Error: Insufficient funds**

```
Error: Account <address> has insufficient funds
```

**Solution:** Airdrop SOL to deployer:

```bash
solana airdrop 2 --url devnet
```

**Error: Program deployment failed**

```
Error: Program write failed
```

**Solution:** Check program size (max 10MB on devnet), verify keypair:

```bash
ls -lh target/deploy/solchat_solana.so  # Should be < 10MB
solana-keygen verify <pubkey> target/deploy/solchat_solana-keypair.json
```

### Runtime Errors

**Error: "User not registered"**

```
❌ Error: User not registered. Please send 'register' first.
```

**Solution:** After deploying a new program, all users must re-register:

```bash
# Check which users need re-registration
node backend/reregisterUsers.js

# Users send: register
```

**Error: "Program account not found"**

```
Error: AccountNotFound: pubkey=<PROGRAM_ID>
```

**Solution:** Verify program ID in `.env` matches deployed program:

```bash
solana program show <PROGRAM_ID> --url devnet
```

**Error: Twilio 429 Too Many Requests**

```
Status 429: Too Many Requests
```

**Solution:** Use test script to bypass Twilio limits:

```bash
node testWhatsApp.js
```

### Network Errors

**Error: Connection timeout to Solana RPC**

```
Error: 429 Too Many Requests
```

**Solution:** Use a different RPC endpoint or rate limit:

```env
# In backend/.env, try these alternatives:
SOLANA_RPC_URL=https://api.devnet.solana.com
SOLANA_RPC_URL=https://devnet.helius-rpc.com/?api-key=YOUR_KEY
```

---

## 📁 Project Structure

```
solchat/
├── program/                    # Solana program (Rust + Anchor)
│   ├── src/
│   │   └── lib.rs             # Phone registry logic
│   ├── Cargo.toml             # Dependencies (anchor-lang 0.30.1)
│   └── Xargo.toml
├── backend/                    # Node.js backend
│   ├── whatsappHandler.js     # WhatsApp message parsing
│   ├── whatsappServer.js      # Express server + Twilio webhook
│   ├── solanaService.js       # Solana RPC + program calls
│   ├── crossChainHandler.js   # Wormhole bridge logic
│   ├── swapHandler.js         # Jupiter DEX integration
│   ├── reregisterUsers.js     # User migration script
│   └── .env                   # Configuration (not in git)
├── target/
│   ├── deploy/
│   │   ├── solchat_solana.so  # Compiled program
│   │   └── solchat_solana-keypair.json
│   └── idl/
│       └── solchat_solana.json  # Interface definition
├── Anchor.toml                 # Anchor configuration
├── package.json                # Root dependencies
└── README.md                   # This file
```

---

## 🔑 Key Technologies

### Solana Stack

- **Anchor Framework 0.30.1**: Rust framework for Solana programs
- **@solana/web3.js 1.87.6**: JavaScript SDK for Solana RPC
- **@coral-xyz/anchor 0.30.1**: TypeScript client for Anchor programs

### Cross-Chain

- **@wormhole-foundation/sdk 3.9.0**: Cross-chain messaging protocol
- **Wormhole Token Bridge**: Transfer assets between Solana ↔ Ethereum
- **ethers.js 6.15.0**: Ethereum RPC interactions

### DeFi

- **@jup-ag/api 6.0.45**: Jupiter aggregator for best swap rates
- **SPL Token**: Solana token standard (USDC, etc.)

### Backend

- **Express 4.18.2**: Web server for webhooks
- **Twilio 4.23.0**: WhatsApp Business API
- **bs58**: Base58 encoding for keys
- **dotenv**: Environment configuration

---

## 🎨 How It Works

### 1. User Registration

```
User sends: "register"
   ↓
Backend generates:
  - Solana keypair
  - Ethereum keypair
   ↓
Backend calls Solana program:
  registerUser(phoneNumber, publicKey)
   ↓
Program creates PDA:
  seeds: [b"phone", phoneNumber.as_bytes()]
   ↓
Stores mapping on-chain:
  PhoneNumber → Solana Wallet Address
```

### 2. Sending Payment

```
User sends: "send 1 sol to +1234567890"
   ↓
Backend parses command:
  amount: 1 SOL
  recipient: +1234567890
   ↓
Backend queries program:
  getPhoneAccount(+1234567890)
   ↓
Program returns recipient's Solana address
   ↓
Backend creates transaction:
  SystemProgram.transfer(
    from: sender.wallet,
    to: recipient.wallet,
    lamports: 1_000_000_000
  )
   ↓
Backend signs and sends to Solana
   ↓
WhatsApp confirms: "✅ Sent 1 SOL to +1234567890"
```

### 3. Cross-Chain Bridge

```
User sends: "bridge 1 sol to ethereum"
   ↓
Backend initiates Wormhole transfer:
  1. Lock SOL on Solana (user's wallet)
  2. Wormhole VAA (signed message)
  3. Mint wrapped SOL on Ethereum
   ↓
Backend monitors bridge status:
  PENDING → PROCESSING → COMPLETE
   ↓
WhatsApp confirms: "🎉 Bridge Complete!"
```

---

## 🌟 Advanced Features

### PDA-Based Phone Registry

The Solana program uses Program Derived Addresses (PDAs) for deterministic account discovery:

```rust
// Find user account without storing mapping
let (pda, _bump) = Pubkey::find_program_address(
    &[b"phone", phone_number.as_bytes()],
    &program_id
);
```

**Benefits:**

- No centralized database needed
- Phone → Wallet mapping is on-chain and verifiable
- Deterministic: Same phone always maps to same PDA

### Jupiter Integration

SolChat uses Jupiter's aggregator API for best swap rates:

```javascript
const route = await getJupiterRoute({
  inputMint: SOL_MINT,
  outputMint: USDC_MINT,
  amount: 1_000_000_000,
  slippage: 50, // 0.5%
});
```

**Advantages:**

- Best prices across all Solana DEXs
- Automatic route optimization
- Low slippage

### Wormhole Cross-Chain

Wormhole enables trustless bridging:

```javascript
const transfer = await wormhole.tokenBridge.transfer({
  token: SOL_TOKEN,
  amount: parseUnits("1", 9),
  fromChain: "Solana",
  toChain: "Ethereum",
  recipient: ethereumAddress,
});
```

---

## 🚧 Known Limitations

1. **Custodial Model**: Backend holds user private keys (future: MPC wallets)
2. **Testnet Only**: Currently on Devnet/Sepolia (mainnet requires audits)
3. **Wormhole Fees**: Cross-chain transfers have bridge fees (~$0.50-$1)
4. **Twilio Limits**: Free tier limited to 1,000 msgs/month
5. **Phone Verification**: No SMS verification (future: Twilio Verify API)

---

## 🔐 Security Considerations

### Current Implementation

- ⚠️ Custodial wallets stored on backend server
- ⚠️ Private keys in filesystem (encrypted recommended)
- ✅ Phone → Wallet mapping is decentralized (on-chain)
- ✅ All transactions signed by user's dedicated wallet

### Production Recommendations

1. **Use HSM** for private key storage
2. **Implement MPC** (Multi-Party Computation) for key management
3. **Add 2FA** via SMS or authenticator app
4. **Rate limiting** on transactions
5. **Security audit** before mainnet deployment

---

## 🗺️ Roadmap

### Phase 1: Hackathon MVP ✅

- [x] Solana program deployment
- [x] WhatsApp bot integration
- [x] Cross-chain bridge (Wormhole)
- [x] Token swaps (Jupiter)
- [x] Phone-based payments

### Phase 2: Mainnet Launch

- [ ] Security audit
- [ ] MPC wallet integration
- [ ] Gas fee abstraction
- [ ] Multi-language support
- [ ] Web dashboard

### Phase 3: Ecosystem Growth

- [ ] Merchant integration
- [ ] Recurring payments
- [ ] Invoice generation
- [ ] Analytics dashboard
- [ ] Mobile app (React Native)

---

## 🤝 Contributing

Contributions are welcome! Please follow these guidelines:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit changes: `git commit -m 'Add amazing feature'`
4. Push to branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

**Code Style:**

- Follow existing patterns
- Add comments for complex logic
- Test before submitting

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- **Solana Foundation** for the Cypherpunk Hackathon
- **Anchor Framework** for excellent Solana development tools
- **Wormhole** for cross-chain infrastructure
- **Jupiter** for DEX aggregation
- **Twilio** for WhatsApp API

---

## 📞 Contact & Support

- **GitHub Issues**: [github.com/yourusername/solchat/issues](https://github.com/yourusername/solchat/issues)
- **Twitter**: [@yourhandle](https://twitter.com/yourhandle)
- **Discord**: [Join our community](#)

---

## 🎥 Demo

Watch the full demo video: [YouTube Link](#)

**Deployed Program (Devnet):** `BZ5Z67xFRgyCaobqDnRw2p2NDPu8EoqMFwV55rENVsBR`

**Live Backend:** Contact for demo access

---

**Built with ❤️ for Solana Cypherpunk Hackathon 2025**
