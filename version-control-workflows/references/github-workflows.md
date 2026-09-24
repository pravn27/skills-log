# GitHub Workflows

Use this reference only after detecting GitHub as the provider or when the user explicitly asks about GitHub.

## Establish context

Confirm the repository owner/name, authenticated identity, remote URL, source branch, target branch, and whether the repository is a fork. If GitHub CLI is available, read-only checks may include:

```bash
gh auth status
gh repo view
gh pr status
gh pr checks <number>
```

Do not authenticate, change accounts, or broaden token scopes without the user's request.

## Pull requests

- Compare the intended source and target branches before creation.
- Inspect repository templates and contribution instructions.
- Use draft state for incomplete work when appropriate.
- Include purpose, approach, validation, risk, screenshots or evidence when useful, and linked issues only when accurate.
- Inspect changed files and checks after creation; remote comparison can differ from a local diff when branches moved.
- Creating, editing, reviewing, commenting on, closing, reopening, or merging a pull request changes external state and requires user authorization.

Example commands are patterns, not permission:

```bash
gh pr view <number> --comments
gh pr diff <number>
gh pr create --base <base> --head <head> --title <title> --body-file <file>
gh pr merge <number> --merge
```

Select `--merge`, `--squash`, or `--rebase` only when repository policy and the user-requested outcome support it.

## Rules and protected branches

GitHub branch protection rules and rulesets can require reviews, status checks, signed commits, linear history, merge queues, or other conditions. Inspect existing rules before recommending a change. Do not bypass protections or alter rules because a push or merge is blocked.

Use [GitHub protected-branch documentation](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches) and current ruleset documentation when exact behavior or plan availability matters.

## Checks and Actions

- Identify the failing check and open its logs before changing code.
- Distinguish branch-push runs, pull-request runs, merge-queue runs, and deployment jobs.
- Treat workflow files as executable supply-chain configuration.
- Do not rerun, cancel, approve, or dispatch a workflow unless authorized.
- Do not expose Actions secrets, environment secrets, or logs containing credentials.

## Reviews

Check CODEOWNERS and required-review rules. Submit a formal approval, request changes, or review comment only when the user asks; drafting review feedback is not authorization to post it. Re-evaluate after new commits or dismissed reviews.

## Releases and tags

Resolve whether the task is to create a Git tag, GitHub Release, generated notes, prerelease, latest release, or uploaded assets. Verify the tag target and artifacts. Creating or deleting tags/releases is a remote mutation.

## Issues and linking

Do not create, close, assign, label, or link an issue without authorization. Use closing keywords only when the repository's intended automation and issue relationship are known.

## Official anchors

- [GitHub pull request documentation](https://docs.github.com/en/pull-requests)
- [GitHub branch and merge documentation](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository)
- [GitHub Actions documentation](https://docs.github.com/en/actions)
- [GitHub CLI manual](https://cli.github.com/manual/)
