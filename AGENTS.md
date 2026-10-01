# AGENTS.md

This file provides guidance to AI coding agents (Claude Code, GitHub Copilot,
and others). `CLAUDE.md` and `.github/copilot-instructions.md` point here so
the guidance lives in one place.

The first section, "Working as an agent in any OAF repository", is org-wide.
Other repositories' `AGENTS.md` files should reference it rather than copy it,
because copies drift. Fetch the current version immediately with:

`curl -fsSL https://gitlab.com/openaustralia/templates/-/raw/main/AGENTS.md`

This file lives in [`openaustralia/templates`](https://gitlab.com/openaustralia/templates)
on GitLab and is copied to [`openaustralia/.github`](https://github.com/openaustralia/.github)
on GitHub, so `https://raw.githubusercontent.com/openaustralia/.github/main/AGENTS.md`
serves the same text. Any equivalent fetch works: a web fetch of either URL,
`glab` or `gh` if installed, or a local clone of this repository beside the
one being worked on. Don't assume any particular tool is present.

## Working as an agent in any OAF repository

### How OAF writes

- Non-partisan: nothing in these files should imply endorsement or criticism
  of any party, candidate, or position.
- Australian English throughout.
- No em dashes. Use a hyphen, a comma, or a full stop.
- Active not passive voice.
- Give each sentence a clear subject, especially where a paragraph has
  more than one candidate for it.
- State a choice's benefit directly rather than justifying by saying the
  alternative was worse.
- Plain words over jargon. Use a technical term or acronym only when
  accuracy and clarity need it, and link its first use to an
  authoritative reference - from our repos where one exists, or a
  reputable general source otherwise.
- Be concise: include only the words and information people need. Code
  and its comments already explain what and why - link to them, with enough
  context for the reader to decide whether to follow it.
- Disclose AI involvement in both places the contributing guide asks for
  ([`CONTRIBUTING.md`](CONTRIBUTING.md) for GitLab,
  [`.github/CONTRIBUTING.md`](.github/CONTRIBUTING.md) for GitHub): an
  `Assisted-by: <agent-name>:<model-id>` trailer on each commit, and a note
  in the merge or pull request description. Report the model actually used, not a
  remembered default.
- When leaving a review comment, give the actual replacement code instead
  of describing the change, but only when a) there are no remaining decisions
  to make, b) it replaces just one section of code, and c) it is not
  significantly longer than describing the change would be. The comment then
  reduces to the code plus a short line on the reason for the change. If any
  condition fails, describe the change in prose as usual.
- Cite sources where you can. If you adapt code or an approach from an
  identifiable source, note the reference and its licence in the commit, merge
  request or pull request description so reviewers can check for licence compatibility and gotchas.
- The four questions the July 2026 contributing guide left open were settled
  on 2026-09-30: full-word branch prefixes, project-specific staging, no
  Contributor Licence Agreement, and a verified signature on every commit
  pushed to GitLab. Repositories that stay on GitHub do not require
  signatures. DCO sign-off is encouraged on both hosts, but requiring it is
  paused.

### How to operate

- Fetch before you plan, and again before rewriting a file wholesale. A local
  clone can be many commits behind `origin/main`, and a change designed
  against a stale file quietly reverts whatever landed in between. Compare
  against the remote rather than the working copy: `git fetch` then
  `git log --oneline main..origin/main`, or read the file from the remote if
  the clone can't be fetched.
- Before starting a non-trivial task, or one that differs from what was
  asked, state the intended approach and get agreement on it before writing
  any code. This is about the plan itself, not about tool permissions.
  Claude Code's `/plan` mode implements this directly; other agents should
  reach the same checkpoint by whatever means they have available.
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
- When you notice something worth suggesting beyond what was asked, put it
  as a short bullet list at the start of your reply, clearly separated from
  the change itself. That lets the reviewer accept it, adjust the request,
  or defer it, rather than burying it in prose alongside the
  implementation.
- Stage commits rather than making them, unless the human has explicitly
  asked you to commit: `git add` the files, then write the proposed message
  (with the `Assisted-by:` trailer) to `.git/GITGUI_MSG` and display it.
  Check that file first; if it already has content, ask before overwriting.
  A DCO sign-off is a certification only a person can make, so the commit
  is normally the human's deliberate act.
  Never add `Signed-off-by` or `Co-authored-by` on an AI agent's behalf, and
  never strip a human's.
- Don't hard-wrap sentences in prose in merge or pull request descriptions, issue bodies, issue comments, or review comments, in any OAF repository, on GitLab or GitHub.
  GitHub renders each newline in those fields as a line break, so text wrapped at a column width comes out ragged.
  Write one sentence per line instead, however long that line gets, and check the rendered result after posting.
  This gives each sentence equal emphasis by starting at the left margin, and balances GitHub's hard-wrap behaviour against long lines being awkward in some text editors.
  This applies to bodies passed via `--body`, `--body-file`, or a heredoc just as much as to text typed into the web UI.
  Hard-wrapping markdown files committed to a repository is a different matter and stays fine.
- Keep a merge or pull request description to what a reviewer needs: two or three
  sentences on what changed and why, or the same in dot points, plus a
  sentence or two on how you checked it. The diff already shows what changed
  line by line, so spend the description on what it can't, the reason, the
  constraint, the thing you verified. Describe the change's final state, not
  the path taken to reach it. Drafts you revised, options you rejected, and
  audits of your own earlier work belong in a review comment, where a reviewer
  can reply to them. Delete a template section that doesn't apply rather than
  filling it with "N/A".
- Merge or pull requests an agent creates are opened as drafts and assigned
  to the human driving the change, not to the agent. Taking one out of draft
  is the human's call. On GitLab, agents open merge requests as the
  `oaf-agent` account, so the human who signed the commits can approve them.
- Issues on GitHub and GitLab have no draft state. Don't create one directly, draft the
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
- Hyperlink a reference to a specific code or document section, where
  possible, instead of only naming it in prose.
- When reviewing someone else's merge or pull request, prefer leaving a fix
  as a suggested change or comment. Only push a commit to a team member's
  branch when it is small, unambiguous and uncontroversial.

## About this repository

Everything above is org-wide. This section and the next are about this
repository itself, so a reader who fetched this file from another
repository can stop here.

This repository is [`openaustralia/templates`](https://gitlab.com/openaustralia/templates)
on GitLab, where changes are made through merge requests per
[`CONTRIBUTING.md`](CONTRIBUTING.md). Its `main` branch is copied to
[`openaustralia/.github`](https://github.com/openaustralia/.github) on GitHub,
so the two always hold the same history. Never commit to `.github` directly:
the next copy would fail, or overwrite the change.

It serves both hosts:

- **GitLab:** every project in the `openaustralia` group inherits the issue
  and merge request templates under `.gitlab/`, because this is the group's
  template project. The root `CONTRIBUTING.md` is the GitLab guide.
  `pointers/` holds the small files each project gets at its Cutover.
- **GitHub:** `openaustralia/.github` is a [GitHub special repository](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file):
  files under `.github/` are inherited by every repository in the
  `openaustralia` org that doesn't provide its own copy, so
  `.github/CONTRIBUTING.md` is the GitHub guide. `profile/README.md` is
  unrelated to that mechanism. It's the org's [profile README](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/personalizing-your-profile#adding-a-public-profile-readme-for-your-organization),
  shown at github.com/openaustralia.

The GitLab group's own README is in the
[`gitlab-profile`](https://gitlab.com/openaustralia/gitlab-profile) project,
not here. Don't confuse either profile with the root `README.md`, which
documents this repository.

There is no build, lint, or test step. The GitHub issue forms are the one
part with a schema worth checking before you push. Validate them against the
[GitHub issue-forms schema](https://www.schemastore.org/github-issue-forms.json)
rather than guessing at the syntax. Nothing in this repository runs that check
for you, and the forms only render on the default branch, so the first real
confirmation is opening a new issue after the copy to GitHub.

## Files that reference each other

Several files cross-reference one another by content, not by any tooling.
Keep them consistent by hand when editing:

- OAF's four Collections and morph.io are listed in **six** places: the "Our
  Collections" table and the sentence after it in `profile/README.md`, the
  "Support our work" paragraph in that same file, the "Which site is this
  about?" dropdown in each of `.github/ISSUE_TEMPLATE/bug_report.yml` and
  `.github/ISSUE_TEMPLATE/feature_request.yml`, and the same question in each
  of `.gitlab/issue_templates/Bug.md` and `Feature.md`. Adding, renaming, or
  retiring one means editing all six. Nothing checks this for you.
- `.github/CODEOWNERS` names a team (`@openaustralia/staff`) that must
  actually have write access to repos inheriting this file. A team with no
  access is silently ignored by GitHub rather than erroring (see commit
  `b09ffcd`, which fixed exactly this).
- The `type:` key in each issue form (`Bug`, `Feature`) names an issue type
  that must be enabled on the `openaustralia` org. Check the org's issue types
  before changing either value, and confirm the result on a real issue.
- The `Assisted-by:` example appears in five places: both contributing guides
  (`CONTRIBUTING.md` and `.github/CONTRIBUTING.md`), the "How OAF writes"
  subsection here, and the comment at the end of each of
  `.github/PULL_REQUEST_TEMPLATE.md` and
  `.gitlab/merge_request_templates/Default.md`. Changing the separator or the
  model-id form means editing all five.
- The merge or pull request description rule is stated in five places: the
  "How to operate" subsection here, the "Merge requests" list in
  `CONTRIBUTING.md`, the "Pull requests" list in `.github/CONTRIBUTING.md`,
  and the comments in `.github/PULL_REQUEST_TEMPLATE.md` and
  `.gitlab/merge_request_templates/Default.md`. Changing the expected length
  means editing all five.
- `pointers/AGENTS.md` and the fetch instructions at the top of this file
  name the same raw URL. Moving this file means editing both.
- `openaustralia/morph`'s `AGENTS.md` quotes the "Working as an agent in any
  OAF repository" heading and summarises what both of its subsections cover.
  Renaming the heading or moving a rule between subsections means editing
  that file too.
