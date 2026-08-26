<!--
SPDX-FileCopyrightText: 2026 Basis Network
SPDX-License-Identifier: Apache-2.0
-->

# OpenChain Programme Records

**Applies to:** [ISO/IEC 5230 licence compliance](./OPENCHAIN-5230.md) and
[ISO/IEC 18974 security assurance](./OPENCHAIN-18974.md)
**Version:** 1.0 · 2026-08-24
**Next review:** 2027-08-24

The two programme documents describe what we do. This one holds the records
both standards require us to *keep*: who takes part, what they are expected to
know, what we distribute, what it is built from, how the programme is measured,
and when it was last reviewed.

It is one file for both programmes because the participants, the scope and the
review cycle are the same. Splitting it in two would mean maintaining two
copies of the same facts, and the second copy is the one that goes stale.

---

## 1. Scope

### 1.1 How the scope was determined

The scope is drawn around **what we distribute to third parties from public
repositories**, on the principle that licence obligations and security
assurance duties attach to distribution. We ask three questions of any
candidate artifact:

1. Do we hand it to someone else? If not, it is internal use, and out of scope.
2. Do we control its build and its licence metadata? If not, its records belong
   to whoever does, and we say where that is instead of claiming them.
3. Can conformance for it be demonstrated with evidence a reader can check?

Reviewed whenever a repository is published, retired, or changes what it ships.

### 1.2 Scope statement

**In scope — the Supplied Software:**

| Artifact | Repository |
|---|---|
| `download.sh`, the release verification script | [`basis-cli`](https://github.com/basis-network/basis-cli) |
| The published checksum files under `checksums/` | `basis-cli` |
| The release, signing and CI workflows | `basis-cli` |
| The test suite and the documentation set | `basis-cli` |
| Organisation health files and these programme documents | [`.github`](https://github.com/basis-network/.github) |

**Out of scope, and why:**

| Not covered | Reason |
|---|---|
| The `basis` binary served by our releases | Built from `basis-core`, which is not public. Its component records belong to that build, not to this programme. `download.sh` verifies the binary's integrity; it does not vouch for its provenance, and [`basis-cli`'s architecture document](https://github.com/basis-network/basis-cli/blob/main/docs/ARCHITECTURE.md) says so. |
| The Basis development network and its nodes | Operated, not distributed. |
| Internal infrastructure and deployment tooling | Not distributed. |

**Limits of the programme.** This is a narrowly-scoped programme, which is what
the OpenChain project recommends starting with. We would rather conform over a
boundary we can evidence than claim one we cannot. The boundary is stated here,
in the repositories themselves, and in our OpenSSF Best Practices entry, and
the three agree.

---

## 2. Programme participants and assessed competence

Competence is assessed by the programme lead against the requirements listed in
§1.2 of each programme document. Evidence is public work, not a certificate:
for a two-person project, the honest measure of whether someone knows how to do
this is whether the thing they built stands up when examined.

| Participant | Roles | Competence assessed | Evidence |
|---|---|---|---|
| Sebastian Tobar Quintero | Programme lead; licence compliance contact; security assurance lead; security contact | **Met** · 2026-08-24 | Authored both programme documents and the [assurance case](https://github.com/basis-network/basis-cli/blob/main/docs/ASSURANCE-CASE.md); brought `basis-cli` to REUSE compliance and to OpenSSF Best Practices **Silver**; specified and reviewed the checksum-and-signature release path, including the decision to keep checksums and binaries on separate channels. |
| David Alejandro Blandón Román | Second maintainer (access continuity) | **Not yet assessed** | Holds equal repository access so that a fix can be published while the lead is unavailable. Has not yet contributed changes or reviews, so there is no work to assess. Stated plainly rather than recorded as met. |
| External legal counsel | Legal expertise for open source licence matters | **Met** · retained | Legal counsel retained by the organisation and available to the programme lead for internal and external licence compliance questions, including claimed violations. Identified internally and reachable through the programme lead; not named here, because publishing the identity of a third party is not ours to do. |

**What this record admits.** One person holds every decision-making role, and
that person assessed their own competence. A larger organisation would separate
those. We are not one, and a record that pretended otherwise would fail the
first time anyone looked at the commit history.

### 2.1 Awareness record

Both standards require participants to be aware of the policy, the objectives,
what is expected of them, and what happens if the programme is not followed.
For a project this size that is not a training programme; it is a short list of
places where the rules are stated and enforced.

| What participants must be aware of | Where it is stated | How it reaches them |
|---|---|---|
| The open source policy, and where to find it | §1.1 of each programme document, public at this repository | Linked from the organisation profile and from every repository's `CONTRIBUTING.md` |
| Relevant open source objectives | The [scope statement](#12-scope-statement) above; each repository's `README.md` | Read before any change to what a repository ships |
| Contributions expected of them | `CONTRIBUTING.md`: DCO sign-off, SPDX headers, tests, review checklist | Enforced on every pull request by CI, not by reminder |
| The implications of not following the programme | A pull request that omits a licence header, a sign-off or a passing test **cannot be merged** | `reuse lint`, `shellcheck`, the test suite and branch protection are blocking |

| Participant | Policy communicated | Acknowledged |
|---|---|---|
| Sebastian Tobar Quintero | 2026-08-23, on publishing the programme | 2026-08-23 |
| David Alejandro Blandón Román | 2026-08-24, on being granted maintainer access | 2026-08-24 |

The enforcement column is the load-bearing one. Awareness that depends on
someone remembering a document is not a control; a check that blocks a merge
is. Where we rely on memory, we say so.

---

## 3. Component records

### 3.1 The record, and how it is kept

Every third-party component that takes part in producing or verifying the
Supplied Software is listed below with its licence and the obligations that
licence creates for us. The record is updated when a component is added,
removed, or moved to a new version, which for pinned GitHub Actions means every
Dependabot pull request.

**The Supplied Software has no third-party runtime dependencies.**
`download.sh` is POSIX shell and calls only tools already present on the host
(`curl`, `sha256sum` or `shasum`, `uname`, `mktemp`). There is no package
manager, no lockfile and no vendored code, so there is nothing to redistribute
and no attribution to carry. That is a property of the design, and the reason
this record is short.

### 3.2 Build and verification components

| Component | Version (pinned) | Licence | Distributed? | Obligation |
|---|---|---|---|---|
| [`actions/checkout`](https://github.com/actions/checkout) | `3d3c42e` | MIT | No | None. Used at build time only. |
| [`actions/upload-artifact`](https://github.com/actions/upload-artifact) | `043fb46` | MIT | No | None. Used at build time only. |
| [`fsfe/reuse-action`](https://github.com/fsfe/reuse-action) | `676e2d5` | **GPL-3.0-or-later** | No | **None, because we do not convey it.** See §3.3. |
| [`github/codeql-action`](https://github.com/github/codeql-action) | `db488dd` | MIT | No | None. Used at build time only. |
| [`ossf/scorecard-action`](https://github.com/ossf/scorecard-action) | `2d11466` | Apache-2.0 | No | None. Used at build time only. |
| [`sigstore/cosign-installer`](https://github.com/sigstore/cosign-installer) | `6f9f177` | Apache-2.0 | No | None. Used at build time only. |

Every one is pinned to a full commit SHA rather than a tag, so the component
recorded here is the component that runs. A tag can be moved; a SHA cannot.

### 3.3 The one that needs a reason, not a row

`fsfe/reuse-action` is **GPL-3.0-or-later**, and it is the only copyleft
component we touch. It creates no obligation for us, and the reason is the
distinction that §1.2 of the licence compliance programme says the programme
lead has to understand: **GPL obligations attach to conveying the software, not
to running it.** We run this action inside our own CI to check our own files.
Nothing of it is combined with, linked to or shipped in what we distribute, and
no recipient of our software receives any part of it.

We record it anyway, with its licence and its reasoning, because a component
record that only lists the permissive components is not a record — it is a
summary of the easy cases.

### 3.4 What we distribute, and its licensing

| Property | Value |
|---|---|
| Outbound licence | Apache-2.0 unless a file states otherwise |
| Per-file copyright and licence | SPDX headers, or `REUSE.toml` where the format has no comment syntax |
| Attribution notice | `NOTICE`, delivered with the repository |
| Licence texts | `LICENSE` and `LICENSES/` |
| Verification | `reuse lint`, blocking, on every push and pull request |

### 3.5 Known vulnerabilities and action taken

ISO/IEC 18974 requires the component record to track known vulnerabilities and
the action taken for each — **including where no action was required**, since
"we looked and it did not affect us" is a decision that has to be recorded or
it will be made again.

| Date | Component | Vulnerability | Assessment | Action |
|---|---|---|---|---|
| — | — | — | — | *None identified to date.* |

How an entry gets here:

- **Dependabot** raises a pull request when a pinned component moves. The pull
  request is the record: it carries the advisory, the version change and the
  decision, and it is preserved whether it is merged or closed.
- **A report** to `security@basisnetwork.com.co` or a GitHub security advisory
  is triaged under [§4 of the security assurance programme](./OPENCHAIN-18974.md#4-documented-response-process)
  and lands here with its outcome.
- **Scorecard and CodeQL** findings that concern a component rather than our
  own code are assessed and recorded the same way.

The table is empty because nothing has been identified, not because nothing is
being watched. The controls that would populate it are listed in
[§3.1 of the security assurance programme](./OPENCHAIN-18974.md#31-identifying-vulnerabilities),
along with the two that do not exist.

---

## 4. Programme metrics

ISO/IEC 18974 asks for metrics that measure programme performance. Ours are the
numbers the programme already produces, because a metric nobody generates is a
metric nobody reads.

| Metric | Source | Reading on 2026-08-24 |
|---|---|---|
| Files without licence or copyright information | `reuse lint` in CI | **0** — blocking, so any other value stops the build |
| Supply-chain posture | [OpenSSF Scorecard](https://scorecard.dev/viewer/?uri=github.com/basis-network/basis-cli) | **7.1 / 10** |
| Open source practice conformance | [OpenSSF Best Practices](https://www.bestpractices.dev/projects/14224) | **Silver** (gold 78 %) |
| Statement coverage of the distributed script | `make coverage`, blocking below 90 % | **98.1 %** |
| Static analysis findings in shipped shell | `shellcheck` in CI | **0** — blocking |
| Released assets whose checksum disagrees with git | Release workflow | **0** — a mismatch fails the release |
| Vulnerability reports received | Security advisories and `security@basisnetwork.com.co` | **0** to date |
| Median time to acknowledge a report | Same | *no data — no reports yet* |
| Dependencies behind their pinned version | Dependabot, weekly | tracked per pull request |

Two of these have no data, and both say so. The response-time metric becomes
meaningful the first time someone reports something; until then, publishing a
median of nothing would be worse than an empty cell.

---

## 5. Compliance artifact archive

| Artifact | Where it is archived | For how long |
|---|---|---|
| Licence texts and per-file licence metadata | Git history of each repository | Life of the repository |
| `NOTICE`, attribution as delivered | Git history | Life of the repository |
| Checksums for every published release | `checksums/<tag>/`, committed **before** the release is published | Life of the repository |
| Signatures and certificates | The public [Rekor](https://docs.sigstore.dev/logs/overview/) transparency log | Held by the log, not by us |
| The exact source of any release | Git tag | Life of the repository |
| CI evidence: lint, tests, coverage, licence check | GitHub Actions run history | GitHub's retention, currently 90 days |

**Retention is the life of the repository**, which is longer than the last
offer of the Supplied Software and therefore satisfies both the standard and
the licences we ship under. This works because our compliance artifacts are
text in version control rather than files on a build server: archiving is a
consequence of how we store them, not a task someone has to remember.

The one exception is CI run history, which GitHub expires after 90 days. The
evidence that matters — what was shipped, its checksum, and the commit it came
from — is in git, and git does not expire it.

---

## 6. Handling a non-conformance

Applies to a licence obligation we missed, a component that should not have
shipped, or any report that the programme was not followed.

1. **Acknowledge** within 10 working days, to whoever raised it.
2. **Establish the facts**: what shipped, under what licence, from which commit,
   and to whom.
3. **Contain**: if something is being distributed that should not be, the
   distribution stops before anything else happens.
4. **Remediate**: correct the metadata, add the missing notice, replace or
   remove the component.
5. **Re-release** where recipients received a non-conforming artifact, and say
   in the `CHANGELOG` what was wrong.
6. **Fix the cause**: if the failure could recur, it becomes a blocking check,
   not a note to be careful. Every automated check we run was added this way or
   to prevent a class of failure we could foresee.
7. **Record it** in §7 below.

**Non-conformances to date: none recorded.**

---

## 7. Review record

Both standards require conformance to be reviewed at least every 18 months.
Ours is reviewed annually, and on the triggers listed in each programme
document.

| Date | Reviewer | Scope of review | Outcome |
|---|---|---|---|
| 2026-08-24 | Sebastian Tobar Quintero | Full review of both programmes against the OpenChain self-certification checklists for ISO/IEC 5230:2020 and ISO/IEC 18974:2023 | **Conformant** — 34 of 34 items met for [ISO/IEC 5230](./OPENCHAIN-5230-CHECKLIST.md) and 35 of 35 for [ISO/IEC 18974](./OPENCHAIN-18974-CHECKLIST.md). The review found the programme documents described the practice accurately but did not hold several records the standards require: assessed competence, the awareness record, a written scope statement, component records, metrics, the artifact archive, non-conformance handling, and a review record. This document was created to hold them. The completed checklists were published at the same time, initially with six and five items open. Those closed on the same day: the second maintainer acknowledged the programme documents, and legal counsel was identified. Conformance was declared for both standards on 2026-08-24. |
| 2026-08-23 | Sebastian Tobar Quintero | Initial authoring of both programme documents | Programmes published |

**Next scheduled review: 2027-08-24.**
