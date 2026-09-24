# Collaboration Workflows

Use this reference to select a team workflow and carry a change through review, validation, integration, and release without imposing one provider's terminology.

## Select a workflow from constraints

Evaluate deployment frequency, release support, team size, regulatory needs, repository topology, CI reliability, review latency, and rollback requirements.

| Workflow | Fits | Main trade-off |
|---|---|---|
| Short-lived branch plus review | Most teams needing review and CI before main | Review latency and stale branches if changes grow too large |
| Trunk-based development | Frequent integration with strong automated checks and feature flags | Demands disciplined small changes and reliable main-branch protections |
| Fork-based contribution | Open source or restricted write access | Extra remote and synchronization complexity |
| Release branches | Products supporting multiple maintained versions | Backports, drift, and added policy overhead |
| Long-lived environment or feature branches | Rare cases with unavoidable parallel lifecycle needs | Merge debt and unclear source of truth |

Do not label one workflow an industry standard for every team. Prefer the simplest workflow that satisfies risk, release, and collaboration requirements.

## Commit quality

A useful commit is coherent, reviewable, buildable when practical, and honest about scope.

- Stage explicit files or hunks.
- Separate generated or mechanical changes when that materially improves review.
- Use the repository's message convention; do not impose Conventional Commits unless the project uses it.
- Explain why a change exists when the diff alone does not reveal intent.
- Preserve authorship and required sign-off or provenance.
- Never include secrets, transient debug data, or unrelated formatting.

## Pull or merge request lifecycle

1. Confirm source and target branches.
2. Inspect the provider's comparison, not only the local working-tree diff.
3. Keep scope focused and identify dependencies.
4. Write a title and description covering purpose, approach, validation, risk, and rollout or rollback when relevant.
5. Mark incomplete work as draft when supported.
6. Request the right reviewers and honor code ownership.
7. Respond to feedback with code, explanation, or a documented disagreement.
8. Re-run required checks after material changes.
9. Use the repository's accepted merge method.
10. Verify integration and clean up branches only when safe and desired.

Creating, updating, approving, closing, or merging a review is an external mutation. Do it only when requested.

## Review method

Review for correctness, security, tests, failure behavior, maintainability, performance, compatibility, operations, and documentation in proportion to risk.

- Read the request and acceptance criteria first.
- Inspect the full comparison and important unchanged context.
- Distinguish blocking defects from questions and optional suggestions.
- Give evidence, impact, and a concrete correction.
- Avoid style comments already enforced automatically.
- Recheck after updates; do not assume an earlier approval still applies.

## Checks and protections

Treat CI and branch policy as part of the workflow contract:

- required build, test, security, quality, and status checks;
- required reviewers or code owners;
- resolved-conversation requirements;
- signed commit or tag requirements;
- linear-history, merge-queue, or allowed-merge-method rules;
- deployment approvals and environment protections.

If a check fails, inspect the failure and fix the cause. Do not bypass it merely because bypass permission exists. If a check is flaky, document evidence and follow the repository's exception process.

## Merge methods

| Method | Useful when | Consequence |
|---|---|---|
| Merge commit | Topology and branch context matter | Preserves all commits and adds a merge node |
| Squash merge | The review should become one mainline change | Source commits are not ancestors of the result |
| Rebase/fast-forward | Linear history is required | Rewrites source commits or advances without a merge node |

Use the configured repository method. If several methods are allowed and neither repository guidance nor the user identifies the intended result, explain the rollback, traceability, and backport consequences and ask the user to choose; do not select one silently.

## Release collaboration

Resolve the release source commit, versioning scheme, tag type, artifacts, notes, checks, approval, publication target, and rollback before publishing. A local tag is not a hosted release, and a hosted release is not proof that deployed software is healthy.

## Evidence for learning or governance

Capture a sanitized commit graph, review description, check results, merge decision, rollback plan, and retrospective. Measure change size, review time, escaped defects, rollback time, and developer friction before changing team policy.
