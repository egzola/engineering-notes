# Engineering Notes

This repository contains technical notes, investigations, and system-level observations derived from real-world work.

## Scope

Focus areas include:

- Bitcoin infrastructure and wallet behavior
- HD wallet derivation (BIP32 / BIP39 / BIP44)
- System constraints in managed environments (e.g. Umbrel)
- Runtime behavior vs expected specification

## Approach

The goal is not to document features, but to understand:

- how systems actually behave
- where implementations diverge from specifications
- how assumptions break in real environments

All notes are based on direct observation, testing, or debugging.

## Structure

- `umbrel/` → app integration, runtime constraints, deployment behavior
- `bitcoin/` → wallet derivation, address generation, edge cases

## Notes

- [Umbrel App Submission](./umbrel/umbrel-app-submission.md)
- [AirGap Derivation Issue](./wallets/airgap-vault-derivation-path-index.md)
