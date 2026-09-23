# Real-World Practice

Turn concepts into credible performance without exposing a learner or organization to avoidable risk.

## Use-case design

Write each use case as:

> As a [role], in [context], I need to [task] so that [outcome], while respecting [constraints]. Success is demonstrated by [observable criteria].

Include realistic inputs, stakeholders, constraints, failure modes, and a definition of done. Replace confidential data with safe samples.

## Project ladder

### 1. Reproduce

Follow a known-good example and verify the expected result.

### 2. Modify

Change one requirement, data shape, environment setting, or constraint. Predict and explain the effect.

### 3. Build from a brief

Deliver from acceptance criteria without a full recipe. Document decisions and tests.

### 4. Integrate

Connect multiple components or concepts. Handle interfaces, data flow, dependencies, and failure propagation.

### 5. Operate and troubleshoot

Observe behavior, diagnose a seeded incident, recover safely, and write a short post-incident analysis.

### 6. Optimize and defend

Improve performance, usability, reliability, security, maintainability, or cost. Compare options and defend trade-offs with evidence.

### 7. Lead or innovate

Define an ambiguous problem, set standards, coordinate review, create reusable guidance, and measure downstream impact.

## Project brief checklist

Every substantial project should specify:

- user or stakeholder;
- problem and desired outcome;
- in-scope and out-of-scope work;
- starting assets and environment;
- functional and quality acceptance criteria;
- security, privacy, ethics, accessibility, and compliance constraints;
- tests and evidence to capture;
- observability and troubleshooting expectations;
- time, cost, and tool limits;
- review method and reflection questions.

## Environment progression

Use this order unless the domain requires stricter controls:

1. simulation or paper exercise;
2. local sandbox;
3. disposable lab environment;
4. shared development environment;
5. staging with realistic controls;
6. supervised production change with approval, backup, rollback, and monitoring.

Never require a novice to use live credentials, personal data, irreversible commands, or an unreviewed production change.

## Evidence package

Ask the learner to retain:

- brief and acceptance criteria;
- working artifact or recorded demonstration;
- test results and failure cases;
- decision record and trade-offs;
- troubleshooting log;
- reviewer feedback and response;
- retrospective describing what would change next time.

The evidence should make independent judgment visible, not just the final output.
