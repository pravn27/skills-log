# Version-Control Learning Levels

Use this reference to design a hands-on path from first repository to expert workflow leadership. Adapt breadth to the target role, provider, and existing evidence.

## Progression model

| Level | Capability | Typical autonomy | Evidence |
|---|---|---|---|
| Beginner | Understand and use a local repository safely | Guided work in a disposable repository | Explain the basic states and complete a small commit-and-branch exercise |
| Intermediate | Collaborate through remotes and reviews | Independent familiar work with review | Deliver a focused branch through a pull or merge request and resolve a conflict |
| Advanced | Design, diagnose, and recover complex workflows | Independent ambiguous work | Debug history and CI/review problems, choose trade-offs, and recover safely |
| Expert | Govern version control across teams and systems | Strategic leadership and mentoring | Establish evidence-based standards, migrations, controls, and incident practices |

## Beginner

### Concepts

- repository, working tree, staging area, commit, object ID, branch, `HEAD`, remote, clone, fetch, pull, and push;
- tracked, untracked, modified, staged, and committed states;
- diff, status, log, ignore rules, and basic configuration;
- the distinction between Git and a Git hosting platform.

### Hands-on sequence

1. Initialize a disposable repository and create two small commits.
2. Predict the output of `status` before and after staging.
3. Inspect the working-tree and staged diffs.
4. Create a branch, make a change, and merge it without conflict.
5. Clone a local bare repository to simulate a remote safely.
6. Make a mistake, then recover it with a non-destructive method.

### Exit gate

The learner can explain where a change exists, predict which files a commit will contain, create a focused commit, use a branch, inspect history, and distinguish local work from remote publication.

## Intermediate

### Concepts

- upstream tracking, fetch versus pull, ahead/behind state, merge bases, merge conflicts, rebase, cherry-pick, revert, tags, and releases;
- feature branches, trunk-based development, forks, pull/merge requests, review comments, CI checks, and protected branches;
- commit scope, meaningful messages, ownership, and reviewability.

### Hands-on sequence

1. Synchronize a branch after inspecting incoming changes.
2. Resolve a realistic text conflict and explain why it occurred.
3. Compare a merge with a rebase in separate disposable branches.
4. Open a draft pull or merge request in a training repository.
5. Respond to review, update the branch, and verify checks.
6. Tag a training release and document how to undo it before publication.

### Exit gate

The learner can independently take a focused change from branch creation through review, choose a suitable integration method, resolve ordinary conflicts, and explain the effects on collaborators.

## Advanced

### Concepts

- commit graph analysis, reflog, interactive rebase, bisect, worktrees, signed commits or tags, submodules or alternatives, large-file strategies, hooks, and CI integration;
- branch policies, required checks, merge queues, release branching, monorepo concerns, permissions, and auditability;
- recovery from incorrect merges, lost refs, partial publication, secret exposure, and failed release operations.

### Hands-on sequence

1. Use `bisect` to isolate a seeded regression.
2. Recover a deleted local branch through the reflog.
3. Diagnose a detached `HEAD`, divergent branches, and an interrupted rebase.
4. Compare merge strategies against audit, rollback, and release requirements.
5. Design a protected-branch and review policy for a sample team.
6. Run an incident simulation involving an accidentally published secret without exposing a real secret.

### Exit gate

The learner can diagnose unfamiliar repository states, recover without losing unrelated work, explain history and policy trade-offs, and design a workflow that fits team and delivery constraints.

## Expert

### Concepts

- organization-wide repository governance, identity, signing, retention, audit, compliance, disaster recovery, migration, mirroring, scaling, and supply-chain controls;
- developer-experience measurement, exception handling, policy rollout, automation ownership, and cross-platform migration;
- mentoring, incident leadership, and standards that balance safety with flow.

### Evidence projects

- migrate a realistic training repository between platforms with preserved refs and a verified rollback plan;
- design a multi-team branching and release model, pilot it, measure outcomes, and revise it;
- create an incident runbook and lead a recovery exercise;
- teach a complex history or recovery concept and review another person's solution.

### Exit gate

Expertise requires sustained evidence across systems and teams. The learner can set policy, handle exceptions, lead recovery, justify trade-offs, and improve outcomes without relying on one provider's UI or memorized commands.

## Practice rules

- Use disposable repositories, forks, or training namespaces for destructive and recovery exercises.
- Ask for predictions before commands and explanations after results.
- Include one failure and recovery task at every level.
- Save evidence such as command transcripts with secrets removed, diagrams, review links, runbooks, and retrospectives.
- Use sustainable focused sessions and repeated retrieval; do not use extreme hours as a proxy for mastery.
