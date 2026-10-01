# Pointers

Small files each GitLab project gets at its Cutover, so the shared policy
lives in one place here and projects do not carry copies that drift.

| File | Copy to | Notes |
| --- | --- | --- |
| [`CONTRIBUTING.md`](CONTRIBUTING.md) | the project root | Add project-specific notes below the link. |
| [`AGENTS.md`](AGENTS.md) | the project root | Add a `CLAUDE.md` containing `@AGENTS.md` beside it. |

Issue and merge request templates are not copied: GitLab projects in the
group inherit them from [`.gitlab/`](../.gitlab) here. `CODEOWNERS` stays
project-specific.
