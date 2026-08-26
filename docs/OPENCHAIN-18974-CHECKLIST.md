<!--
SPDX-FileCopyrightText: 2026 Basis Network
SPDX-License-Identifier: Apache-2.0
-->

# OpenChain ISO/IEC 18974 Self-Certification Checklist — Basis Network

**Standard:** ISO/IEC 18974:2023 (OpenChain Security Assurance)
**Organisation:** Basis Network
**Completed:** 2026-08-24 by Sebastian Tobar Quintero, security assurance lead
**Scope:** as stated in [§1.2 of the programme records](./OPENCHAIN-PROGRAMME-RECORDS.md#12-scope-statement)

The OpenChain security assurance self-certification checklist, answered, with a
pointer to the evidence for each item. This is a **self-certification**: Basis
Network is solely responsible for the accuracy of the statements below.

Companion to the [ISO/IEC 5230 checklist](./OPENCHAIN-5230-CHECKLIST.md).

---

## Section 4.1.1 — Policy

- [x] **We have a documented policy governing the open source security assurance of Supplied Software.**
  → [Programme §1.1](./OPENCHAIN-18974.md#11-policy) — five rules, including that no secret value is ever committed and that known weaknesses are documented rather than hidden.

- [x] **We have a documented procedure to communicate the existence of the open source policy to all Program Participants.**
  → [Records §2.1](./OPENCHAIN-PROGRAMME-RECORDS.md#21-awareness-record) — where each rule is stated and how it reaches participants.

## Section 4.1.2 — Roles, competence and review

- [x] **We have identified the roles and responsibilities that affect the performance and effectiveness of the Program.**
  → [Programme §2](./OPENCHAIN-18974.md#2-relevant-tasks-defined-and-supported) — role table, which records that triage and disclosure remain one person's.

- [x] **We have identified and documented the competencies required for each role.**
  → [Programme §1.2](./OPENCHAIN-18974.md#12-competence) — four areas, including the cryptographic properties of a post-quantum signature implementation, whose failure modes are not the usual ones.

- [x] **We have identified and documented a list of Program Participants and how they fill their respective roles.**
  → [Records §2](./OPENCHAIN-PROGRAMME-RECORDS.md#2-programme-participants-and-assessed-competence) — named participants, roles held, and what each role actually covers.

- [x] **We have documented the assessed competence for each Program Participant.**
  → [Records §2](./OPENCHAIN-PROGRAMME-RECORDS.md#2-programme-participants-and-assessed-competence) — assessment, date and evidence. The second maintainer is recorded as *not yet assessed*, with the reason.

- [x] **We have a way to document periodic reviews and changes made to our processes.**
  → [Records §7](./OPENCHAIN-PROGRAMME-RECORDS.md#7-review-record) — review record with date, reviewer, scope and outcome. Process changes also arrive as reviewable pull requests in public git history.

- [x] **We have a way to verify that our processes align with current company best practices and staff assignments.**
  → [Records §7](./OPENCHAIN-PROGRAMME-RECORDS.md#7-review-record) plus two external measures we do not grade ourselves on: [OpenSSF Scorecard](https://scorecard.dev/viewer/?uri=github.com/basis-network/basis-cli) and [OpenSSF Best Practices](https://www.bestpractices.dev/projects/14224). Both are scored by someone else's criteria.

## Section 4.1.3 — Awareness

- [x] **Our Program Participants are aware of the open source security assurance policy and where to find it.**
  → [Records §2.1](./OPENCHAIN-PROGRAMME-RECORDS.md#21-awareness-record) — public, communicated on the recorded dates, and acknowledged by both participants.

- [x] **Our Program Participants are aware of relevant open source objectives.**
  → Same record. The objectives are the scope statement and what each repository ships.

- [x] **Our Program Participants are aware of contributions expected to ensure the effectiveness of the Program.**
  → Same record. Stated in `CONTRIBUTING.md` and enforced on every pull request by blocking CI.

- [x] **Our Program Participants are aware of the implications of failing to follow the Program requirements.**
  → Same record. The implication is mechanical rather than disciplinary: a pull request that fails a security check cannot be merged.

## Section 4.1.4 — Scope, metrics and evidence

- [x] **We have a written statement clearly defining the scope and limits of the Program.**
  → [Records §1.2](./OPENCHAIN-PROGRAMME-RECORDS.md#12-scope-statement) — in, out, and why. The `basis` binary is explicitly outside it.

- [x] **We have a set of metrics to measure Program performance.**
  → [Records §4](./OPENCHAIN-PROGRAMME-RECORDS.md#4-programme-metrics) — nine metrics with their source and their reading. Two have no data yet and say so rather than showing a zero that would read as a result.

- [x] **We have Documented Evidence from each review, update, or audit to demonstrate continuous improvement.**
  → [Records §7](./OPENCHAIN-PROGRAMME-RECORDS.md#7-review-record) — the 2026-08-24 review records what it found missing and what was created in response, which is the improvement rather than a claim of one.

## Section 4.1.5 — Identifying and handling risk

- [x] **We have a method to identify structural and technical threats to the Supplied Software.**
  → [`basis-cli` assurance case](https://github.com/basis-network/basis-cli/blob/main/docs/ASSURANCE-CASE.md) — a threat model of six threats mapped to Saltzer & Schroeder principles and to CWE identifiers, with the trust boundaries named.

- [x] **We have a method for detecting existence of Known Vulnerabilities in Supplied Software.**
  → [Programme §3.1](./OPENCHAIN-18974.md#31-identifying-vulnerabilities) — control table: `shellcheck`, CodeQL, Scorecard and Dependabot, each recorded as active or not implemented.

- [x] **We have a method for following up on identified Known Vulnerabilities.**
  → [Programme §3.2](./OPENCHAIN-18974.md#32-remediation) — four steps from severity assessment to crediting the reporter; recorded in [Records §3.5](./OPENCHAIN-PROGRAMME-RECORDS.md#35-known-vulnerabilities-and-action-taken).

- [x] **We have a method to communicate identified Known Vulnerabilities to customer base when warranted.**
  → GitHub security advisories, the `CHANGELOG` entry naming the fix, and coordinated disclosure under [Programme §4](./OPENCHAIN-18974.md#4-documented-response-process).

- [x] **We have a method for analyzing Supplied Software for newly published Known Vulnerabilities post release of the Supplied Software.**
  → Dependabot weekly against pinned components, Scorecard on a schedule, and CodeQL on every push — all of which run after release, not only before it.

- [x] **We have a method for continuous and repeated Security Testing is applied for all Supplied Software before release.**
  → Blocking CI on every push and pull request: `shellcheck`, CodeQL, `reuse lint`, the test suite, and statement coverage with a 90 % floor. Repeated, not sampled.

- [x] **We have a method to verify that identified risks will have been addressed before release of Supplied Software.**
  → Branch protection on `main` with required status checks and linear history; the release workflow additionally verifies every published asset against checksums committed to git and fails the release on disagreement.

- [x] **We have a method to export information about identified risks to third parties as appropriate.**
  → Three channels, all public: GitHub security advisories in a standard machine-readable format; the [known gaps section](https://github.com/basis-network/basis-cli/blob/main/docs/ASSURANCE-CASE.md) of the assurance case; and the defects documented in `basis-cli`'s own `README.md`. Signing certificates are exportable from the public Rekor transparency log.

## Section 4.2.1 — Receiving reports

- [x] **We have a method to allow third parties to make Known Vulnerability or Newly Discovered Vulnerability enquires.**
  → `SECURITY.md` in every repository: `security@basisnetwork.com.co` with `[security]` in the subject, plus GitHub private security advisories. Issue templates route security reports away from public issues.

- [x] **We have an internal documented procedure for responding to third party Known Vulnerability or Newly Discovered Vulnerability inquiries.**
  → `SECURITY.md`, "How a report is handled" — six steps — with the timelines in [Programme §4](./OPENCHAIN-18974.md#4-documented-response-process): acknowledgement 3 working days, first assessment 10, fix or stated plan 90.

## Section 4.2.2 — Staffing and expertise

- [x] **We have documented the people, group or functions related to the Program.**
  → [Programme §2](./OPENCHAIN-18974.md#2-relevant-tasks-defined-and-supported) and [Records §2](./OPENCHAIN-PROGRAMME-RECORDS.md#2-programme-participants-and-assessed-competence).

- [x] **We have ensured the identified Program roles have been properly staffed and adequate funding has been provided.**
  → [Programme §2, "Resources"](./OPENCHAIN-18974.md#2-relevant-tasks-defined-and-supported) — controls run in CI at no cost and are blocking, so they cannot be skipped under time pressure; remediation time is allocated ahead of feature work.

- [x] **We have ensured expertise available is to address identified Known Vulnerabilities.**
  → [Programme §1.2](./OPENCHAIN-18974.md#12-competence) and [Records §2](./OPENCHAIN-PROGRAMME-RECORDS.md#2-programme-participants-and-assessed-competence) — assessed competence covering triage, coordinated disclosure, supply-chain integrity and the cryptography we ship.

- [x] **We have a documented procedure that assigns internal responsibilities for Security Assurance.**
  → [Programme §2](./OPENCHAIN-18974.md#2-relevant-tasks-defined-and-supported) — role table assigning policy, triage, remediation decisions and coordinated disclosure.

## Section 4.3.1 — Recording what we use

- [x] **We have a documented procedure ensuring all Open Source Software used in the Supplied Software is continuously recorded across the lifecycle of the Supplied Software, including an archive.**
  → [Records §3.1](./OPENCHAIN-PROGRAMME-RECORDS.md#31-the-record-and-how-it-is-kept) for the procedure and its update trigger; [Records §5](./OPENCHAIN-PROGRAMME-RECORDS.md#5-compliance-artifact-archive) for the archive, retained for the life of the repository.

- [x] **We have open source component records for the Supplied Software which demonstrate the documented procedure was properly followed.**
  → [Records §3.2](./OPENCHAIN-PROGRAMME-RECORDS.md#32-build-and-verification-components) — six components, each pinned to a full commit SHA, with licence and obligation. The Supplied Software has no third-party runtime dependencies.

## Section 4.3.2 — Vulnerabilities in components

- [x] **We have a documented procedure for handling detection and resolution of Known Vulnerabilities for the Open Source Software components of the Supplied Software.**
  → [Programme §3.1 and §3.2](./OPENCHAIN-18974.md#3-open-source-content-review-and-remediation) — detection controls and the four remediation steps, including reporting upstream and following their disclosure process rather than publishing first.

- [x] **We have open source component records for the Supplied Software which track identified Known Vulnerabilities and action(s) taken (including even if no action was required).**
  → [Records §3.5](./OPENCHAIN-PROGRAMME-RECORDS.md#35-known-vulnerabilities-and-action-taken) — the table is empty because nothing has been identified; the three routes by which an entry arrives are documented above it.

## Section 4.4.1 — Adherence

- [x] **We have documentation confirming that the Program meets all the requirements of this specification.**
  → This document, complete, with a pointer to the evidence for all 35 items.

## Section 4.4.2 — Review

- [x] **We have documentation confirming that Program conformance was reviewed within the last 18 months.**
  → [Records §7](./OPENCHAIN-PROGRAMME-RECORDS.md#7-review-record) — reviewed 2026-08-24 against this checklist. Next scheduled 2027-08-24.

---

## Result

**35 of 35 met. Conformant.**

Five items were open when this checklist was first published on 2026-08-24 —
the four awareness acknowledgements and the confirmation item that depended on
them. All five closed the same day, when the second maintainer acknowledged the
programme documents. The version history of this file is public, so both the
gap and its closing are on the record.

---

## Declaration of conformance

**Basis Network declares conformance with ISO/IEC 18974:2023 (OpenChain
Security Assurance).**

- **Scope:** as stated in [§1.2 of the programme records](./OPENCHAIN-PROGRAMME-RECORDS.md#12-scope-statement)
- **Method:** self-certification against the OpenChain ISO/IEC 18974
  Self-Certification Checklist
- **Date:** 2026-08-24
- **Declared by:** Sebastian Tobar Quintero, Security Assurance Lead
- **Next review:** 2027-08-24

This is a self-certification. Basis Network is solely responsible for the
accuracy of the statements in this document.

**What conformance does not claim.** It does not say the software is free of
vulnerabilities, and it does not say every control exists: [§3.1 of the
programme](./OPENCHAIN-18974.md#31-identifying-vulnerabilities) records that we
do no fuzzing and that dependency scanning of the node workspace is not public.
The standard asks for a programme that identifies, tracks and remediates — not
for a perfect one — and a declaration that implied otherwise would be the kind
of claim this programme exists to avoid.
