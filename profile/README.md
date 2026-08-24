<!--
SPDX-FileCopyrightText: 2026 Basis Network
SPDX-License-Identifier: Apache-2.0
-->

# Basis Network

Blockchain infrastructure for industrial companies. Built in Medellín,
Colombia.

Basis is a **permissioned Layer 1** that signs with **ML-DSA-65** (FIPS 204),
the post-quantum signature standard — not with the elliptic curves every other
chain uses. That single decision is why our tooling exists: no Ethereum wallet
can produce a valid transaction for this network, so the wallet, the CLI and
the SDK had to be written rather than adopted.

## What is here

| Repository | What it is |
|---|---|
| [basis-cli](https://github.com/basis-network/basis-cli) | The command-line client. Wallets, queries, transfers, contract deployment. |

Most of the stack — the node, the wallet extension, the explorer, the faucet
and the infrastructure — is not public yet. What we open, we open properly:
licensed per file, checksummed, signed, and documented including the parts that
do not work.

## The network

`basis-devnet-6969` is a **development network**. LITHOS has no value, the
chain may be reset without notice, and nothing here is production. Endpoints,
tokens and chain parameters are documented at
[basisnetwork.com.co/docs](https://basisnetwork.com.co/docs).

## How we work in the open

- **Apache-2.0**, with a [DCO](https://developercertificate.org/) sign-off on
  every commit.
- **[REUSE](https://reuse.software/) 3.3 compliant** — every file states its
  copyright and licence, and CI fails if one does not.
- **Releases are verifiable.** Checksums live in git, where they have a commit
  and a diff; binaries live in releases. Checking one against the other is the
  point. Assets are signed with [Sigstore](https://www.sigstore.dev/) cosign in
  keyless mode — no private key exists to be stolen.
- **Known problems are written down.** Every repository documents the rough
  edges of what it ships. A tool that hides them costs its users an afternoon
  each.

Our open source programme is documented under
[`docs/`](https://github.com/basis-network/.github/tree/main/docs):
[licence compliance](https://github.com/basis-network/.github/blob/main/docs/OPENCHAIN-5230.md)
and [security assurance](https://github.com/basis-network/.github/blob/main/docs/OPENCHAIN-18974.md),
against ISO/IEC 5230 and ISO/IEC 18974, with the
[records](https://github.com/basis-network/.github/blob/main/docs/OPENCHAIN-PROGRAMME-RECORDS.md)
both standards require. The OpenChain self-certification checklists are
published answered —
[5230](https://github.com/basis-network/.github/blob/main/docs/OPENCHAIN-5230-CHECKLIST.md),
[18974](https://github.com/basis-network/.github/blob/main/docs/OPENCHAIN-18974-CHECKLIST.md)
— including the items we have **not** met, because a conformance claim you
cannot check is worth less than a gap you can.

## Contact

**contact@basisnetwork.com.co** — including for security reports, which should
never go in a public issue. See each repository's `SECURITY.md`.

[basisnetwork.com.co](https://basisnetwork.com.co)
