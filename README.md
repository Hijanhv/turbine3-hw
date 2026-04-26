# Turbine3 — Assignment 0: Environment Setup & Anchor Initialization

## Overview

This repository contains the setup and initialization of a Solana development environment as part of **Turbine3 Assignment 0**. It covers installing all required dependencies and scaffolding a new Anchor project.

---

## Environment

| Tool | Version |
|------|---------|
| Rust | 1.95.0 |
| Solana CLI | 3.1.14 |
| Anchor CLI | 1.0.1 |
| Surfpool | 1.2.0 |

---

## Installation Steps

### 1. Install Rust

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
. "$HOME/.cargo/env"
rustc --version
```

### 2. Install Solana CLI

```bash
sh -c "$(curl -sSfL https://release.anza.xyz/stable/install)"
echo 'export PATH="$HOME/.local/share/solana/install/active_release/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
solana --version
```

### 3. Install Anchor CLI (via AVM)

```bash
cargo install --git https://github.com/solana-foundation/anchor avm --force
avm install latest
avm use latest
anchor --version
```

### 4. Install Surfpool CLI

```bash
curl -sL https://run.surfpool.run/ | bash
surfpool --version
```

### 5. Verify All Installations

```bash
rustc --version && solana --version && anchor --version && surfpool --version
```

---

## Wallet Setup

```bash
# Generate a new keypair (skip if one already exists)
solana-keygen new

# Switch to Devnet
solana config set -ud

# Airdrop test SOL
solana airdrop 2

# Check balance
solana balance
```

---

## Anchor Project Initialization

```bash
anchor init turbine3-hw
cd turbine3-hw
anchor build
anchor test
```

### Project Structure

```
turbine3-hw/
├── Anchor.toml
├── Cargo.toml
├── programs/
│   └── turbine3-hw/
│       └── src/
│           ├── lib.rs
│           ├── constants.rs
│           ├── error.rs
│           ├── instructions.rs
│           ├── instructions/
│           │   └── initialize.rs
│           └── state.rs
├── migrations/
│   └── deploy.ts
└── tests/
    └── test_initialize.rs
```

---

## Network Configuration

- **Cluster:** Devnet
- **RPC URL:** https://api.devnet.solana.com

---

## Resources

- [Solana Docs](https://solana.com/docs)
- [Anchor Docs](https://www.anchor-lang.com/docs)
- [Surfpool Docs](https://docs.surfpool.run)
- [Solana Faucet](https://faucet.solana.com)
