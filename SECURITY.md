<!--
SPDX-FileCopyrightText: 2026 Basis Network
SPDX-License-Identifier: Apache-2.0
-->

# Security Policy

This is the default policy for repositories in the `basis-network`
organisation. A repository with its own `SECURITY.md` overrides this one.

## Reporting a vulnerability

Email **security@basisnetwork.com.co** with `[security]` in the subject.
**Never open a public issue for a vulnerability.**

Include what you can: what you did, what happened, what you expected, and the
version and platform. A proof of concept helps and is never required.

| Stage | Target |
|---|---|
| Acknowledgement | 3 working days |
| First assessment | 10 working days |
| Fix, or a stated plan | 90 days from the report |

If you do not hear back within those windows, assume the mail did not arrive
and send it again. We would rather read it twice than not at all.

We agree disclosure timing with you, credit you in the release notes unless
you ask us not to, and publish what was wrong once a fix exists. There is no
bug bounty.

## Scope

Our published tooling talks to a **development network**. LITHOS has no value
and the chain may be reset without notice. That lowers the impact of most
findings, and we will say so in triage — but it is not a reason to leave
something broken. Reports about the network itself, the RPC gateway or the
explorer are in scope at the same address, even where that code is not public.

## Verifying what you downloaded

Release binaries have a SHA-256 committed to their repository under
`checksums/`, and are signed with Sigstore cosign in keyless mode. The checksum is deliberately kept out of the release that serves
the binary: one stored beside the file it describes proves nothing.

## How we run this

Our security assurance programme is documented in
[docs/OPENCHAIN-18974.md](./docs/OPENCHAIN-18974.md), including the controls
that are active and the ones that are not.
