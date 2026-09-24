# Skills Log

A collection of reusable AI-agent skills for structured upskilling, career development, hands-on practice, and real-world execution.

## Skill index

| Skill no. | Skill | Purpose | Learning levels | Status |
|---:|---|---|---|---|
| 1 | [build-progressive-skill-paths](build-progressive-skill-paths/) | Build a fundamentals-first, Why-and-How upskilling journey with concept practice, projects, assessments, and measurable progression. | Beginner → Intermediate → Advanced → Expert | Available |
| 2 | `interview-prep` | Prepare concept knowledge, practical exercises, interview questions, mock interviews, and improvement feedback for a target role. | Beginner → Intermediate → Advanced → Expert | Planned |

Add each new skill as the next numbered row. Link the skill name only after its directory and `SKILL.md` have been added.

## Learning-level index

| Level | Primary learning focus | Expected execution | Evidence of readiness |
|---|---|---|---|
| Beginner | Vocabulary, prerequisites, fundamentals, purpose, and basic mental models | Complete guided examples and small labs safely | Explain What, Purpose, Why, How, and When; produce a working basic artifact |
| Intermediate | Common patterns, framework application, integration, and debugging | Complete familiar tasks independently and modify solutions for changed requirements | Deliver a small real-world project and diagnose common failures |
| Advanced | Architecture, trade-offs, quality, security, performance, and unfamiliar problems | Design and deliver ambiguous end-to-end solutions | Defend decisions, troubleshoot abstraction leaks, and provide production-quality evidence |
| Expert | Strategy, system-level judgment, standards, mentoring, and innovation | Lead complex work and improve how others execute it | Demonstrate sustained results across cases, teach the concepts, and establish reusable practices |

## Skill 1: Build Progressive Skill Paths

Use [`build-progressive-skill-paths`](build-progressive-skill-paths/) to create a smooth learning journey for any engineering, IT, digital, or professional skill.

It provides:

- a fundamentals-first approach with an adaptive 80/20 learning heuristic;
- concept-by-concept explanations using `What → Purpose → Why → How → When`;
- a bridge from underlying principles to framework abstractions;
- guided practice, independent challenges, debugging, and real-world transfer;
- Beginner, Intermediate, Advanced, and Expert stage gates;
- project ladders, assessments, evidence, and progress tracking;
- alignment with selected 2026 industry frameworks and resources;
- portable guidance for OpenAI Codex, Claude Code, Gemini CLI, and Grok.

## Repository structure

Each implemented skill should follow this modular structure:

```text
skills-log/
├── README.md
└── skill-name/
    ├── SKILL.md
    ├── agents/       # Optional platform metadata
    ├── references/   # Detailed modular guidance
    ├── scripts/      # Optional reusable automation
    └── assets/       # Optional templates or media
```

## Adding the next skill

1. Create a lowercase, hyphenated skill directory.
2. Add a focused `SKILL.md` with clear activation criteria and instructions.
3. Place detailed reusable material in `references/`.
4. Validate the skill and its local links.
5. Add the next sequential number to the Skill index in this README.
6. Mark the row `Available` only after the skill is usable and validated.
