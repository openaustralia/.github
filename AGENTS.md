# AGENTS.md

This file provides guidance to AI coding agents (Claude Code, GitHub Copilot,
and others) when working with code in this repository. `CLAUDE.md` and
`.github/copilot-instructions.md` point here so the guidance lives in one
place. The final section, "Working as an agent in any OAF repository", is
org-wide guidance that other repositories' `AGENTS.md` files reference.

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

## Working as an agent in any OAF repository

This section is org-wide guidance, not specific to this repository. Other
repositories' `AGENTS.md` files should reference it rather than copy it,
because copies drift. Fetch the current version with:

`curl -fsSL https://raw.githubusercontent.com/openaustralia/.github/main/AGENTS.md`

Any equivalent fetch works: a web fetch of that URL, `gh api` if the
GitHub CLI is installed, or a local clone of this repository beside the
one being worked on. Don't assume any particular tool is present.

- Fetch before you plan, and again before rewriting a file wholesale. A local
  clone can be many commits behind `origin/main`, and a change designed
  against a stale file quietly reverts whatever landed in between. Compare
  against the remote rather than the working copy: `git fetch` then
  `git log --oneline main..origin/main`, or read the file from the remote if
  the clone can't be fetched.
- Keep the future effect of any standing approval ("yes to all following",
  "don't ask again") clearly scoped. Read-only tool calls (Read, grep,
  `git status`/`diff`/`log`) can be batched freely, and a standing approval
  for them is safe to extend broadly. File changes (Edit/Write, or Bash like
  `mv`/`rm`/`sed -i`) are different: state what's about to change and why
  before making it, one described step or clearly-announced group at a time,
  so an approval covers something the human has actually seen reasoned about.
  `git add` isn't covered by this, it's cheap to undo.
- The same scoping applies to Bash allow-patterns for multi-subcommand CLIs
  (`gh`, `git`, `aws`, `terraform`): a prefix like `gh pr` covers both
  read-only `gh pr view` and mutating `gh pr create`/`merge`/`close`. Prefer
  the pattern scoped to the exact safe subcommand used, not the shared
  prefix, and don't save a broader pattern to a settings file either.
- Stage commits rather than making them, unless the human has explicitly
  asked you to commit: `git add` the files, then write the proposed message
  (with the `Assisted-by:` trailer) to `.git/GITGUI_MSG` and display it.
  Check that file first; if it already has content, ask before overwriting.
  The DCO sign-off in `.github/CONTRIBUTING.md` is a certification only a
  person can make, so the commit is normally the human's deliberate act.
  Never add `Signed-off-by` or `Co-authored-by` on an AI agent's behalf, and
  never strip a human's.
- Don't hard-wrap prose in pull request descriptions, issue bodies, issue
  comments, or review comments, in any OAF repository. GitHub renders each
  newline in those fields as a line break, so text wrapped at a column width
  comes out ragged. Write one paragraph per line, however long that line
  gets, and check the rendered result after posting. This applies to bodies
  passed via `--body`, `--body-file`, or a heredoc just as much as to text
  typed into the web UI. Hard-wrapping markdown files committed to a
  repository is a different matter and stays fine.
- PRs an agent creates are opened as drafts and assigned to the human driving
  the change, not to the agent. Taking a PR out of draft is the human's call.
- GitHub issues have no draft state. Don't create one directly, draft the
  title and body for the human to file themselves, unless they've explicitly
  asked you to create it this time.
- Never commit real personal details, credentials, or secrets; use fictional
  placeholders in examples, specs, and seed data (the Australian Privacy
  Principles apply here as much as anywhere). Never read a file that
  plausibly holds live credentials into an AI conversation, even to check
  its structure; if you need one fact from it, `grep` for that specific line
  rather than printing the whole file.
- If a repository's `AGENTS.md` doesn't match what you consistently see in
  its code, flag the mismatch and ask which needs fixing rather than
  silently trusting either.
- Make each commit a single, logical change. Don't bundle a feature
  addition, a typo fix, and a dependency update into one commit just because
  they came from the same session or review pass.
