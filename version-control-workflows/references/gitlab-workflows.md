# GitLab Workflows

Use this reference only after detecting GitLab as the provider or when the user explicitly asks about GitLab.

## Establish context

Confirm the GitLab instance, namespace/project, authenticated identity, source branch, target branch, fork relationship, and project policies. Self-managed GitLab may differ from GitLab.com by version, tier, and administrator settings.

If `glab` is installed and authenticated, read-only patterns may include:

```bash
glab auth status
glab repo view
glab mr list
glab mr view <number>
glab ci status
```

Do not authenticate, change hosts, or modify token scopes without authorization.

## Merge requests

- Inspect contribution guidance and merge-request templates.
- Confirm source and target branches and whether the request should be draft.
- Include purpose, approach, validation, risk, rollout/rollback, and accurate issue links.
- Check reviewers, approvers, Code Owners, discussions, pipeline results, merge conflicts, and merge trains or auto-merge conditions.
- Creating, editing, commenting on, approving, closing, or merging a merge request is an external mutation.

Example command patterns:

```bash
glab mr diff <number>
glab mr checks <number>
glab mr create --source-branch <source> --target-branch <target>
glab mr merge <number>
```

Check the installed `glab` help before relying on options; command behavior can change.

## Pipelines and merge checks

- Distinguish branch, merge-request, merged-result, scheduled, and child pipelines.
- Inspect job logs and artifacts before diagnosing a failure.
- Do not retry, cancel, play, or approve a job without authorization.
- Respect required successful pipelines, resolved-discussion rules, approval rules, and external status checks.
- Treat `.gitlab-ci.yml` and included CI configuration as executable supply-chain code.

## Protected branches and tags

Protected refs control who may push, merge, or create tags. Check the project's current policy and GitLab version/tier. Do not change protection, use bypass privileges, or push directly merely because permissions allow it.

## Merge methods

GitLab projects may allow merge commits, semi-linear history, fast-forward merges, squashing, auto-merge, or merge trains. Use project configuration and current MR state rather than assuming a default.

## Releases

Separate Git tags, GitLab Releases, milestones, packages, and deployed environments. Verify the commit, tag, assets, evidence, notes, and publication state. Release creation or deletion requires explicit authorization.

## Official anchors

- [GitLab merge request documentation](https://docs.gitlab.com/user/project/merge_requests/)
- [GitLab protected branches](https://docs.gitlab.com/user/project/repository/branches/protected/)
- [GitLab CI/CD pipelines](https://docs.gitlab.com/ci/pipelines/)
- [GitLab CLI documentation](https://docs.gitlab.com/editor_extensions/gitlab_cli/)
