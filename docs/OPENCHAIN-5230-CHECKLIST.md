<!--
SPDX-FileCopyrightText: 2026 Basis Network
SPDX-License-Identifier: Apache-2.0
-->

# OpenChain ISO/IEC 5230 Self-Certification Checklist — Basis Network

**Standard:** ISO/IEC 5230:2020 (OpenChain Licence Compliance)
**Checklist:** Generation 2, Version 1 (2025-08-18)
**Organisation:** Basis Network
**Completed:** 2026-08-24 by Sebastian Tobar Quintero, programme lead
**Scope:** as stated in [§1.2 of the programme records](./OPENCHAIN-PROGRAMME-RECORDS.md#12-scope-statement)

This is the OpenChain self-certification checklist, answered. Each item carries
a pointer to the evidence rather than a bare tick, so that a reader can check
the answer instead of trusting it.

This is a **self-certification**. Basis Network is solely responsible for the
accuracy of the statements below.

---

## Section 1: Programme foundation

- [x] **We have a documented policy governing the open source license compliance of supplied software.**
  → [Programme §1.1](./OPENCHAIN-5230.md#11-policy) — four rules, public at a stable URL.

- [x] **We have a documented procedure to communicate the existence of the open source policy to program participants.**
  → [Records §2.1](./OPENCHAIN-PROGRAMME-RECORDS.md#21-awareness-record) — where each rule is stated and how it reaches participants. Linked from the organisation profile and from every repository's `CONTRIBUTING.md`.

- [x] **We have identified the roles and responsibilities that affect the performance and effectiveness of the program.**
  → [Programme §2](./OPENCHAIN-5230.md#2-relevant-tasks-defined-and-supported) — role table. It records that both programme roles are held by one person.

- [x] **We have identified and documented the competencies required for each role.**
  → [Programme §1.2](./OPENCHAIN-5230.md#12-competence) — four required areas, including the distinction between distribution and internal use.

- [x] **We have documented the assessed competence for each program participant.**
  → [Records §2](./OPENCHAIN-PROGRAMME-RECORDS.md#2-programme-participants-and-assessed-competence) — assessment and evidence per participant. The second maintainer is recorded as *not yet assessed*, with the reason.

- [x] **We have documented the awareness of our program participants on the open source policy and where to find it.**
  → [Records §2.1](./OPENCHAIN-PROGRAMME-RECORDS.md#21-awareness-record) — the policy is public, communicated to both participants on the dates recorded, and acknowledged by both.

- [x] **We have documented the awareness of our program participants on relevant open source objectives.**
  → Same record. The objectives are the scope statement and what each repository ships.

- [x] **We have documented the awareness of our program participants on contributions expected to ensure the effectiveness of the program.**
  → Same record. What is expected is stated in `CONTRIBUTING.md` — DCO sign-off, SPDX headers, tests — and enforced on every pull request by CI rather than by reminder.

- [x] **We have documented the awareness of our program participants on the implications of failing to follow the Program requirements.**
  → Same record. The implication is mechanical rather than disciplinary: a pull request that omits a licence header, a sign-off or a passing test cannot be merged.

- [x] **We have a process for determining the scope of our program.**
  → [Records §1.1](./OPENCHAIN-PROGRAMME-RECORDS.md#11-how-the-scope-was-determined) — three questions applied to each candidate artifact, re-run whenever a repository is published or retired.

- [x] **We have a written statement clearly defining the scope and limits of the program.**
  → [Records §1.2](./OPENCHAIN-PROGRAMME-RECORDS.md#12-scope-statement) — what is in, what is out, and why. The `basis` binary is explicitly out of scope.

- [x] **We have a documented procedure to review and document open source license obligations, restrictions and rights.**
  → [Programme §3.2](./OPENCHAIN-5230.md#32-inbound-components) — three steps before a component ships. Outcomes recorded in [Records §3](./OPENCHAIN-PROGRAMME-RECORDS.md#3-component-records).

## Section 2: Relevant tasks defined and supported

- [x] **We have a publicly visible method for any third party to make an open source license compliance inquiry.**
  → `contact@basisnetwork.com.co`, published in [Programme §2](./OPENCHAIN-5230.md#2-relevant-tasks-defined-and-supported), in the closing section of the programme, and in each repository's `SUPPORT.md`.

- [x] **We have a documented procedure for responding to open source compliance inquiries.**
  → [Programme, "Reporting a compliance concern"](./OPENCHAIN-5230.md#reporting-a-compliance-concern) — acknowledgement within 10 working days; handling in [Records §6](./OPENCHAIN-PROGRAMME-RECORDS.md#6-handling-a-non-conformance).

- [x] **We have documented the persons, group or function supporting the program role(s) identified.**
  → [Programme §2](./OPENCHAIN-5230.md#2-relevant-tasks-defined-and-supported) and [Records §2](./OPENCHAIN-PROGRAMME-RECORDS.md#2-programme-participants-and-assessed-competence) — named, not described as a function.

- [x] **We have ensured the identified program roles been properly staffed and adequately funded.**
  → [Programme §2, "Resources"](./OPENCHAIN-5230.md#2-relevant-tasks-defined-and-supported) — the controls run on the organisation's GitHub Actions allowance and require no purchase; review time is allocated as part of release work and is enforced mechanically.

- [x] **We have identified legal expertise to address internal and external open source compliance matters.**
  → [Records §2](./OPENCHAIN-PROGRAMME-RECORDS.md#2-programme-participants-and-assessed-competence) — legal counsel retained by the organisation, available to the programme lead for internal and external licence questions including claimed violations. Identified internally and reachable through the programme lead; not named in a public document, because publishing the identity of a third party is not ours to do.

- [x] **We have a documented procedure assigning internal responsibilities for open source compliance.**
  → [Programme §2](./OPENCHAIN-5230.md#2-relevant-tasks-defined-and-supported) — role table assigning policy, inbound licence decisions and external contact.

- [x] **We have a documented procedure for handling the review and remediation of non-compliant cases.**
  → [Records §6](./OPENCHAIN-PROGRAMME-RECORDS.md#6-handling-a-non-conformance) — seven steps from acknowledgement to making the cause a blocking check. None recorded to date.

## Section 3: Open source content review and approval

- [x] **We have a documented procedure for identifying, tracking, reviewing, approving, and archiving information about the open source components in a supplied software release.**
  → [Programme §3.2](./OPENCHAIN-5230.md#32-inbound-components) for the procedure; [Records §3.1](./OPENCHAIN-PROGRAMME-RECORDS.md#31-the-record-and-how-it-is-kept) for how the record is kept and when it is updated; [Records §5](./OPENCHAIN-PROGRAMME-RECORDS.md#5-compliance-artifact-archive) for archiving.

- [x] **We have open source component records for the supplied software to demonstrate the documented procedure was properly followed.**
  → [Records §3.2](./OPENCHAIN-PROGRAMME-RECORDS.md#32-build-and-verification-components) — every component, its pinned SHA, its licence and its obligation. The Supplied Software has no third-party runtime dependencies, and §3.1 says why.

- [x] **We have a documented procedure that covers distribution of the supplied software in binary form.**
  → [Programme §3.1](./OPENCHAIN-5230.md#31-what-we-distribute) and [§4](./OPENCHAIN-5230.md#4-compliance-artifact-creation-and-delivery) — provenance stated per artifact, checksums committed to git before release, assets verified against them or the release fails.

- [x] **We have a documented procedure that covers distribution of the supplied software in source form.**
  → [Programme §3.3](./OPENCHAIN-5230.md#33-outbound-licence) and [§4](./OPENCHAIN-5230.md#4-compliance-artifact-creation-and-delivery) — Apache-2.0, per-file SPDX headers, `LICENSE`, `LICENSES/` and `NOTICE` travelling with the repository, verified by blocking `reuse lint`.

- [x] **We have a documented procedure that covers integration of the supplied software with open source that may trigger additional obligations.**
  → [Programme §3.2](./OPENCHAIN-5230.md#32-inbound-components), step 2 — obligations checked against the intended distribution before integration. The worked case is in [Records §3.3](./OPENCHAIN-PROGRAMME-RECORDS.md#33-the-one-that-needs-a-reason-not-a-row).

- [x] **We have a documented procedure that covers inclusion of modified open source in the supplied software.**
  → [Programme §5](./OPENCHAIN-5230.md#5-understanding-open-source-community-engagement) — modifications kept as patches against pinned upstream commits, under the upstream licence, so the boundary between their work and ours stays legible.

- [x] **We have a documented procedure that covers inclusion of open source or other software under incompatible licenses interacting with other components in the supplied software.**
  → [Programme §3.2](./OPENCHAIN-5230.md#32-inbound-components), step 3 — incompatible or unidentifiable licences are rejected, and §1.1 rule 4 makes that a policy rather than a preference.

- [x] **We have a documented procedure that covers inclusion of open source with attribution requirements in the supplied software.**
  → [Programme §4](./OPENCHAIN-5230.md#4-compliance-artifact-creation-and-delivery) — `NOTICE` ships with the artifact; policy rule 3 requires notices to travel with what we ship rather than live on a website.

## Section 4: Compliance artifact creation and delivery

- [x] **We have a documented procedure describing the process for preparing and distributing compliance artifacts with the supplied software as required by the identified licenses.**
  → [Programme §4](./OPENCHAIN-5230.md#4-compliance-artifact-creation-and-delivery) — artifact table plus the two blocking automated checks.

- [x] **We have a documented procedure for archiving copies of compliance artifacts for the supplied software from either the last offer of the supplied software or as required by the identified licenses, whichever is longer.**
  → [Records §5](./OPENCHAIN-PROGRAMME-RECORDS.md#5-compliance-artifact-archive) — retention is the life of the repository, because the artifacts are text in version control rather than files on a build server.

## Section 5: Understanding open source community engagements

- [x] **We have a documented open source contribution policy.**
  → [Programme §5](./OPENCHAIN-5230.md#5-understanding-open-source-community-engagement) — contribute upstream under the upstream licence and process, with the programme lead's knowledge.

- [x] **We have a documented procedure governing open source contributions.**
  → [Programme §3.4](./OPENCHAIN-5230.md#34-contributions-in) for inbound (DCO, no CLA, contributors keep copyright) and §5 for outbound. Sign-off is enforced on every pull request.

- [x] **We have a documented procedure for making all program participants aware of the open source contribution policy.**
  → [Records §2.1](./OPENCHAIN-PROGRAMME-RECORDS.md#21-awareness-record) — stated in `CONTRIBUTING.md` in every repository and enforced by CI rather than by reminder.

## Section 6: Adherence to the specification requirements

- [x] **We have documentation confirming that the program meets all the requirements of the specification.**
  → This document, complete, with a pointer to the evidence for all 34 items.

- [x] **We have documentation confirming that the program conformance is reviewed at least every 18 months.**
  → [Records §7](./OPENCHAIN-PROGRAMME-RECORDS.md#7-review-record) — review record with dates, reviewer, scope and outcome. Reviewed annually; next scheduled 2027-08-24.

---

## Result

**34 of 34 met. Conformant.**

Six items were open when this checklist was first published on 2026-08-24, and
they are listed here rather than quietly overwritten: the four awareness
acknowledgements, identified legal expertise, and the confirmation item that
depended on them. All six closed the same day — the second maintainer
acknowledged the programme documents, and legal counsel was identified.

The version history of this file is public, so the gaps and their closing are
both on the record. We would rather show a checklist that was briefly
incomplete than one that was never anything else.

---

## Declaration of conformance

**Basis Network declares conformance with ISO/IEC 5230:2020 (OpenChain Licence
Compliance).**

- **Scope:** as stated in [§1.2 of the programme records](./OPENCHAIN-PROGRAMME-RECORDS.md#12-scope-statement)
- **Method:** self-certification against the OpenChain ISO/IEC 5230
  Self-Certification Checklist, Generation 2, Version 1
- **Date:** 2026-08-24
- **Declared by:** Sebastian Tobar Quintero, Open Source Programme Lead
- **Next review:** 2027-08-24

This is a self-certification. Basis Network is solely responsible for the
accuracy of the statements in this document. Every item above points at
evidence a reader can check without asking us.
