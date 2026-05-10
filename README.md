# Proof, please!

### Decentralized Contribution & Reputation Infrastructure for Indie Games

**Built on Solana | Powered by AI Scoring | Web3 Native**

> Hackathon MVP — May 2026

---

## Overview

**Proof, please!** is a decentralized platform where indie game developers and creative contributors — artists, musicians, animators, writers, testers, and coders — can submit verifiable contributions to game projects and earn on-chain reputation without relying on centralized authorities.

The platform combines:

* Solana smart contracts
* AI-powered contribution scoring
* Soulbound reputation tokens (SBTs)
* Escrow-based funding infrastructure

to create a trustless, merit-based ecosystem for indie game collaboration.

---

# Vision

Indie game development is fragmented and underfinanced. Creative contributors often cannot prove the value of their work in a way that translates into trust, reputation, or funding opportunities.

Traditional crowdfunding platforms focus almost exclusively on financial investment while leaving creative labor invisible.

**Proof, please!** introduces a new paradigm:

* Creative work becomes verifiable on-chain
* Reputation becomes portable across projects
* Funding becomes milestone-based and trustless
* AI replaces governance overhead for small teams

Without boundaries of any kind. We create more value globally.

---

# Problem

* Indie creators cannot prove the value of creative contributions in a verifiable way
* Traditional crowdfunding excludes talent-based participation
* No portable reputation exists across indie game ecosystems
* Small teams lack governance infrastructure and trust mechanisms

---

# Solution

Proof, please! creates a decentralized contribution verification layer where:

* Creative labor becomes an investable asset
* Reputation is earned, not purchased
* AI verification reduces DAO overhead
* Escrow contracts protect contributors and funders

---

# Core Features

## AI-Powered Reputation Scoring

Inspired by Web3 reputation systems such as Nomis, Ethos, and Statur.

The AI scorer evaluates:

* Originality
* Technical quality
* Completeness
* Project relevance
* Cross-project consistency
* Community value

Scores are stored on-chain as non-transferable Soulbound Tokens (SBTs).

---

## Soulbound Reputation Tokens (SBTs)

Reputation is represented by:

* Non-transferable tokens
* Permanent contribution history
* Cross-project identity
* Merit-based progression

Reputation cannot be bought or traded.

It must be earned.

---

## Escrow Smart Contracts

Funding infrastructure is milestone-based:

* Project creators deposit SOL into escrow
* Funds remain locked until milestones are verified
* AI scorer validates contribution completion
* Escrow releases rewards proportionally

Transparent. Trustless. Auditable.

---

# MVP Demo Flow

1. User connects Phantom or Solflare wallet
2. Contributor submits work with:

   * contribution type
   * project ID
   * description
   * IPFS file hash
3. AI scorer analyzes the contribution
4. Reputation score (0–100) is generated
5. Score is stored on-chain as a Soulbound Token
6. Dashboard updates with contribution history and reputation level
7. Escrow contract demonstrates milestone reward distribution

---

# Technology Stack

| Layer               | Technology                        |
| ------------------- | --------------------------------- |
| Blockchain          | Solana Devnet                     |
| Smart Contracts     | Anchor Framework                  |
| Contract Generation | Noah AI                           |
| Reputation Tokens   | Soulbound Tokens (SBTs)           |
| AI Scorer           | Claude API / custom scoring agent |
| Frontend            | React 18 + Tailwind CSS           |
| Wallets             | Phantom / Solflare                |
| Storage             | IPFS / Arweave                    |
| Identity            | DIDs (Decentralized Identifiers)  |
| SDK                 | Solana Web3.js                    |

---

# Repository Structure

```bash
/indie-pool
  /programs
    /indie-pool
      src/lib.rs

  /app
    /src
      /components
      /hooks
      /utils

  /ai-scorer
    scorer.js

  /tests

  README.md
  Anchor.toml
  package.json
```

---

# Smart Contract Architecture

## Core Instructions

### `submit_contribution`

Stores contribution metadata on-chain with pending status.

### `verify_contribution`

Called by the AI oracle to validate and score contributions.

### `mint_reputation_sbt`

Mints a non-transferable reputation token to the contributor.

---

## Escrow Instructions

### `create_project_escrow`

Creates a project funding vault using a PDA.

### `release_milestone`

Releases SOL rewards after milestone verification.

---

# AI Scorer Architecture

The AI scorer service:

1. Receives contribution metadata
2. Sends evaluation prompts to Claude API
3. Returns:

   * score (0–100)
   * reasoning
   * approval status
4. Signs results with an oracle keypair
5. Smart contract validates oracle signature on-chain

---

# Example AI Scoring Logic

```javascript
const scoreContribution = async (contribution) => {
  const prompt = `
    You are evaluating a game dev contribution for quality.

    Type: ${contribution.type}
    Description: ${contribution.description}

    Return JSON:
    {
      score: 0-100,
      reasoning: string,
      approved: boolean
    }
  `;

  const res = await anthropic.messages.create({
    model: 'claude-sonnet-4-20250514',
    max_tokens: 500,
    messages: [{ role: 'user', content: prompt }]
  });

  return JSON.parse(res.content[0].text);
};
```

---

# Local Development Setup

## Prerequisites

* Node.js >= 18
* Rust
* Solana CLI
* Anchor CLI

---

## Clone Repository

```bash
git clone https://github.com/brutalesxyz/indie-pool

cd indie-pool
npm install
```

---

## Build Smart Contracts

```bash
anchor build
```

---

## Deploy to Devnet

```bash
anchor deploy --provider.cluster devnet
```

---

## Run Frontend

```bash
cd app
npm run dev
```

---

## Run AI Scorer

```bash
cd ai-scorer

ANTHROPIC_API_KEY=<key> node scorer.js
```

---

# Environment Variables

```env
ANTHROPIC_API_KEY=your_claude_api_key

SOLANA_RPC_URL=https://api.devnet.solana.com

ORACLE_KEYPAIR_PATH=./oracle-keypair.json

NEXT_PUBLIC_PROGRAM_ID=your_program_id
```

---

# Token Economic Model

## Two-Layer Architecture

### Layer 1 — Reputation SBTs

* Non-transferable
* Merit-based
* Cross-project identity
* Anti-speculative design

### Layer 2 — SOL Escrow Rewards

* Milestone-gated
* Trustless payments
* Contributor compensation
* No speculative token required

---

# Incentive Mechanism

## Contribution Quality Rewards

Only verified high-quality contributions receive:

* Reputation
* Escrow rewards
* Governance eligibility

---

## Cross-Project Reputation

Reputation travels across all Proof, please! projects.

This creates:

* Long-term retention
* Skill-based trust
* Portable creative resumes

---

## Governance (Future Phase)

Future governance model:

* Reputation staking
* One-soul-one-vote mechanics
* Merit-weighted influence
* Anti-whale governance

---

# Why This Model Works

Indie studios need:

* Fast iteration
* Low governance overhead
* Community trust
* Sustainable incentives

Proof, please! aligns directly with those needs.

This is not Play-to-Earn.

This is **Proof-to-Contribute**.

---

# Aesthetic Direction

Cyberpunk. Decentralized. Anti-corporate.

### Design Principles

* Background: `#0D0D1A`
* Cards: `#1A1A2E`
* Primary Accent: Cyan `#00E5FF`
* Secondary Accent: Purple `#7C3AED`
* Monospace typography for on-chain data
* Glitch effects for loading states

---

# Contributing

We welcome contributions in:

* AI scoring improvements
* Security audits
* UI/UX design
* Additional contribution handlers
* Solana integrations
* Reputation mechanics

Open a PR or issue.

All contributors earn reputation on Proof, please! itself.

---

# License

MIT License

See `LICENSE.md`

---

# Future Vision

* Zero-knowledge contribution proofs
* Cross-chain reputation portability
* Decentralized contributor identity
* Reputation staking
* Funding DAOs
* AI-native game collaboration infrastructure

---

# Built for Indie Creators

Proof, please! exists for the developers, artists, musicians, animators, and builders creating games outside traditional gatekeepers.

Creative work deserves verifiable ownership.

Reputation deserves permanence.

Contribution deserves proof.
