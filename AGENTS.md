# AGENTS.md

This file provides guidance to AI coding agents (Claude Code, GitHub Copilot,
and others) when working with code in this repository.

## What this repository is

`openaustralia/.github` is a [GitHub special repository](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file):
files under `.github/` here are inherited by every repository in the
`openaustralia` org that doesn't provide its own copy. `profile/README.md` is
unrelated to that mechanism. It's the org's [profile README](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/personalizing-your-profile#adding-a-public-profile-readme-for-your-organization),
shown at github.com/openaustralia. Don't confuse it with the root `README.md`,
which documents this repository itself.

There is no build, lint, or test step. The repository is markdown, one
`CODEOWNERS` file, one `FUNDING.yml`, and the two issue forms under
`.github/ISSUE_TEMPLATE/`. Changes are reviewed by opening a PR against `main`
per `.github/CONTRIBUTING.md`.

The issue forms are the one part with a schema worth checking before you push.
Validate them against the [GitHub issue-forms schema](https://www.schemastore.org/github-issue-forms.json)
rather than guessing at the syntax. Nothing in this repository runs that check
for you, and the forms only render on the default branch, so the first real
confirmation is opening a new issue after merge.

## Files that reference each other

Several files cross-reference one another by content, not by any tooling.
Keep them consistent by hand when editing:

- OAF's five public services are listed in **four** places: the "Our services"
  table in `profile/README.md`, the "Support our work" paragraph in that same
  file, and the "Which service is this about?" dropdown in each of
  `.github/ISSUE_TEMPLATE/bug_report.yml` and
  `.github/ISSUE_TEMPLATE/feature_request.yml`. Adding, renaming, or retiring a
  service means editing all four. Nothing checks this for you.
- `.github/CODEOWNERS` names a team (`@openaustralia/staff`) that must
  actually have write access to repos inheriting this file. A team with no
  access is silently ignored by GitHub rather than erroring (see commit
  `b09ffcd`, which fixed exactly this).
- The `type:` key in each issue form (`Bug`, `Feature`) names an issue type
  that must be enabled on the `openaustralia` org. Check the org's issue types
  before changing either value, and confirm the result on a real issue.

## Conventions specific to this org

- Non-partisan: nothing in these files should imply endorsement or criticism
  of any party, candidate, or position.
- Australian English throughout.
- No em dashes. Use a hyphen, a comma, or a full stop.
- Disclose AI involvement in both places `.github/CONTRIBUTING.md` asks for:
  an `Assisted-by: <agent-name>:<model-id>` trailer on each commit, and a note
  in the pull request description. Report the model actually used, not a
  remembered default.
- When leaving a PR review comment, give the actual replacement code instead
  of describing the change, but only when a) there are no remaining decisions
  to make, b) it replaces just one section of code, and c) it is not
  significantly longer than describing the change would be. The comment then
  reduces to the code plus a short line on the reason for the change. If any
  condition fails, describe the change in prose as usual.
- Cite sources where you can. If you adapt code or an approach from an
  identifiable source, note the reference and its licence in the commit or PR
  description so reviewers can check for licence compatibility and gotchas.
- `.github/CONTRIBUTING.md` is still marked as evolving (see the "Open
  questions" section at the end of it), so don't present unsettled points as
  decided. Whether OAF reinstates a contributor licence agreement is one of
  those open questions.
