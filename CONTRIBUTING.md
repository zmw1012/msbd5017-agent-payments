# Contributing

## Secrets and safety

- Never commit `.env`, private keys, seed phrases, API secrets, RPC secrets, logs, or build outputs.
- Copy `.env.example` to a local `.env` and fill values only on your machine.
- No real funds, real customer information, or production credentials.
- Do not deploy or use mainnet / production assets for this coursework project.

## Workflow

1. Work on a feature or docs branch; keep `main` reviewable.
2. Prefer docs-first scope changes: update `docs/` and ADRs (for example `docs/adr/0001-project-scope.md`) when research or payment-path assumptions change.
3. Do not claim the Vault path is an official x402 Exact EVM implementation unless it is actually implemented as a supported scheme.
4. Vault work starts only after the Phase 1 official x402 Base Sepolia test-USDC baseline settles successfully.

## Pull requests

- Describe what changed and why.
- Confirm no secrets are included.
- Link related docs/ADR updates when scope shifts.
