# AGENTS.md

This file provides guidance to AI coding agents (Claude Code, GitHub Copilot,
and others) when working with code in this repository.

## What this repository is

`openaustralia/.github` is a [GitHub special repository](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file):
files under `.github/` here are inherited by every repository in the
`openaustralia` org that doesn't provide its own copy. `profile/README.md` is
unrelated to that mechanism — it's the org's [profile README](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/personalizing-your-profile#adding-a-public-profile-readme-for-your-organization),
shown at github.com/openaustralia. Don't confuse it with the root `README.md`,
which documents this repository itself.

There is no build, lint, or test step — the repository is markdown, one
`CODEOWNERS` file, and one `FUNDING.yml`. Changes are reviewed by opening a PR
against `main` per `.github/CONTRIBUTING.md`.

## Files that reference each other

Several files cross-reference one another by content, not by any tooling —
keep them consistent by hand when editing:

- `.github/CONTRIBUTING.md` links to `CLA/CLA.md` by URL and quotes the exact
  CLA sign-off sentence (`"I have read the CLA Document and I hereby sign the
  CLA"`) — it must match verbatim in both files.
- `.github/CONTRIBUTING.md` describes the AI-disclosure trailer convention
  (`Assisted-by: <agent-name>/<model-id>`) that `CLA/CLA.md` §5 also assumes.
- `.github/CODEOWNERS` names a team (`@openaustralia/staff`) that must
  actually have write access to repos inheriting this file — a team with no
  access is silently ignored by GitHub rather than erroring (see commit
  `b09ffcd`, which fixed exactly this).
- `profile/README.md`'s service table and `.github/CONTRIBUTING.md`'s intro
  both list OAF's public services; keep new services in sync across both if
  either changes.

## Conventions specific to this org

- Non-partisan: nothing in these files should imply endorsement or criticism
  of any party, candidate, or position.
- Australian English throughout.
- The CLA and CONTRIBUTING.md are still marked as evolving (see the "Open
  questions" section at the end of CONTRIBUTING.md) — don't present unsettled
  points as decided.
