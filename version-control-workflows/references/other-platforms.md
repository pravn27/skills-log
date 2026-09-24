# Other Platforms and Version-Control Systems

Use this reference for Git hosts other than GitHub or GitLab and for repositories that are not Git-based. Detect first; do not translate Git commands blindly.

## Identify the system

Look for repository metadata and configured tooling:

| Signal | Likely system |
|---|---|
| `.git/` or successful `git rev-parse` | Git |
| `.hg/` or successful `hg root` | Mercurial |
| `.svn/` or successful `svn info` | Apache Subversion working copy |
| `P4CONFIG`, `p4 set`, or successful `p4 info` | Perforce Helix Core |

Nested repositories and exported source trees can make metadata ambiguous. Stop before mutating when the repository root or VCS is uncertain.

## Bitbucket Cloud or Data Center

Bitbucket adds pull requests, reviewers, merge checks, pipelines, deployments, branch restrictions, and workspace/project permissions around Git repositories.

- Detect Cloud versus Data Center and its version.
- Confirm workspace/project, repository, source/target branches, authenticated account, and merge checks.
- Use the installed CLI, API, or UI only after checking current official documentation; do not assume GitHub CLI syntax.
- Respect branch restrictions, required approvals, build status, unresolved tasks, and merge strategy.

Official anchor: [Bitbucket pull-request review documentation](https://support.atlassian.com/bitbucket-cloud/docs/use-pull-requests-for-code-review/).

## Azure Repos

Azure Repos adds pull requests, reviewers, build validation, status checks, work-item links, comment-resolution rules, permissions, and branch policies around Git.

- Confirm organization, project, repository, source/target branches, and Azure DevOps Services versus Server.
- Inspect policy before recommending direct push or merge.
- Use `az repos` only when the Azure DevOps CLI extension and authentication are configured.
- Do not grant or use policy-bypass permissions merely to complete a blocked change.

Official anchors: [Azure Repos Git documentation](https://learn.microsoft.com/azure/devops/repos/git/) and [branch policies](https://learn.microsoft.com/azure/devops/repos/git/branch-policies).

## Gitea, Forgejo, and other Git forges

- Detect the product and version from the remote host or instance metadata.
- Start with provider-neutral Git operations.
- Verify pull-request terminology, API routes, protected-branch rules, actions/runners, release behavior, and CLI availability against that instance's documentation.
- Do not send GitHub- or GitLab-specific commands to a compatible-looking forge without verification.

## Mercurial

Mercurial is a distributed VCS, but its changesets, named branches, bookmarks, phases, evolution features, and command behavior are not direct Git equivalents.

- Inspect with `hg root`, `hg status`, `hg summary`, `hg paths`, and `hg log` as needed.
- Use `hg incoming` and `hg outgoing` to understand exchange before pull or push.
- Prefer `hg backout` for a shared changeset when appropriate.
- Treat purge, strip, rollback-like extensions, history editing, and phase changes as high risk.

Official anchor: [Mercurial command reference](https://mercurial-scm.org/help/commands).

## Apache Subversion

Subversion is a centralized VCS. A working copy has a server URL and revisioned paths; update and commit interact with the central repository differently from Git.

- Inspect with `svn info`, `svn status`, `svn diff`, and `svn log`.
- Use `svn update` with awareness that it changes the working copy and may create conflicts.
- A commit publishes directly to the central repository; treat it as an external mutation.
- Confirm repository layout before copying, switching, branching, tagging, merging, or relocating paths.
- Do not apply Git branch or staging-area explanations to SVN.

Official anchor: [Apache Subversion Quick Start](https://subversion.apache.org/quick-start).

## Perforce Helix Core

Perforce commonly uses server-managed depots, clients/workspaces, changelists, opened files, streams, and submit operations.

- Inspect connection and workspace with `p4 info`, `p4 set`, `p4 client -o`, `p4 opened`, and `p4 status` only when configured.
- Verify depot paths, client view, stream, changelist, file locks, and server identity before edits or submit.
- Submitting publishes to the server; shelving, unshelving, reconcile, integrate, resolve, obliterate, and administrative operations have distinct risks.
- Never translate `git reset`, branch, or force-push guidance directly to Perforce.

Official anchor: [Helix Core command-line guide](https://help.perforce.com/helix-core/server-apps/p4guide/current/Content/P4Guide/Home-p4guide.html).

## Safe adapter rule

For an unfamiliar VCS or forge:

1. identify product, version, repository root, server, workspace, and active line of work;
2. read status and history without mutation;
3. consult official documentation for the exact operation;
4. explain local and server-side effects;
5. preview exact targets and rollback;
6. execute only with appropriate authorization;
7. verify on the authoritative server when remote state changed.
