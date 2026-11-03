# Agent Payments: On-chain Budget Control for x402-paid APIs

HKUST MSBD5017 Blockchain group project (three-person team).

## What this project is about (plain language)

APIs can charge for each request. **x402** is a payment protocol that lets a client pay on-chain (on a blockchain) before the API returns a result. We will first show that a normal x402 payment works on a **test network** using **fake test money** (not real USD).

After that works, we will add an on-chain **Vault**: a smart contract that holds a spending budget (a ceiling). The research question is whether that Vault can keep the budget limit correct when many payments happen at once or when a budget is revoked mid-flight, and how much blockchain gas (execution cost) that takes.

## Research question

Within a payment path demonstrated to settle successfully, can an on-chain Vault maintain the budget ceiling during concurrent payments and revocation races, and at what execution cost?

**Settle successfully** means the on-chain payment completes and the mock API accepts it. **Concurrent payments** means several payments at the same time. **Revocation races** means trying to cancel/limit the budget while payments are still in flight.

## Important terms

| Term | Meaning here |
|------|----------------|
| Mock Merchant API | A fake paid API we control for experiments (not a real product) |
| Base Sepolia | A public **test** blockchain network (Base’s Sepolia testnet) — not mainnet |
| Test USDC | A test stablecoin used on the test network — **not real money** |
| Official x402 baseline | The standard x402 payment path we must get working first |
| Vault path | Our later experimental budget-control path (not claimed as official x402 Exact EVM unless we actually implement a supported scheme) |

## Scope constraints

1. We use **one mock Merchant API**, not multiple APIs.
2. The official x402 baseline and the experimental Vault-controlled path use the **same** API, price, network, test asset, and request sequence.
3. **Phase 1** first demonstrates an official x402 Base Sepolia test-USDC payment.
4. Vault development starts **only after** that baseline settles successfully.
5. The Vault path must **not** be described as an official x402 Exact EVM implementation unless it is actually implemented as a supported scheme.
6. No real funds, real customer information, or production credentials are used.
7. `.env`, private keys, seed phrases, API secrets, RPC secrets, logs, and build outputs must stay out of Git (see `.gitignore`).

## Repository layout

```
.
├── apps/merchant-api     # One mock paid API (shared by both paths)
├── apps/agent-client     # Client that calls the API / pays
├── packages/shared       # Shared types/constants (later)
├── contracts             # Vault smart contract (after Phase 1)
├── experiments           # Concurrency / revocation / cost tests (later)
├── scripts               # Helper scripts (later)
└── docs                  # Architecture, experiments, security, ADRs
```

## Phase roadmap

1. **Phase 0 (current)** — Repository skeleton and docs only. No payment code yet.
2. **Phase 1** — Official x402 Base Sepolia test-USDC payment against the one mock Merchant API.
3. **Later** — Vault only after baseline settlement; then experiments on concurrent payments, revocation races, and gas cost.

## Local setup notes (Phase 0)

- Do **not** install dependencies yet for this phase.
- Do **not** create a real `.env` with secrets in the repo.
- When secrets are needed later: copy `.env.example` → `.env` on your machine only (`.env` is gitignored).
- See [CONTRIBUTING.md](CONTRIBUTING.md) and [docs/security.md](docs/security.md).

## Safety

Testnet / mock only. Never commit private keys, seed phrases, API keys, RPC secrets, or a populated `.env`.
