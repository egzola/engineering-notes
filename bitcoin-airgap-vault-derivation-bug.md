# AirGap Vault – Derivation Path Index Issue

## Context

While validating wallet address derivation, a mismatch was observed between AirGap Vault and a reference implementation.

Reference tool used:
Ian Coleman BIP39 tool (offline)

## Method

- Generated address[0] using the same mnemonic (with passphrase)
- Compared results between:
  - AirGap Vault
  - Ian Coleman BIP39 tool

## Observation

The first derived address did not match.

## Investigation

Derivation paths were analyzed.

Expected:
m/84'/0'/0'/0/0

Observed (AirGap):
m/84'/0'/1'/0/0

The account index was incremented to 1 instead of starting at 0.

## Impact

- Derives a completely different address set
- Wallet appears empty or incorrect
- Potential confusion for users relying on deterministic derivation

## Notes

The issue appears related to handling of account index when using BIP39 passphrases.

Behavior suggests implicit increment instead of respecting standard derivation starting point.

## Status

- Issue reported to AirGap developers
- Acknowledged as unintended behavior
- Fix planned for a future release
