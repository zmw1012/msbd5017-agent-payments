# Experiment design

## Research question

Within a payment path demonstrated to settle successfully, can an on-chain Vault maintain the budget ceiling during concurrent payments and revocation races, and at what execution cost?

## Controlled variables

The official x402 baseline and the experimental Vault-controlled path share:

- One mock Merchant API (not multiple APIs)
- Same price
- Same network (Base Sepolia)
- Same test asset (test USDC)
- Same request sequence

## Prerequisites

1. Phase 1: demonstrate an official x402 Base Sepolia test-USDC payment that settles successfully.
2. Only then begin Vault development and Vault-path experiments.

## Future metrics (post-Vault)

- Budget ceiling integrity under concurrent payments
- Budget ceiling integrity under revocation races
- Execution cost (for example gas)

## Naming honesty

The Vault path is experimental. Do not describe it as an official x402 Exact EVM implementation unless it is actually implemented as a supported scheme.

## Safety

Experiments use testnet/mock assets only. No real funds, real customer information, or production credentials.
