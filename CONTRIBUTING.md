<!--
SPDX-FileCopyrightText: 2026 Basis Network
SPDX-License-Identifier: Apache-2.0
-->

# Contributing to Basis Network projects

Default guidance for the `basis-network` organisation. A repository with its
own `CONTRIBUTING.md` overrides this one — read that first, because what each
repository accepts differs.

## Before you write code

Several of our public repositories **distribute and document** software whose
source is not public yet. In those, bug reports and documentation fixes are
welcome and patches to the tool itself are not possible. The repository's own
`CONTRIBUTING.md` says which kind it is. Checking first saves you the work.

## Sign your work — the DCO

Every commit needs a [Developer Certificate of Origin](https://developercertificate.org/)
sign-off. It is not a copyright assignment: you keep your copyright, and you
state that you have the right to contribute what you are contributing.

```bash
git commit -s -m "fix: whatever it is"
```

Use your real name and an address that reaches you. Commits without a sign-off
cannot be merged.

## Licence

Contributions are licensed under **Apache-2.0** unless the repository states
otherwise. Chosen for its express patent grant, which matters when the subject
is a post-quantum cryptographic implementation.

## Every file states its licence

Our repositories are [REUSE](https://reuse.software/) 3.3 compliant. A new file
needs an SPDX header:

```
SPDX-FileCopyrightText: 2026 Your Name
SPDX-License-Identifier: Apache-2.0
```

or an entry in `REUSE.toml` if it has no comment syntax. CI fails otherwise;
`reuse lint` tells you which files are missing what.

## How we write

- **Comments explain why, not what.** If a line needs a comment saying what it
  does, the line is the problem.
- **Known problems get written down.** A documented limitation costs a reader
  a minute; an undocumented one costs them an afternoon.
- **Commit messages say what was broken.** Not "update script" — what did not
  work before, and what works now.

## Code of Conduct

By participating you agree to the [Code of Conduct](./CODE_OF_CONDUCT.md).

## Reporting a vulnerability

Not here. See [SECURITY.md](./SECURITY.md).
