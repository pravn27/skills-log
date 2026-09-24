# Git Fundamentals

Use this reference for concept explanations and ordinary local Git work. Anchor command choices in Git's data model rather than recipes alone.

## Core concept map

| Concept | Purpose | Why it is used | How it works | Use when |
|---|---|---|---|---|
| Repository | Store project history and references | Makes change history addressable and shareable | A `.git` directory or equivalent stores objects, refs, configuration, and metadata | A project needs Git-managed history |
| Working tree | Present editable files for one checked-out state | Lets a user edit ordinary files | Git materializes a commit plus local modifications on disk | Creating or testing changes |
| Index/staging area | Define the exact content of the next commit | Separates selection from recording | The index stores a proposed tree independent of unstaged changes | Building focused commits or resolving conflicts |
| Commit | Record an immutable project snapshot with metadata and parent links | Creates reviewable, transferable history | A commit points to a tree, parents, author/committer data, and message | A coherent change is ready to record |
| Branch | Give a movable name to a line of development | Makes parallel work understandable | A branch ref advances to new commits | Isolating a task or maintaining a line |
| `HEAD` | Identify the current checked-out commit or branch | Tells Git where new commits attach | Usually a symbolic ref to a branch; sometimes a direct commit in detached state | Inspecting or changing the current context |
| Remote | Name another repository and its ref namespace | Supports collaboration and synchronization | Fetch maps remote refs into remote-tracking refs; push requests remote ref updates | Sharing or receiving history |
| Tag | Give a durable name to a specific object, usually a release commit | Supports releases and stable references | Lightweight or annotated refs point at an object | Marking a release or milestone |

## The everyday state model

Use `git status --short --branch` as the first view. Explain that a file can differ across three comparisons:

1. working tree versus index;
2. index versus `HEAD`;
3. local refs versus remote-tracking refs after the most recent fetch.

Useful inspections:

```bash
git diff
git diff --cached
git diff HEAD
git log --oneline --decorate --graph --all -n 20
git show --stat --oneline HEAD
```

Do not say “Git saved the file” without naming the layer. A working-tree edit, staged content, local commit, pushed ref, and merged pull request are different states.

## A focused local change

1. Inspect repository root, branch, and status.
2. Make or review the requested edits.
3. Inspect `git diff -- <path>`.
4. Stage explicit paths or hunks with `git add <path>` or `git add -p`.
5. Inspect `git diff --cached`.
6. Run relevant tests or validation.
7. Commit only when authorized.
8. Recheck status and show the new commit.

Avoid broad staging in a dirty worktree. Never stage or commit unrelated user changes merely because they are present.

## Fetch, pull, and push

### Fetch

- **Purpose:** update local knowledge of remote refs and download missing objects.
- **Why:** inspect incoming history before changing the current branch.
- **How:** `git fetch <remote>` updates remote-tracking refs according to refspecs but normally does not modify working-tree files.
- **Use:** before comparing or integrating remote changes.

### Pull

- **Purpose:** fetch and then integrate into the current branch.
- **Why:** convenient when the repository's merge or rebase strategy is known.
- **How:** combines fetch with merge, rebase, or another configured reconciliation behavior.
- **Boundary:** do not use it as an unexplained default when strategy, local changes, or divergence are unclear.

### Push

- **Purpose:** request remote ref updates and upload necessary objects.
- **Why:** publish branches, commits, or tags for collaboration.
- **How:** sends objects and proposes ref changes subject to fast-forward rules, permissions, and server policies.
- **Boundary:** pushing is an external mutation. Confirm remote, refspec, and authorization first.

## Configuration and identity

- Inspect effective values with `git config --show-origin --get <key>` when origin matters.
- Do not silently change global identity, signing, credential helpers, aliases, hooks, or line-ending policy.
- Use repository-local configuration when the change is intentionally scoped to one project.
- Treat remote URLs and credential-helper output as potentially sensitive.
- Never place tokens or passwords directly in commands that may appear in shell history or logs.

## Ignore and attributes

- `.gitignore` prevents untracked paths from being selected by ordinary add operations; it does not untrack committed files.
- `.git/info/exclude` supports local, non-shared ignore patterns.
- `.gitattributes` controls path-specific behavior such as text normalization, diff drivers, merge drivers, and large-file filters.
- Explain team impact before changing shared ignore or attribute rules.

## Foundational gates

A learner is ready to move on when they can:

- predict `status` and diff output across working-tree, staged, and committed states;
- explain why a branch is a movable ref rather than a folder copy;
- create a focused commit without including unrelated work;
- distinguish fetch, pull, and push;
- trace a simple commit graph and identify the current `HEAD`;
- recover one ordinary mistake without destructive cleanup.

## Official anchor

Use the maintained [Git reference](https://git-scm.com/docs) for current command behavior. Check the installed Git version and each command's local help when syntax or version-specific behavior matters.
