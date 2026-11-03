# ADR 0001: Project scope

## Status

Accepted (Phase 0)

## Context

MSBD5017 group project: *Agent Payments: On-chain Budget Control for x402-paid APIs*. We need a fixed experimental scope so baseline and Vault comparisons are fair and claims stay accurate.

## Decision

1. Use **one mock Merchant API**, not multiple APIs.
2. The official x402 baseline and the experimental Vault-controlled path use the **same** API, price, network, test asset, and request sequence.
3. **Phase 1** first demonstrates an official x402 Base Sepolia test-USDC payment.
4. Vault development starts **only after** that baseline settles successfully.
5. The Vault path must **not** be described as an official x402 Exact EVM implementation unless it is actually implemented as a supported scheme.
6. No real funds, real customer information, or production credentials will be used.
7. `.env`, private keys, seed phrases, API secrets, RPC secrets, logs, and build outputs must be ignored by Git.

## Consequences

- Implementation order is gated: repo init → x402 baseline settlement → Vault → experiments.
- Documentation and marketing language must distinguish official x402 from the experimental Vault path.
- Contributors must treat secrets and production data as out of scope for this repository.
