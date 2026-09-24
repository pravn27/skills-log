# Branching and History

Use this reference for integration strategy, history editing, diagnostic graph work, and multiple-worktree decisions.

## Decision table

| Operation | Purpose | Prefer when | Avoid or pause when |
|---|---|---|---|
| Branch | Isolate a line of work | A task needs independent commits or review | The repository requires a different naming or fork workflow |
| Merge | Join histories while preserving topology | Shared branches or merge commits carry useful context | The project requires linear history or the target is wrong |
| Rebase | Replay commits onto a new base | Cleaning local unpublished history or following a linear-history policy | Commits are shared and collaborators have not agreed to the rewrite |
| Cherry-pick | Copy selected changes as new commits | Backports or narrowly selected fixes | The relationship should be represented as a merge or duplicate changes will confuse ownership |
| Revert | Add a commit that undoes earlier effects | Undoing shared or published history | A local unpublished correction is clearer and safe to rewrite |
| Reset | Move a ref and optionally index or working tree | A precisely scoped local recovery with impact understood | Any target or uncommitted content is uncertain |
| Worktree | Check out another branch in a separate directory | Parallel tasks need isolated files without another clone | Tooling assumes one worktree or paths are not understood |
| Stash | Temporarily record selected local changes | A short interruption with a clear restoration plan | It would hide long-lived work or include unrelated files accidentally |
| Bisect | Search history for the first bad commit | A reproducible regression has a known good and bad boundary | The test is flaky or commits cannot be evaluated consistently |

## Branch creation

Before creating a branch, resolve:

- intended base branch and whether it is current;
- repository naming conventions;
- local versus fork-based collaboration;
- whether another worktree already has the branch checked out.

Modern Git supports `git switch -c <branch> <base>`. Use established repository commands when contribution guidance specifies them. Never invent a base branch from habit.

## Merge reasoning

Explain the merge base, source tip, target tip, fast-forward possibility, and expected result before a non-trivial merge.

- A fast-forward advances a ref without creating a merge commit.
- A true merge commit has multiple parents and preserves topology.
- A squash merge creates a new combined commit and does not preserve source commits as ancestors.

Resolve conflicts by understanding the intended final content, not by automatically choosing “ours” or “theirs.” In rebase and some plumbing contexts, those labels can be counterintuitive. Inspect the operation and files directly.

## Rebase reasoning

Rebase copies commits onto a new base, producing new commit IDs. Before rebasing:

1. verify the exact commit range;
2. check whether commits are published or shared;
3. ensure the worktree is safe;
4. identify how to abort and how to recover through the reflog;
5. understand the later push implications.

Use interactive rebase for an explicitly requested cleanup such as reorder, squash, fixup, edit, or message change. Do not rewrite other authors' shared work casually.

## Dirty worktree before a history operation

Do not automatically stash unrelated edits. Choose after inspecting overlap and ownership:

| Situation | Safer option |
|---|---|
| Unrelated work can remain isolated from the target branch | Use a separate worktree or temporary branch/ref, then verify before moving the intended ref |
| Exact local paths must be set aside briefly | Use a focused stash only with authorization, include untracked paths only when intended, name it, and verify restoration |
| Work is coherent and the user wants it recorded | Commit it on an appropriate temporary or task branch, not as an accidental shared-history commit |
| Changes overlap the rebase or their ownership is unclear | Stop and ask; do not hide, discard, or rewrite them |

Whichever option is chosen, record the original branch tip, verify the unrelated changes afterward, and keep the recovery path until the user confirms success.

## Revert, reset, and restore

- `git revert` records a new inverse change and is normally collaboration-safe.
- `git reset` moves the current ref; modes determine index and working-tree effects.
- `git restore` copies content into the working tree and optionally the index.

Read [safety-and-recovery.md](safety-and-recovery.md) before using reset modes that can overwrite content or restore operations that discard changes.

## Cherry-pick and backport

Confirm the source commit, destination branch, dependency commits, conflict risk, and whether provenance must be recorded. Use `-x` when project policy wants a source-commit reference. Validate the resulting tree and tests; a clean cherry-pick does not prove semantic compatibility.

## Worktrees

Use `git worktree list` before creating or removing one. Keep task branches, dependencies, and generated files isolated. Do not remove a worktree containing uncommitted changes. Managed agent worktrees may have lifecycle rules beyond ordinary Git; follow the host tool's workflow.

## Bisect

Define a deterministic pass/fail check. Start from known good and bad commits, record skipped or untestable commits, and run `git bisect reset` after the result. Automated bisect scripts must return meaningful exit codes and avoid external side effects.

## History inspection

Use the smallest relevant view:

```bash
git log --oneline --decorate --graph --all
git show <commit>
git diff <base>...<tip>
git merge-base <base> <tip>
git reflog --date=local
git blame -L <start>,<end> -- <path>
```

Treat blame as line-history evidence, not proof of responsibility or intent.

## Stage gate

A practitioner is ready for shared-history operations when they can draw the before-and-after commit graph, state which commit IDs will change, explain collaborator impact, identify abort and recovery paths, and validate the resulting tree.
