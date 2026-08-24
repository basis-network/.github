<!--
SPDX-FileCopyrightText: 2026 Basis Network
SPDX-License-Identifier: Apache-2.0
-->

# Open Source Security Assurance Programme

**Conformance target:** ISO/IEC 18974:2023 (OpenChain Security Assurance)
**Organisation:** Basis Network
**Version:** 1.1 · 2026-08-24
**Next review:** 2027-08-24
**Records:** [programme records](./OPENCHAIN-PROGRAMME-RECORDS.md) ·
**Self-certification:** [completed checklist](./OPENCHAIN-18974-CHECKLIST.md)

Companion to the [licence compliance programme](./OPENCHAIN-5230.md). Same
principle: this describes what we actually do. Where a control does not exist
yet, it says so.

---

## 1. Programme foundation

### 1.1 Policy

1. **Known vulnerabilities in what we ship are our problem**, whether the code
   is ours or came from upstream.
2. **There is one way in for reports, it is public, and it is answered.** See
   §4 for the timelines we hold ourselves to.
3. **What we distribute can be verified by whoever receives it.** Checksums in
   version control, signatures from a transparency log, and provenance stated
   for every artifact — including "we do not know", where that is the truth.
4. **No secret material is ever committed, logged, or embedded in an
   artifact.** Names of secrets may appear; values never do.
5. **Known weaknesses are documented rather than hidden.** A user who knows
   about a limitation can work around it. One who does not, cannot.

### 1.2 Competence

The person named in §2 maintains working knowledge of:

- the vulnerability landscape of the components we distribute;
- how to receive, triage and coordinate disclosure of a report;
- the cryptographic properties of what we ship — this is a post-quantum
  signature implementation, and the failure modes are not the usual ones;
- supply-chain integrity: signing, checksums, dependency pinning, and the
  build provenance of a released binary.

### 1.3 Awareness

- every public repository has a `SECURITY.md` with the reporting address and
  the response timelines;
- issue templates route security reports away from public issues, explicitly;
- every repository documents the known limitations of what it ships.

---

## 2. Relevant tasks defined and supported

| Role | Person | Responsibility |
|---|---|---|
| Security assurance lead | Sebastian Tobar Quintero — contact@basisnetwork.com.co | Policy, triage, remediation decisions, coordinated disclosure |
| Security contact | Sebastian Tobar Quintero — contact@basisnetwork.com.co | Receives reports |
| Second maintainer | David Alejandro Blandón Román — contact@basisnetwork.com.co | Equal access to the repositories: can publish a fix and a release while the assurance lead is unavailable |

**Triage and disclosure remain one person's**, and that is the main limitation
of this programme. Reaching two maintainers changed one thing and not the
other: a fix can now be published while the lead is away, but reports are still
read and triaged by one person, so a report arriving during an absence can
still wait. We state the timelines in §4 anyway, and we ask reporters to resend
rather than assume silence is a decision.

**Resources:** the automated controls in §3 run in CI at no cost and are
blocking, so they cannot be skipped under time pressure. Remediation time is
allocated ahead of feature work.

---

## 3. Open source content review and remediation

### 3.1 Identifying vulnerabilities

| Control | Where | Status |
|---|---|---|
| Static analysis of shell | `shellcheck` in CI, blocking | active |
| Supply-chain posture scoring | [OpenSSF Scorecard](https://scorecard.dev/), published publicly | active |
| Dependency pinning | GitHub Actions pinned to commit SHAs, never tags | active |
| Pinned-dependency freshness | Dependabot, weekly | active |
| Licence/attribution integrity | `reuse lint` in CI, blocking | active |
| Release integrity | Published assets verified against checksums committed in git | active |
| Artifact signing | Sigstore cosign, keyless, in the release workflow | active |
| Dependency vulnerability scanning of the node workspace | `cargo audit` in the `basis-core` build | not yet public |
| Fuzzing | — | not implemented |

We publish what is active and name what is not. A programme that lists
aspirations as controls fails the first time someone checks.

### 3.2 Remediation

On confirming a vulnerability in something we distribute:

1. assess severity and reachability in our artifacts;
2. fix, or state a plan with a date;
3. release, with the fix named in the `CHANGELOG`;
4. notify the reporter, and credit them unless they decline.

Where the vulnerability is upstream, we report it upstream and follow their
disclosure process rather than publishing first.

### 3.3 Integrity of what we ship

The controlling design decision: **the checksum and the binary travel by
different routes.** Checksums are committed to git, where they carry a commit,
an author, a date and a reviewable diff. Binaries are attached to releases. A
checksum stored beside the file it describes proves nothing, because whoever
can replace one can replace the other.

Signing uses cosign in **keyless** mode. There is no private key: the signing
identity is the release workflow's OIDC token and the certificate is recorded
in the public Rekor transparency log. A key that does not exist cannot be
stolen, and the trust anchor is a public log rather than our own good custody.

---

## 4. Documented response process

Published in each repository's `SECURITY.md`:

| Stage | Target |
|---|---|
| Acknowledgement | 3 working days |
| First assessment | 10 working days |
| Fix, or a stated plan | 90 days from the report |

Coordinated disclosure: we agree timing with the reporter, credit them by
default, and publish what was wrong once a fix is available. There is no bug
bounty, and we say so rather than letting reporters assume otherwise.

**Scope note.** Our published tooling talks to a development network. That
lowers the impact of most findings and we will say so in triage — but it is
not a reason to leave something broken, and reports about the network itself
are in scope at the same address.

---

## 5. Adherence to the specification

Reviewed **annually**, and whenever:

- a new artifact is published;
- a vulnerability is reported;
- a control in §3.1 changes status.

The review checks that this document still describes what happens. Where it
does not, the document is corrected.

Programme participants, assessed competence, scope, metrics, component records
including known vulnerabilities and action taken, and the review log are kept
in the [programme records](./OPENCHAIN-PROGRAMME-RECORDS.md).

**Self-certification status:** the OpenChain self-certification checklist for
ISO/IEC 18974:2023 has been completed and is published at
[`OPENCHAIN-18974-CHECKLIST.md`](./OPENCHAIN-18974-CHECKLIST.md). As of the
2026-08-24 review, **30 of 35 items are met and five are open**, all five
closing on a single acknowledgement. We do not claim conformance until they do.
The declaration is signed by the security assurance lead and published here.

## Reporting

**contact@basisnetwork.com.co**, with `[security]` in the subject. Never in a
public issue.
