# PQCrypta Discovery Agent — Signing Keys (out-of-band trust anchor)

The discovery-agent release artifacts are **hybrid-signed** — a classical **Ed25519**
signature and a post-quantum **ML-DSA-65 (NIST FIPS 204)** signature over a
`SHA256SUMS` manifest that also covers the agent's own CBOM.

This repository is the **out-of-band publication** of the signing public keys, so you
can bootstrap trust from a *different origin* than the one that serves the binaries
(`api.pqcrypta.com`). Cross-check the fingerprints below against the keys the installer
or download page hands you — if they differ, do not run the binary.

## Key fingerprints (SHA-256 of the public key file)

| Key | Algorithm | SHA-256 fingerprint |
|-----|-----------|---------------------|
| `pqcrypta-agent-signing.pub` | Ed25519 (classical) | `c46d2fac1a3039e9a8aee8637e21eb39d6558da25a5814b97a29f7fb9237dee0` |
| `pqcrypta-agent-signing-mldsa.pub` | ML-DSA-65 / FIPS 204 (post-quantum) | `68ceb2dc10b4789eabef1f903d879408a15b3fe8cf2dc15eec3cb839fb981ddf` |

## Verify a fingerprint

```bash
curl -sO https://api.pqcrypta.com/stream/downloads/discovery-agent/verify/pqcrypta-agent-signing.pub
sha256sum pqcrypta-agent-signing.pub   # must equal the Ed25519 fingerprint above
```

The public keys themselves are committed here alongside their fingerprints. Full
verification instructions (classical + post-quantum, Linux/macOS/Windows) are in the
agent's [Complete Guide](https://pqcrypta.com/discovery/guide.php#verify).
