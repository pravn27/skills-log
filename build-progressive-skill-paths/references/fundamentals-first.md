# Fundamentals First

Use this reference to keep a learning path grounded in transferable understanding while still reaching productive framework use quickly.

## Contents

- [Operating rule](#operating-rule)
- [Select the relevant fundamentals](#select-the-relevant-fundamentals)
- [Build the foundation-to-framework bridge](#build-the-foundation-to-framework-bridge)
- [Set stage expectations](#set-stage-expectations)
- [Develop sustainable learning and career habits](#develop-sustainable-learning-and-career-habits)
- [Use concept examples](#use-concept-examples)
- [Apply the fundamentals gate](#apply-the-fundamentals-gate)
- [Avoid anti-patterns](#avoid-anti-patterns)

## Operating rule

Treat `80% fundamentals / 20% frameworks` as a starting heuristic for the foundation phase, not a rigid time sheet or universal law.

- For many beginners, start near 70-80% underlying concepts and deliberate practice and 20-30% framework syntax.
- Adjust the split for prior knowledge, the target use case, urgency, risk, and demonstrated evidence.
- Increase framework and integration time as understanding becomes reliable, while continuing to connect framework behavior to fundamentals.
- Use a framework early when it provides a motivating visible result, but explain what problem it solves and revisit the mechanism.
- Implement only the smallest framework-free slice needed to reveal the mechanism. Do not rebuild mature libraries or frameworks without a learning reason.

The objective is not to delay useful tools. It is to prevent tool syntax from being mistaken for transferable capability.

## Select the relevant fundamentals

Choose only the foundations that support the destination and real use cases. For a software or IT path, consider:

- language semantics, runtime behavior, and execution model;
- values, state, data flow, control flow, and side effects;
- data structures, algorithms, and relevant complexity;
- interfaces, contracts, protocols, and APIs;
- data modeling, persistence, consistency, and transactions;
- operating systems, networking, concurrency, or distribution when the use case requires them;
- testing, debugging, logging, metrics, and tracing;
- security, privacy, reliability, performance, accessibility, and ethics;
- domain rules and business invariants.

For a non-software skill, identify the equivalent durable principles, vocabulary, operating mechanisms, decision rules, and quality constraints.

Do not add a foundation merely because it appears in a traditional syllabus. Connect every selected foundation to a target task, decision, failure mode, or later abstraction.

## Build the foundation-to-framework bridge

For every major framework feature or tool, answer:

1. **Real problem** — what user, engineering, or operational problem exists?
2. **Fundamental or invariant** — what durable principle controls the behavior?
3. **Purpose** — what job must be performed?
4. **Why** — why is this solution useful, and what trade-off does it introduce?
5. **Mechanism** — what data, state, control, or responsibility moves where?
6. **Minimal demonstration** — what small manual or basic implementation exposes the mechanism?
7. **Framework mapping** — which API, convention, or component implements it?
8. **Abstraction benefit** — what complexity, repetition, or risk does the framework reduce?
9. **Abstraction leak** — where can the underlying mechanism become visible or fail?
10. **Alternative** — when would another approach be simpler or safer?
11. **Transfer** — can the learner recognize the same principle in a different tool or scenario?

Use this compact sequence in roadmaps:

`Fundamental -> Problem -> Minimal implementation -> Framework abstraction -> Benefit -> Failure mode -> Trade-off -> Transfer`

## Set stage expectations

### Beginner

- Explain the underlying problem and basic mental model in plain language.
- Predict the result of a small example.
- Build or trace a minimal version before or alongside the framework feature.
- Use the framework feature in a guided scenario and connect it back to the mechanism.

### Intermediate

- Select a standard abstraction for a familiar problem.
- Explain which fundamentals the abstraction relies on.
- Debug common abstraction leaks and compare at least one alternative.
- Modify the solution for a changed requirement without copying a tutorial.

### Advanced

- Reason from first principles across integrations, constraints, and unfamiliar failures.
- Evaluate performance, reliability, security, maintainability, and operational trade-offs.
- Replace or extend an abstraction when its assumptions no longer fit.
- Deliver an ambiguous end-to-end use case with evidence.

### Expert

- Design, adapt, or govern abstractions for complex contexts.
- Make defensible decisions under uncertainty and communicate their consequences.
- Teach the underlying mental models, review others' reasoning, and improve team standards.
- Sustain results across multiple cases; do not infer expertise from a single project.

## Develop sustainable learning and career habits

Adapt the screenshot themes as evidence-based habits rather than admission requirements:

1. **Clear fundamentals and first-principles reasoning** — ask what must remain true and derive behavior instead of memorizing recipes.
2. **Curiosity and constructive questioning** — question architecture and documentation with evidence. Do not require passion or identity-based claims as a gate.
3. **Sustainable deep work** — use protected, focused blocks, deliberate breaks, sleep, and review. Never prescribe 10-12 hour sessions as a quality signal.
4. **A useful peer group** — seek code review, practice partners, mentors, and collaborative feedback. Favor mutual growth over unhealthy competition.
5. **Evidence-based optimism and resilience** — respond to market facts, feedback, and setbacks with adjusted actions rather than denial or doom-scrolling.
6. **Ownership of a career search** — for career goals, use tailored outreach, visible work, referrals, feedback, and iteration. Do not recommend spam or deceptive automation.
7. **Ambitious projects at the right time** — after prerequisites, solve a meaningful problem with scope, constraints, acceptance criteria, and users or reviewers.

Treat items 1-4 as learning practices. Add items 5-7 only when the roadmap includes career outcomes or portfolio delivery.

## Use concept examples

### React: state and props

- **Fundamentals:** JavaScript values and functions, lexical scope, immutability, state transitions, render cycles, and one-way data flow.
- **Purpose of state:** retain component-owned data that can change and trigger a new render.
- **Why use state:** the rendered interface must stay synchronized with changing local data.
- **Purpose of props:** pass parent-owned inputs and callbacks into a child component.
- **Why use props:** they create an explicit, read-only input contract and preserve one-way data flow.
- **Minimal demonstration:** trace a parent value, a child input, a user event, a state transition, and the resulting render before adding more hooks.
- **Framework abstraction:** React supplies component rendering and state APIs so the learner does not manually synchronize every DOM change.
- **Abstraction leaks:** direct mutation, stale closures, unnecessary derived state, unstable identity, and misunderstood render timing.
- **Transfer:** relate the same ideas to inputs, ownership, state machines, event flow, and other UI frameworks.

### ORM: models and queries

- **Fundamentals:** tables, keys, relationships, joins, indexes, transactions, cardinality, and query cost.
- **Purpose:** map application objects and operations to persistent relational data.
- **Why use it:** reduce repetitive data-access code and make common operations safer and more expressive.
- **Minimal demonstration:** write and inspect a simple schema, join, and transaction before hiding them behind model methods.
- **Framework abstraction:** an ORM maps models and relationships to SQL and database operations.
- **Abstraction leaks:** N+1 queries, missing indexes, transaction boundaries, lazy loading, and generated SQL that does not fit the workload.

## Apply the fundamentals gate

Advance when the learner can reliably:

- explain the problem, purpose, invariant, and mechanism in plain language;
- predict behavior before running the example;
- build, trace, or reason through a minimal version;
- use the framework abstraction correctly in a relevant task;
- diagnose at least one failure where the abstraction leaks;
- compare an alternative and name the trade-off;
- transfer the principle to a changed scenario or another tool;
- produce an artifact or demonstration as evidence.

Do not require mastery of internals that do not affect the learner's target decisions, use cases, or failure modes.

## Avoid anti-patterns

- Teaching framework syntax without the problem and underlying mental model.
- Teaching theory for weeks without a visible use case or working artifact.
- Rebuilding an entire framework to prove understanding.
- Enforcing exactly 80/20 despite learner evidence or workplace urgency.
- Treating extreme working hours, passion, or competition as proof of ability.
- Copying AI or tutorial output without prediction, retrieval, debugging, or transfer.
- Starting an oversized portfolio project before its prerequisite gates are met.
- Equating course completion, time spent, or one successful demo with expertise.
