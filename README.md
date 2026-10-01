# templates

The OpenAustralia Foundation's shared contribution policy and community
files, for both of the hosts our code lives on.

Most OAF projects are in the [`openaustralia`](https://gitlab.com/openaustralia)
GitLab group. The Planning Alerts scrapers, other repositories that
[morph.io](https://morph.io) runs, and upstream projects we have forked stay on
GitHub. This repository holds the policy for both in one place.

It is canonical here on GitLab. Its `main` branch is copied to
[`openaustralia/.github`](https://github.com/openaustralia/.github), which
GitHub reads for the `openaustralia` organisation. Never change `.github`
directly.

## What's here

| Path | Host | Purpose |
| --- | --- | --- |
| [`CONTRIBUTING.md`](CONTRIBUTING.md) | GitLab | Contributing guide for projects on GitLab |
| [`.gitlab/merge_request_templates/`](.gitlab/merge_request_templates) | GitLab | Default merge request template, inherited by every project in the group |
| [`.gitlab/issue_templates/`](.gitlab/issue_templates) | GitLab | Bug report and feature request templates, inherited the same way |
| [`pointers/`](pointers) | GitLab | Small `CONTRIBUTING.md` and `AGENTS.md` files each project gets at its Cutover |
| [`.github/CONTRIBUTING.md`](.github/CONTRIBUTING.md) | GitHub | Contributing guide for repositories on GitHub |
| [`.github/PULL_REQUEST_TEMPLATE.md`](.github/PULL_REQUEST_TEMPLATE.md) | GitHub | Default pull request template |
| [`.github/ISSUE_TEMPLATE/`](.github/ISSUE_TEMPLATE) | GitHub | Default bug report and feature request forms |
| [`.github/FUNDING.yml`](.github/FUNDING.yml) | GitHub | Powers the "Sponsor" button across the org's repositories |
| [`.github/CODEOWNERS`](.github/CODEOWNERS) | GitHub | Reviewers for this repository on GitHub |
| [`profile/README.md`](profile/README.md) | GitHub | The org profile page shown at [github.com/openaustralia](https://github.com/openaustralia) |
| [`AGENTS.md`](AGENTS.md) | Both | Guidance for AI coding agents in any OAF repository |

The GitLab group's README lives in its own
[`gitlab-profile`](https://gitlab.com/openaustralia/gitlab-profile) project.

A project or repository can override any inherited file by adding its own
copy. [Right to Know](https://github.com/openaustralia/righttoknow) does this
for `CODEOWNERS`.

## Copying to GitHub

Until GitLab mirrors this repository automatically, a person copies `main` to
GitHub after each merge:

```sh
git fetch origin
git push git@github.com:openaustralia/.github.git origin/main:main
```

The push is always a fast-forward. If GitHub refuses it as non-fast-forward,
someone has changed `.github` directly: stop and reconcile rather than
forcing it.

## Contributing

This repository follows the [GitLab contributing guide](CONTRIBUTING.md) it
defines for everyone else.

---

*OpenAustralia Foundation - https://www.oaf.org.au*
