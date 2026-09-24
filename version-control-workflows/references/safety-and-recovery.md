# Safety and Recovery

Read this reference before destructive cleanup, history rewriting, force-push, ref deletion, secret removal, or recovery from an unclear repository state.

## Risk classes

| Class | Examples | Required handling |
|---|---|---|
| Read-only | status, diff, log, show, remote listing | Safe when scoped to the requested repository and sensitive output is protected |
| Reversible local | create branch, create worktree, stage selected files, ordinary commit | Ensure target and worktree state are known; act only within requested scope |
| Complex local | merge, rebase, cherry-pick, amend, restore, stash, tag | Explain state change, abort path, and collaborator impact |
| Remote mutation | push, review creation, comment, merge, release, settings | Requires explicit user request and remote verification |
| Destructive or rewriting | reset with overwrite, clean, force-push, ref deletion, published-history rewrite, purge, obliterate | Resolve exact targets, create a recovery point when possible, and obtain explicit confirmation immediately before action |

## Preflight for high-risk operations

1. Resolve the repository or workspace root and authoritative server.
2. Show the active branch/stream, target ref/path, and relevant status.
3. Inventory staged, unstaged, untracked, ignored, conflicted, and nested-repository content.
4. Determine whether affected commits or files are published or shared.
5. Record recoverable identifiers: commit IDs, refs, reflog entries, changelists, shelves, or server revision numbers.
6. Prefer a backup ref, patch, bundle, shelf, or separate worktree when it materially improves recoverability.
7. State exactly what will be removed, rewritten, or made inaccessible.
8. Obtain confirmation for the resolved command and target.

Do not use an unresolved variable, broad directory, home directory, repository root wildcard, or ambiguous ref as a destructive target.

## Common Git recovery choices

| Situation | Usually prefer | Reason |
|---|---|---|
| Undo a shared commit | `git revert` | Preserves published history and adds an auditable inverse |
| Stop an in-progress merge | `git merge --abort` after inspection | Returns toward the pre-merge state when Git can do so safely |
| Stop an in-progress rebase | `git rebase --abort` after inspection | Restores the original branch state when possible |
| Recover a moved or deleted local ref | inspect `git reflog`, then create a new recovery branch | Avoids further moving the current branch while preserving the found commit |
| Unstage without discarding working content | `git restore --staged <path>` or repository-compatible equivalent | Changes the index while preserving the working file |
| Undo shared merge effects | carefully planned revert, sometimes with a mainline parent | Avoids rewriting shared history but requires correct parent reasoning |
| Replace a remote rewritten branch | confirmed `--force-with-lease` with expected ref state | Refuses some overwrites when the remote changed unexpectedly |

These are decision patterns, not automatic commands. Inspect Git version, operation state, and exact paths first.

## Reset and restore boundaries

- A soft reset moves the branch but keeps index and working tree.
- A mixed reset normally moves the branch and resets the index.
- A hard reset can overwrite tracked working-tree and index content.
- Restore can overwrite working-tree or staged content depending on options.

Never choose a mode from memory alone when user work may be affected. Explain the before-and-after states and preserve a recovery ref when appropriate.

## Clean boundaries

`git clean` can permanently remove untracked or ignored files that Git cannot recover. Use a dry run and explicit pathspecs, but do not treat a dry run as sufficient authorization. Check nested repositories and build artifacts separately. Never use a broad clean command merely to make tests pass.

## Force-push boundaries

Before a confirmed force-push:

- verify remote, branch, expected remote commit, and who may have based work on it;
- fetch current remote state;
- prefer a lease tied to the expected remote state;
- preserve or communicate the old tip;
- confirm branch protections and incident or change process;
- verify the remote tip after the push.

Do not use `--force` when a lease can protect against an unexpected remote update.

## Secret exposure

Stopping future commits does not remove a secret from history, caches, forks, pull-request diffs, CI logs, releases, or clones.

1. Revoke or rotate the credential first through the responsible system.
2. Determine exposure scope without repeating the secret.
3. Follow the provider and organization incident process.
4. Plan history rewriting only if required, with coordination and backups.
5. Remove derived artifacts and logs where authorized.
6. Add prevention such as scanning, ignore rules, or secret management.

Do not print or paste the secret into commands, messages, or reports.

## Stop conditions

Stop and request direction when:

- repository ownership or target remote is ambiguous;
- the worktree contains overlapping user changes;
- the expected ref changed after inspection;
- a destructive target expands beyond the confirmed scope;
- required backup or recovery information is unavailable;
- permissions, policy, authentication, or server response contradict the plan;
- a remote mutation returns an uncertain result;
- recovery would affect collaborators or systems outside the user's stated scope.
