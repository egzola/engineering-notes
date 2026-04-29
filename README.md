# Engineering Notes

This repository contains technical notes, investigations, and system-level observations derived from real-world work.

Many of these notes come from building, debugging and shipping practical projects such as:

- **bitBoard** — customizable crypto price dashboard for Umbrel
- **bitBalance** — private Bitcoin wallet balance tracker for Umbrel

## Scope

Focus areas include:

- Bitcoin infrastructure and wallet behavior
- HD wallet derivation (BIP32 / BIP39 / BIP44)
- System constraints in managed environments (e.g. Umbrel)
- Runtime behavior vs expected specification
- Dockerized deployments and self-hosted services
- Real-world software packaging and release workflows

## Approach

The goal is not to document features, but to understand:

- how systems actually behave
- where implementations diverge from specifications
- how assumptions break in real environments

All notes are based on direct observation, testing, or debugging.

## Structure

- `umbrel/` → app integration, runtime constraints, deployment behavior
- `wallet/` → wallet derivation, address generation, edge cases
- `docker/` → image builds, multi-arch, packaging notes
- `systems/` → practical runtime observations and infrastructure behavior

## Notes

- [bitBalance Umbrel Submission](./umbrel/bitbalance-submission.md)
- [bitBoard Umbrel Submission](./umbrel/bitboard-submission.md)
- [AirGap Derivation Issue](./wallet/airgap-vault-derivation-path-index.md)
  
## Philosophy

Theory matters.  
Observed behavior matters more.

Understanding the path is often more valuable than only seeing the result.
