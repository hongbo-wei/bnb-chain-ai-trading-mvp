---
title: "BNB Chain AI Trading MVP"
subtitle: "Whitepaper"
author: "Hongbo Wei"
date: "2026-01-01"
---

# Abstract
BNB Chain AI Trading MVP is an agentic system that turns on-chain signals into safe, explainable trade intent. It combines semantic search over blockchain data, risk-aware advice generation, and policy-gated execution planning. The system is designed for transparency, auditability, and rapid iteration on BNB Chain.

# Problem
On-chain markets move quickly, but most traders and teams rely on fragmented tooling: data dashboards, signal bots, and manual execution scripts. These tools are rarely connected to a consistent risk policy or an auditable decision trail. The result is poor transparency, low trust, and limited automation at scale.

# Solution
BNB Chain AI Trading MVP delivers an end-to-end pipeline built around three specialized agents and an orchestration layer:
- Data Agent for ingesting and embedding on-chain signals
- Advisor Agent for generating risk-aware recommendations
- Execution Agent for deterministic, safety-checked execution planning
- MCP Orchestrator for policy enforcement and decision logging

# System Architecture
- API: FastAPI endpoints for ingestion, search, insights, advice, execution, and scoring
- Orchestrator: MCP-style routing with explicit policy gates
- Storage: Postgres + pgvector for events, embeddings, and decision logs
- On-chain integration: optional RPC execution on BNB Chain

# Core Components
## Data Agent
- Ingests on-chain events (BscScan or Bitquery)
- Extracts metadata and tags
- Creates embeddings for semantic search

## Advisor Agent
- Accepts risk profile and objective
- Returns recommendation, allocation mix, confidence, and rationale
- Supports personalization from user trades and holdings

## Execution Agent
- Generates a deterministic execution plan
- Enforces gas, slippage, and position size constraints
- Runs in dry-run mode by default

## MCP Orchestrator
- Routes requests by intent
- Applies policy gates
- Stores decision logs for auditability

# Workflow
1. Ingest on-chain data
2. Generate insights and semantic search results
3. Produce a risk-aware recommendation
4. Build a policy-compliant execution plan
5. Score readiness across data, advisor, and execution

# Security and Policy Controls
- Policy modes: read_only, paper_trade, execute_enabled
- Asset and action allowlists
- Max gas, max position size, and slippage bounds
- Decision logging for traceability

# On-Chain Deployment
The DecisionLog contract is deployed and verified on BSC mainnet:
- Contract: https://bscscan.com/address/0x74B9CFd32552630B0bfEF0976Fc1d8198f830242
- Source: `chain/contracts/DecisionLog.sol`

# Evaluation and Metrics
A built-in scorecard measures readiness across:
- Data ingestion and query performance
- Recommendation quality and confidence
- Execution safety and policy compliance

# Market and Use Cases
- Wallets and frontends that need explainable trade intent
- Traders seeking risk-aware decision support
- Protocols and funds requiring audited automation flows

# Roadmap
See `docs/roadmap-6-month.md` for detailed milestones and delivery plan.

# Open Source
Repository: https://github.com/hongbo-wei/bnb-chain-ai-trading-mvp

# Disclaimer
This project is for research and demonstration only and does not provide financial advice.
