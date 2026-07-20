# Contributing to OpenAustralia Foundation projects

Thank you for helping build tools that give people the information and access
they need to take part in Australian democracy. This guide explains how we
work with Git and GitHub across our repositories so that contributions are
consistent, easy to follow, and clearly licensed.

This file lives in the [`openaustralia/.github`](https://github.com/openaustralia/.github)
repository and applies to every OpenAustralia Foundation repository unless a
repository provides its own `CONTRIBUTING.md` that overrides it. Some projects
have their own workflow for good reasons (for example, Right to Know), so
always check for a repository-specific file first.

> **Status:** This is our shared starting point, agreed by the team in July
> 2026. A few details are still being finalised and are marked as open
> questions at the end. Suggestions are welcome via an issue or pull request.

## Our workflow: GitHub Flow

We use [GitHub Flow](https://docs.github.com/en/get-started/using-github/github-flow).
The key principle is simple:

**The `main` branch is always production-ready.**

In practice that means:

1. Create a branch off `main` for your work.
2. Open a pull request early. Pull requests are how the team keeps up with what
   is changing. They are for visibility and shared understanding, not just a
   gate to pass through.
3. Open your pull request as a **draft** while it is still in progress.
4. Make sure **all** the checks in `.github/workflows` pass before you take the
   pull request out of draft. The author is responsible for confirming the
   tests are green.
5. Once reviewed and passing, the pull request is merged. The author normally
   does the merging.
6. Deploy from `main`.

### Staging

GitHub Flow does not prescribe how staging works, and our practice varies by
project. Where staging is used, staging branches (for example `staging` or
`staging1`) are treated as ephemeral: they are created for a specific server or
group of changes and reset as needed. Follow the conventions in the repository
you are working in, and prefer aiming pull requests at `main`.

## Branches

Name branches using the [Conventional Branch](https://conventionalbranch.org/#summary)
convention, with a type prefix followed by the issue number and a short description, for example:

- `feature/123-add-postcode-search`
- `bugfix/890-fix-pagination`
- `hotfix/123-correct-broken-link`
- `chore/21-update-dependencies`
- `doc/7391-clarify-setup-steps`

Assign pull requests you create to yourself so it is clear who is driving each
change.

## Pull requests

- Fill in the pull request template. Describe what you changed, why, and how you
  tested it.
- Keep changes focused and reviewable.
- Link to any related issue.
- Take the pull request out of draft only once the checks pass.

## Commits and sign-off

We are moving towards requiring a sign-off on every commit so that we have a
clear, documented record that each contribution can be lawfully included in our
projects. This matters more than ever now that AI tools are commonly involved
in writing code.

**Sign off your commits** using the
[Developer Certificate of Origin](https://developercertificate.org/) (DCO). Add
a `Signed-off-by` line by committing with the `-s` flag:

```sh
git commit -s -m "Your commit message"
```

By signing off, you certify that you wrote the change or otherwise have the
right to submit it under our licence.

## Contributor Licence Agreement

Before your first contribution is merged, we ask you to agree to our
[Contributor Licence Agreement](https://github.com/openaustralia/.github/blob/main/CLA/CLA.md)
(CLA). You do this by commenting on your pull request with:

> **I have read the CLA Document and I hereby sign the CLA**

The CLA confirms you have the right to contribute your work and that you are
licensing it to us so we can keep distributing our software under an open
licence. This reflects our charitable object of providing content and software
under an open licence wherever practicable.

## AI-assisted contributions

We welcome contributions that use AI tools, provided you take responsibility
for what you submit. If you use an AI tool to generate a meaningful part of a
contribution:

- **Disclose it.** Add a short note in your pull request description, for
  example: _"Parts of this contribution were generated or assisted by
  [tool name]."_ Minor use, such as autocomplete or grammar checking, does not
  need disclosing.
- **Review it.** You are responsible for reviewing all AI-generated material
  before submitting, to the same standard as any other contribution. Be
  prepared to explain and support the change.
- **Cite sources where you can.** If an AI tool adapted code or an approach
  from an identifiable source, note the reference and its licence so reviewers
  can check for licence compatibility and any gotchas.

A human, not an AI agent, must sign off the commit and agree to the CLA, as
these are commitments only a person can make.

See the [CLA](https://github.com/openaustralia/.github/blob/main/CLA/CLA.md)
for the full terms covering AI-assisted contributions.

## Reviews

Reviews help us share knowledge and keep `main` healthy. Repositories use a
`CODEOWNERS` file to request reviews from the right people. A review is about
understanding and improving the change together, not gatekeeping.

## Open questions

These points were raised but not yet settled. We will update this guide once
the team decides:

- **Branch prefix wording:** whether to standardise on full words
  (`feature/`, `bugfix/`) or short forms (`feat/`). This guide currently uses
  the full-word forms from Conventional Branch.
- **Cryptographic signing:** whether to require GPG-signed commits in addition
  to the DCO sign-off.
- **Staging conventions:** whether to define a single org-wide approach to
  staging environments and branches.

---

_OpenAustralia Foundation - https://www.oaf.org.au_
