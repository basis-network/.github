<!--
SPDX-FileCopyrightText: 2026 BASE COMPUTING S.A.S.
SPDX-License-Identifier: Apache-2.0
-->

# Open Source Licence Compliance Programme

**Conformance target:** ISO/IEC 5230:2020 (OpenChain Licence Compliance)
**Organisation:** BASE COMPUTING S.A.S. — Basis Network
**Version:** 1.0 · 2026-08-23
**Next review:** 2027-08-23

This document describes how we handle open source licence obligations. It is
deliberately short. We are a small team, and a policy that describes a process
nobody performs is worse than no policy: it is a claim that fails on first
audit.

---

## 1. Programme foundation

### 1.1 Policy

Our open source policy is:

1. **Everything we publish is licensed, per file.** Every file we distribute
   states its copyright holder and its licence, using
   [SPDX](https://spdx.dev/) identifiers, either in the file itself or in a
   `REUSE.toml`. This is verified automatically — see §4.
2. **Everything we consume is licence-checked before it ships.** No third-party
   code enters a distributed artifact without its licence being identified and
   its obligations understood.
3. **Attribution and licence texts travel with the artifact.** Where a licence
   requires notice, that notice is delivered with what we ship, not left on a
   website.
4. **We do not ship what we cannot license.** If the licence of a component is
   unknown, incompatible, or cannot be complied with, the component does not
   go out.

This policy is public, at this URL, and is referenced from every repository we
publish.

### 1.2 Competence

The person named in §2 is responsible for maintaining working knowledge of:

- the licences of the components we distribute;
- the obligations those licences create (notice, source availability,
  modification disclosure, patent grants);
- SPDX identifiers and the REUSE specification;
- the difference between distribution and internal use, since most obligations
  attach to the former.

Refresher: reviewed at each annual programme review, and whenever a component
under an unfamiliar licence is introduced.

### 1.3 Awareness

Licence obligations are stated where the work happens, not only here:

- every repository has a `CONTRIBUTING.md` stating the outbound licence and
  requiring a [DCO](https://developercertificate.org/) sign-off;
- pull request templates require confirmation that new files carry SPDX
  headers;
- CI fails a pull request that introduces an unlicensed file.

---

## 2. Relevant tasks defined and supported

| Role | Person | Responsibility |
|---|---|---|
| Open source programme lead | Sebastián Quintero — contact@basisnetwork.com.co | Policy, decisions on inbound licences, resolution of compliance issues, this document |
| Licence compliance contact | Sebastián Quintero — contact@basisnetwork.com.co | External point of contact for licence questions and claimed violations |

**This is one person.** We state it rather than distributing the same name
across invented roles. The concrete consequence is a single point of failure
for review and response, and it is the main limitation of this programme.

**External enquiries** reach contact@basisnetwork.com.co. Enquiries about
licence compliance are acknowledged within 10 working days.

**Resources:** the automated controls in §4 run on the organisation's GitHub
Actions allowance and require no purchase. Time for review is allocated by the
programme lead as part of release work — a release is not published until its
compliance checks pass, which is enforced mechanically rather than by
intention.

---

## 3. Open source content review and approval

### 3.1 What we distribute

Each repository documents what it ships and where it came from. For binaries,
that includes the toolchain and the commit they were built from, when known —
and says so explicitly when not known, rather than leaving a blank.

### 3.2 Inbound components

Before a third-party component becomes part of anything we distribute:

1. its licence is identified and recorded with an SPDX identifier;
2. its obligations are checked against how we intend to distribute it;
3. incompatible or unidentifiable licences are rejected.

Our currently published artifacts are statically linked binaries built from
our own workspace, plus shell and documentation. The dependency review for
those lives with the build of `basis-core`.

### 3.3 Outbound licence

**Apache-2.0** unless stated otherwise in the repository. Chosen for its
express patent grant, which matters for post-quantum cryptographic
implementations.

### 3.4 Contributions in

The DCO. We do not require a copyright assignment or a CLA: contributors keep
their copyright and certify that they have the right to contribute what they
contribute.

---

## 4. Compliance artifact creation and delivery

For each release we produce and deliver, with the artifact:

| Artifact | Where |
|---|---|
| Licence text | `LICENSE` and `LICENSES/` in the repository |
| Copyright and licence, per file | SPDX headers, or `REUSE.toml` |
| Attribution notice | `NOTICE` |
| Bill of what is shipped and its provenance | `README.md` and `CHANGELOG.md` |
| Integrity | `checksums/<tag>/`, committed to git before the release is published |

**Verification is automated and blocking:**

- `reuse lint` runs in CI on every push and pull request. It fails if any file
  lacks copyright or licence information. Repositories carry a public
  [REUSE](https://reuse.software/) badge reflecting live status.
- The release workflow verifies every published asset against the checksums
  committed in git, and fails the release if they disagree.

Automation is the point. A manual step performed by one person is a step that
gets skipped under pressure.

---

## 5. Understanding open source community engagement

We contribute upstream where our changes are of general use, under the
upstream project's own licence and contribution process. Where we maintain
modifications to an upstream project for our own deployment, we keep them as
patches against pinned upstream commits rather than as a divergent fork, which
keeps the boundary between their work and ours legible.

Employees contributing to open source projects on behalf of the organisation
do so under this policy and with the programme lead's knowledge.

---

## 6. Adherence to the specification

This programme is reviewed **annually**, and whenever:

- a new repository is published;
- a component under an unfamiliar licence is introduced;
- a compliance issue is reported.

The review checks that this document still describes what actually happens.
Where it does not, the document is corrected — not the other way round.

**Self-certification status:** this document is prepared to support
self-certification against ISO/IEC 5230:2020. The declaration itself, when
made, is signed by the programme lead and published here.

## Reporting a compliance concern

Email **contact@basisnetwork.com.co**. Tell us what you believe is wrong and
where. Acknowledgement within 10 working days.
