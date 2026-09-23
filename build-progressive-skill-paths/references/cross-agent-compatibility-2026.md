# Cross-Agent Skill Compatibility — 2026

Keep one vendor-neutral learning workflow and use thin discovery adapters for Claude Code, OpenAI Codex, Gemini CLI, and Grok. Verified against official documentation on **2026-09-23**.

## Contents

- [Portable core](#portable-core)
- [Platform matrix](#platform-matrix)
- [Recommended repository pattern](#recommended-repository-pattern)
- [Platform notes](#platform-notes)
- [Portability checklist](#portability-checklist)

## Portable core

Use this lowest-common-denominator structure:

```text
skill-name/
├── SKILL.md
├── references/
├── scripts/
└── assets/
```

For a shared `SKILL.md`:

- use only `name` and `description` in YAML frontmatter;
- write portable Markdown instructions in imperative form;
- reference bundled files with relative paths;
- keep scripts explicit, cross-platform where practical, and free of secrets;
- avoid vendor-only prompt interpolation, shell injection, tool grants, hooks, subagent fields, or execution flags in the portable core;
- isolate vendor metadata in sidecar files or adapters.

This skill follows that portable subset. Its `agents/openai.yaml` is an OpenAI-specific sidecar; other agents can ignore it.

## Platform matrix

| Platform | Project discovery | User discovery | Direct invocation | Notes |
|---|---|---|---|---|
| OpenAI Codex | `.agents/skills/<name>/` | `~/.agents/skills/<name>/` | `$name` or `/skills` selection | Uses the open Agent Skills standard; optional `agents/openai.yaml` configures OpenAI UI metadata. |
| Claude Code | `.claude/skills/<name>/` | `~/.claude/skills/<name>/` | `/name` | Uses the Agent Skills standard and supports additional Claude-only frontmatter and body features. |
| Gemini CLI | `.gemini/skills/<name>/` or `.agents/skills/<name>/` | `~/.gemini/skills/<name>/` or `~/.agents/skills/<name>/` | Agent activation; manage with `/skills` | Supports the shared `.agents/skills` alias and asks for activation consent. |
| Grok Build | `.grok/skills/<name>/`; also reads Claude Code project skills | `~/.grok/skills/<name>/` and `~/.agents/skills/<name>/` | `/name` | Reads Grok-native, Agent Skills, and Claude Code-compatible locations; supports additional Grok fields. |

## Recommended repository pattern

Keep the canonical skill once, then link it into platform discovery folders:

```text
skills-log/
└── build-progressive-skill-paths/     # canonical source

consumer-repo/
├── .agents/skills/build-progressive-skill-paths -> canonical source
├── .claude/skills/build-progressive-skill-paths -> canonical source
└── .grok/skills/build-progressive-skill-paths -> canonical source
```

Use `.agents/skills` for Codex and Gemini. Use `.claude/skills` for Claude Code; Grok can read it too. Add `.grok/skills` only when an explicit Grok-native path is preferable. If symlinks are unsuitable for a team or operating system, copy during installation and define one synchronization process.

Do not maintain four independent copies by hand. They will drift.

## Platform notes

### OpenAI Codex

- Treat `name` and `description` as the discovery contract.
- Keep the main workflow in `SKILL.md` and detailed material in references.
- Use `agents/openai.yaml` only for OpenAI UI metadata, invocation policy, or MCP dependency declarations.
- Use plugins when distributing multiple skills or bundling connectors.
- Official source: [Build skills](https://learn.chatgpt.com/docs/build-skills)

### Claude Code

- Keep shared skills within the open-standard frontmatter subset.
- Do not use Claude-only features such as dynamic `!` command injection, invocation-control fields, hooks, or subagent execution when the same skill must run unchanged elsewhere.
- Add a Claude-specific wrapper only when those capabilities are essential.
- Official source: [Extend Claude with skills](https://code.claude.com/docs/en/skills)

### Gemini CLI

- Use `.agents/skills` when sharing the same installed directory with Codex, or `.gemini/skills` for a Gemini-specific installation.
- Reload with `/skills reload`; use `gemini skills link` for local development.
- Expect an activation-consent step before a discovered skill gains access to its resources.
- Official sources: [Creating Agent Skills](https://geminicli.com/docs/cli/creating-skills/) and [Managing Agent Skills](https://geminicli.com/docs/cli/using-agent-skills/)

### Grok

- Distinguish Grok Build's filesystem `SKILL.md` skills from Grok Bot or web private skills saved through the product UI.
- Grok Build can discover `.grok/skills`, user-level `.agents/skills`, and Claude Code-compatible skills.
- Keep Grok-only fields such as `when-to-use`, `paths`, or invocation flags out of the shared frontmatter.
- Official sources: [Grok Build skills, plugins, and marketplaces](https://docs.x.ai/build/features/skills-plugins-marketplaces) and [Grok Bot skills and routines](https://docs.x.ai/grok-bot/skills-routines-and-automations)

## Portability checklist

Before claiming compatibility:

1. Validate the canonical skill with the strictest target validator.
2. Confirm every referenced file resolves from the skill directory.
3. Test explicit invocation on each installed platform.
4. Test one natural-language prompt that should activate the skill.
5. Test one prompt that should not activate it.
6. Review scripts, permissions, network access, secrets, and destructive actions separately on each platform.
7. Verify platform paths and commands against official docs on the test date.
8. Record unsupported vendor-only behavior instead of silently degrading it.
