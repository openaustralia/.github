# Contributing to OpenAustralia Foundation projects on GitHub

Thank you for helping build tools that give people the information and access
they need to take part in Australian democracy. This guide explains how we
work with Git and GitHub, so that contributions are consistent, easy to
follow, and clearly licensed.

It applies to the OAF repositories that stay on GitHub: the Planning Alerts
scrapers in [`planningalerts-scrapers`](https://github.com/planningalerts-scrapers),
which [morph.io](https://morph.io) runs from GitHub, other repositories
morph.io runs, and upstream projects we have forked. A repository can override
it with its own `CONTRIBUTING.md`, so always check for one first.

**Most OAF projects are moving to GitLab.** Once a project has moved, its
GitHub repository is a read-only copy, and its issues and merge requests live
on GitLab instead. Contribute there, following the
[GitLab guide](https://gitlab.com/openaustralia/templates/-/blob/main/CONTRIBUTING.md).

> **Status:** agreed by the team in July 2026. The four questions left open
> then were settled on 2026-09-30, and this guide reflects them. This file is
> maintained in [`openaustralia/templates`](https://gitlab.com/openaustralia/templates)
> on GitLab and copied here. Suggestions are welcome as an issue or merge
> request there.

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

Staging is project-specific. Where it is used, staging branches (for example `staging` or
`staging1`) are treated as ephemeral: they are created for a specific server or
group of changes and reset as needed. Follow the conventions in the repository
you are working in, and prefer aiming pull requests at `main`.

## Branches

Name branches using the [Conventional Branch](https://conventionalbranch.org/#summary)
convention with full-word prefixes, followed by the issue number and a short
description, for example:

- `feature/123-add-postcode-search`
- `bugfix/890-fix-pagination`
- `hotfix/123-correct-broken-link`
- `chore/21-update-dependencies`
- `doc/7391-clarify-setup-steps`

Assign pull requests you create to yourself so it is clear who is driving each
change.

## Pull requests

- Fill in the pull request template: what you changed and why in two or three
  sentences or dot points, and a sentence or two on how you tested it. Delete
  a section that doesn't apply rather than filling it with "N/A".
- Keep the description to what a reviewer needs. The diff shows what changed,
  so use the description for what it can't show.
- If needed, concisely answer expected questions on what was left as is or deferred
- Keep changes focused and reviewable.
- Link to any related issue or pull request, preferably in a bullet point.
  Otherwise repeat the link in a bullet point after the paragraph
  so GitHub shows the title and status.
- Tick every "Type of change" box that applies, not just one, for example a
  hotfix is both "Bug fix" and "Already deployed". Remove those that don't apply.
- Take the pull request out of draft only once the checks pass.

## Commits and sign-off

We are moving towards requiring a sign-off trailer on every commit so that we have a
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
right to submit it under our licence. OAF does not ask for a Contributor
Licence Agreement.

Cryptographic signing is not required for repositories on GitHub. Projects on
GitLab require a verified signature.

## Other contributors

As well as the sign off by the primary author/s at the bottom of the commit,
list any other contributors using "Co-authored-by: Contributor Name
<email@example.com>" immediately following the sign off line/s.

## AI-assisted contributions

We welcome contributions that use AI tools, provided you take responsibility
for what you submit. If you use an AI tool to generate a meaningful part of a
contribution:

- **Disclose it,** in two places: an `Assisted-by` trailer on each commit the
  tool helped produce, and a short note in the pull request description. Both
  name the tool and the specific model, in the same form:

  ```
  Assisted-by: Claude Code:claude-opus-5
  ```

  The commit trailer belongs in the trailer block at the end of the message,
  alongside `Signed-off-by`. Report the model you actually used. Minor use,
  such as autocomplete or grammar checking, does not need disclosing.
- **Review it.** You are responsible for reviewing all AI-generated material
  before submitting, to the same standard as any other contribution. Be
  prepared to explain and support the change.
- **Cite sources where you can.** If an AI tool adapted code or an approach
  from an identifiable source, note the reference and its licence so reviewers
  can check for licence compatibility and any gotchas.

A human, not an AI agent, must sign off the commit, as this is a commitment
only a person can make.

### Review your own code before creating a PR

First, run an AI code review (for example Claude Code's `/code-review`
skill, or an equivalent tool). Work through what it raises like any other
review feedback:

- fix it and recheck,
- Otherwise, note it as a bullet point at the end of "What and why", either:
  - link a follow-up issue if it is a problem best left for later, or
  - explain briefly why a concern raised is not important.

This lets humans reviewing PRs spend their time on understanding and judgement,
not on re-finding issues the author's own AI review should already catch, or
on gatekeeping. If a reviewer judges this step is needed but was skipped,
they can return the pull request for a combined AI and human review.

Then create the draft pull request, handle any concerns GitHub Actions
raises in the same way, and finally click the `Ready for review` button.
Leave it to the human reviewer to read your responses to GitHub Actions and
mark its concerns as resolved.

## Reviews

Reviews help us share knowledge and keep `main` healthy. Repositories use a
`CODEOWNERS` file to request reviews from the right people. A review is about
understanding and improving the change together, not gatekeeping.

---

_OpenAustralia Foundation - https://www.oaf.org.au_
