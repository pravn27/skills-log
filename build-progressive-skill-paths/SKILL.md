---
name: build-progressive-skill-paths
description: Design clear, personalized, hands-on learning journeys for engineering, IT, digital, or other professional skills from beginner through intermediate, advanced, and expert practice. Explain every concept through What it is, Purpose, Why it is used, How it works, and When to use it. Use when an AI agent must create or improve a roadmap, curriculum, study plan, concept-by-concept tutorial sequence, lab plan, project ladder, reskilling path, or real-world implementation plan; select current high-quality resources; diagnose a learner's level; define measurable stage gates; or turn theory into job-relevant practice and portfolio evidence.
---

# Build Progressive Skill Paths

Create one coherent path that moves a learner from understanding to independent, real-world performance. Optimize for clarity, low friction, useful practice, feedback, and proof of capability.

## Core principles

- Start from the learner's desired outcome and real use case, not a generic syllabus.
- Maintain one recommended path. Put alternatives in optional branches.
- Teach each concept just before it is needed in practice.
- Start every concept with `What -> Purpose -> Why -> How -> When`, then demonstrate and practice it.
- Move through `explain -> observe -> reproduce -> modify -> solve -> apply -> teach or defend`.
- Increase task complexity and learner autonomy together.
- Prefer short feedback loops, visible outputs, and realistic constraints.
- Use official documentation and standards as anchors; use courses and tutorials as delivery aids.
- Treat expert performance as sustained judgment in ambiguous situations, not course completion.
- Keep novices in a sandbox. Require review, rollback, observability, and approval before production work.

## Workflow

### 1. Frame the destination

Capture or infer:

- target skill and intended role or outcome;
- one to three real use cases;
- current experience and prerequisites;
- available time, deadline, tools, budget, and accessibility needs;
- desired evidence: interview readiness, certification, project, workplace result, or teaching ability.

Ask only questions that materially change the path. If information is missing, state reasonable assumptions and provide an editable first version.

Rewrite the goal as an observable capability: `Given [context], perform [task] to [quality bar] under [constraints], producing [evidence].`

### 2. Diagnose before sequencing

Use a small diagnostic instead of self-rating alone:

1. Ask for a plain-language explanation.
2. Ask the learner to predict an outcome.
3. Give one representative task.
4. Add one changed condition or troubleshooting case.
5. Inspect existing work when available.

Place the learner at the earliest stage whose exit evidence is not yet reliable. Do not force review of already demonstrated fundamentals.

### 3. Build the dependency map

Organize concepts into:

1. prerequisites;
2. core mental models;
3. essential tools and operations;
4. integration and troubleshooting;
5. quality, security, reliability, ethics, and trade-offs;
6. specialization and frontier topics.

Mark each concept as `must know`, `useful next`, or `specialization`. Remove topics that do not support the target use case.

### 4. Align with current practice

For IT, engineering, digital, software, data, AI, or cybersecurity paths, read [industry-alignment-2026.md](references/industry-alignment-2026.md). Select only applicable frameworks. Never imply that every framework is a formal standard or that the ten-item set is an objective ranking.

When current alignment matters, verify versions and links against official publisher pages. Record an `as of` date. Prefer current stable practices; label preview, experimental, deprecated, or vendor-specific material.

When creating, installing, or sharing the learning skill across Claude Code, OpenAI Codex, Gemini CLI, or Grok, read [cross-agent-compatibility-2026.md](references/cross-agent-compatibility-2026.md). Keep the core `SKILL.md` vendor-neutral and isolate platform-only metadata or behavior.

### 5. Design the four-stage journey

Always read [mastery-levels.md](references/mastery-levels.md). Define Beginner, Intermediate, Advanced, and Expert using observable work, autonomy, task complexity, decision quality, and evidence. Give every stage:

- outcomes and prerequisites;
- ordered concept modules;
- hands-on labs and a stage project;
- expected failure modes and debugging practice;
- an exit gate and tangible evidence;
- a realistic effort range, expressed as a range rather than a promise.

Use `Intermediate` as the standard label; mention `Medium` once when mirroring user wording.

### 6. Build each concept module

Read [concept-learning-loop.md](references/concept-learning-loop.md). For each concept, provide:

1. **What is it?** — define it in plain language.
2. **Purpose** — state the job it exists to perform.
3. **Why do we use it?** — name the problem, benefit, and trade-off.
4. **How does it work?** — explain the mechanism, inputs, outputs, and data or control flow.
5. **When should or should not it be used?** — give a decision boundary and alternatives.
6. **Why now?** — connect it to the current stage and prerequisite.
7. **Mental model** — add an analogy or diagram when it improves understanding.
8. **Worked example** — show a correct example with reasoning.
9. **Guided lab** — give exact steps and expected output.
10. **Independent challenge** — vary one meaningful condition.
11. **Real-world transfer** — use it inside the target scenario.
12. **Debugging case** — identify and fix a realistic failure.
13. **Retrieval check** — explain or perform without the guide.
14. **Evidence and gate** — save an artifact and apply observable pass criteria.

Keep lessons small enough to finish in one focused session. End every session with a working state and the next concrete action.

### 7. Select a focused resource stack

Read [resource-selection.md](references/resource-selection.md). Prefer a small stack for each stage:

- one authoritative reference;
- one structured explanation;
- one hands-on lab environment;
- one project or case-study source;
- one feedback channel when useful.

Do not dump long link lists. Explain why each resource was selected, what to use from it, its level, cost, freshness, and any prerequisite.

### 8. Add real-world execution

Read [real-world-practice.md](references/real-world-practice.md). Build a project ladder from safe reproduction to ambiguous, end-to-end delivery. Include setup, acceptance criteria, constraints, tests, observability, security, documentation, rollback, and retrospective.

Use simulations, local environments, sample data, or staging before live systems. Never equate a tutorial clone with independent capability.

### 9. Assess and adapt

Read [assessment-and-evidence.md](references/assessment-and-evidence.md). Assess knowledge, execution, transfer, and autonomy. Use artifacts and demonstrations, not time spent or content consumed.

If a learner misses a gate:

1. identify the smallest missing prerequisite;
2. provide one clearer example;
3. assign one narrower practice task;
4. retest with a different case;
5. update the path without restarting everything.

### 10. Present the journey

Always read [roadmap-output-template.md](references/roadmap-output-template.md). Adapt its detail to the request, but preserve the visible path, concept modules, project ladder, assessments, evidence, and immediate next action.

## Adaptation rules

- **Complete beginner:** define terms, minimize setup, use worked examples, and give fast visible wins.
- **Experienced learner changing domains:** compress shared fundamentals and emphasize different assumptions, tools, and failure modes.
- **Workplace urgency:** teach the immediate use case first, then backfill reusable foundations.
- **Certification goal:** map objectives to practical tasks; do not turn the plan into exam memorization only.
- **Limited time:** reduce breadth before reducing practice or feedback.
- **Low budget:** prefer official documentation, open curricula, local labs, and open-source projects.
- **Accessibility need:** offer text, visual, audio, keyboard-first, low-bandwidth, or paced alternatives as appropriate.
- **Fast-changing topic:** teach durable mental models first and isolate version-specific details.

## Quality gate

Before delivering a path, verify that it:

- has a clear destination and stated assumptions;
- follows dependencies rather than popularity;
- explains every concept with What, Purpose, Why, How, and When before practice;
- contains more doing than passive consumption after initial orientation;
- pairs every important concept with practice and evidence;
- includes debugging, trade-offs, safety, and realistic constraints;
- defines distinct stage exits from Beginner through Expert;
- uses current, authoritative sources with an `as of` date when recency matters;
- gives a first task the learner can start now;
- avoids unsupported claims that a fixed duration guarantees expertise.
