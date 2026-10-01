# Contributing to OpenAustralia Foundation projects on GitLab

Thank you for helping build tools that give people the information and access
they need to take part in Australian democracy. This guide explains how we
work with Git and GitLab, so that contributions are consistent, easy to
follow, and clearly licensed.

It applies to every project in the [`openaustralia`](https://gitlab.com/openaustralia)
GitLab group. A project can add its own notes in a short local
`CONTRIBUTING.md` that points here, so check for one first.

Some OAF repositories stay on GitHub: the Planning Alerts scrapers that
[morph.io](https://morph.io) runs, and upstream projects we have forked. Their
guide is [`.github/CONTRIBUTING.md`](.github/CONTRIBUTING.md).

> **Status:** agreed by the team in July 2026. The four questions left open
> then were settled on 2026-09-30, and this guide reflects them. Suggestions
> are welcome through an issue or merge request.

## Our workflow

**The `main` branch is always production-ready.**

1. Create a branch off `main` for your work.
2. Open a merge request early, as a [draft](https://docs.gitlab.com/user/project/merge_requests/drafts/)
   while it is still in progress. Merge requests are how the team keeps up
   with what is changing, not just a gate to pass through.
3. Make sure the project's pipeline passes before you mark the merge request
   ready. The author is responsible for confirming it is green.
4. Once it has an approval and every thread is resolved, the merge request is
   merged. The author normally does the merging.
5. Deploy from `main`.

### Staging

Staging is project-specific. Where a project uses it, staging branches (for
example `staging` or `staging1`) are ephemeral: they are created for a
server or group of changes and reset as needed. Follow the conventions in the
project you are working in, and prefer aiming merge requests at `main`.

## Branches

Name branches using the [Conventional Branch](https://conventionalbranch.org/)
convention with full-word prefixes, followed by the issue number and a short
description:

- `feature/123-add-postcode-search`
- `bugfix/890-fix-pagination`
- `hotfix/123-correct-broken-link`
- `chore/21-update-dependencies`
- `doc/7391-clarify-setup-steps`

Assign merge requests you create to yourself, so it is clear who is driving
each change.

## Merge requests

- Fill in the merge request template: what you changed and why in two or
  three sentences or dot points, and a sentence or two on how you checked it.
  Delete a section that doesn't apply rather than filling it with "N/A".
- Keep the description to what a reviewer needs. The diff shows what changed,
  so use the description for what it can't show.
- If needed, concisely answer expected questions on what was left as is or
  deferred.
- Keep changes focused and reviewable.
- Link any related issue or merge request in a bullet point, so GitLab shows
  its title and status. Use `Closes #123` for an issue the change resolves.
- Tick every "Type of change" box that applies, not just one. For example, a
  hotfix is both "Bug fix" and "Already deployed". Remove those that don't
  apply.

## Reviews and approval

Every merge request needs one approval from someone other than its author.
Approvals reset when new commits are pushed, and every review thread must be
resolved before merging. Where a project has a `CODEOWNERS` file, a
[Code Owner](https://docs.gitlab.com/user/project/codeowners/) must approve
changes to the files they own.

A review is about understanding and improving the change together, not
gatekeeping.

## Commits: signatures and sign-off

**Sign** every commit you push to GitLab. GitLab's
[push rules](https://docs.gitlab.com/user/project/repository/push_rules/)
will reject unsigned pushes once the rule is switched on, so set it up now.
Sign each commit cryptographically, with an
[SSH](https://docs.gitlab.com/user/project/repository/signed_commits/ssh/),
[GPG](https://docs.gitlab.com/user/project/repository/signed_commits/gpg/) or
[X.509](https://docs.gitlab.com/user/project/repository/signed_commits/x509/)
key added to your GitLab account. The commit email must be one of your
[verified GitLab emails](https://docs.gitlab.com/user/profile/#change-your-commit-email)
for GitLab to show the signature as verified.

Commits that GitLab's interface or API creates are exempt from the signature
rule. The Web IDE cannot create commits once signatures are required, so make
edits in a local clone.

**Sign off** your commits too, if you can. We are moving towards requiring a
[Developer Certificate of Origin](https://developercertificate.org/) (DCO)
sign-off on every commit, but that requirement is paused for now. Add a
`Signed-off-by` line by committing with the `-s` flag:

```sh
git commit -s -m "Your commit message"
```

By signing off, you certify that you wrote the change or otherwise have the
right to submit it under the project's licence. OAF does not ask for a
Contributor Licence Agreement.

### Other contributors

As well as the sign-off by the primary author or authors at the bottom of the
commit, list any other contributors with
`Co-authored-by: Contributor Name <email@example.com>` immediately after any
sign-off lines.

### Automated contributions

[Renovate](https://docs.renovatebot.com/), OAF's dependency-update bot,
signs its own commits as `OAF Renovate`. A person still reviews and approves
each of its merge requests.

## AI-assisted contributions

We welcome contributions that use AI tools, provided you take responsibility
for what you submit. If you use an AI tool to generate a meaningful part of a
contribution:

- **Disclose it,** in two places: an `Assisted-by` trailer on each commit the
  tool helped produce, and a short note in the merge request description.
  Both name the tool and the specific model, in the same form:

  ```text
  Assisted-by: Claude Code:claude-opus-5
  ```

  The commit trailer belongs in the trailer block at the end of the message,
  alongside `Signed-off-by`. Report the model you actually used. Minor use,
  such as autocomplete or grammar checking, does not need disclosing.
- **Review it.** You are responsible for reviewing all AI-generated material
  before submitting, to the same standard as any other contribution. Be
  prepared to explain and support the change.
- **Cite sources where you can.** If an AI tool adapted code or an approach
  from an identifiable source, note the reference and its licence so
  reviewers can check for licence compatibility and any gotchas.

A sign-off must come from a human, not an AI agent, as it is a commitment
only a person can make.

AI agents open merge requests as the `oaf-agent` account, not as the person
driving them. That keeps the person who signed the commits free to approve
the merge request, because GitLab never lets an author approve their own.

### Review your own code before creating a merge request

First, run an AI code review (for example Claude Code's `/code-review`
skill, or an equivalent tool). Work through what it raises like any other
review feedback:

- fix it and recheck, or
- note it as a bullet point at the end of "What and why", either:
  - linking a follow-up issue if it is a problem best left for later, or
  - explaining briefly why a concern raised is not important.

This lets reviewers spend their time on understanding and judgement, not on
re-finding issues the author's own AI review should already catch. If a
reviewer judges this step was needed but skipped, they can return the merge
request for a combined AI and human review.

Then create the draft merge request, handle anything the pipeline raises in
the same way, and mark it ready.

---

_OpenAustralia Foundation - https://www.oaf.org.au_
