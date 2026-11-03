# Security

## Project boundaries

- Testnet and mock environments only (for example Base Sepolia test USDC).
- No real funds.
- No real customer information.
- No production credentials.

## Secrets handling

- Keep secrets in a local `.env` copied from `.env.example`.
- Never commit `.env`, private keys, seed phrases, API secrets, RPC secrets, logs, or build outputs.
- Git must ignore those paths (see root `.gitignore`).
- Do not paste private keys or seed phrases into docs, issues, PRs, or chat logs that become part of the repository history.

## Scope reminder

- One mock Merchant API for both the official x402 baseline and the experimental Vault path.
- Vault development starts only after the Phase 1 baseline settles successfully.
- Do not claim the Vault path is an official x402 Exact EVM implementation unless it is actually implemented as a supported scheme.
