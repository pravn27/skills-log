# Cross-Agent Compatibility — 2026

Keep one portable `SKILL.md` core for Codex, Claude Code, Gemini CLI, and Grok. Isolate product-specific metadata and installation paths.

Verified against official documentation on **2026-09-24**.

## Portable core

Use this shared structure:

```text
version-control-workflows/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    └── ...
```

- Keep only `name` and `description` in shared YAML frontmatter.
- Keep instructions in portable Markdown and use relative reference links.
- Avoid vendor-only substitutions, tool grants, hooks, invocation flags, or subagent settings in the shared file.
- Keep OpenAI UI metadata in `agents/openai.yaml`; other agents may ignore it.
- Do not assume a GitHub, GitLab, or other connector exists. Use the tools available in the active environment.
- Preserve authorization boundaries regardless of a platform's tool permissions.

## Discovery and invocation

| Agent | Repository location | User location | Explicit use |
|---|---|---|---|
| OpenAI Codex | `.agents/skills/version-control-workflows/` | `~/.agents/skills/version-control-workflows/` | `$version-control-workflows` or the skills selector |
| Claude Code | `.claude/skills/version-control-workflows/` | `~/.claude/skills/version-control-workflows/` | `/version-control-workflows` |
| Gemini CLI | `.gemini/skills/version-control-workflows/` or `.agents/skills/...` | `~/.gemini/skills/...` or `~/.agents/skills/...` | Agent activation or `/skills` management |
| Grok | `.grok/skills/version-control-workflows/` and supported compatible locations | `~/.grok/skills/...` or `~/.agents/skills/...` | `/version-control-workflows` |

Prefer symlinks or a controlled installation process from this canonical repository rather than four manually maintained copies.

## Platform notes

### OpenAI Codex

- `name` and `description` drive discovery; keep the description specific.
- The portable directory plus optional `agents/openai.yaml` follows OpenAI's skill structure.
- Use `.agents/skills` for project or user installation.
- Automatic discovery remains enabled; sensitive Git actions still require task-level authorization.

Official source: [Build skills](https://learn.chatgpt.com/docs/build-skills).

### Claude Code

- Project skills live under `.claude/skills/<name>/SKILL.md`; personal skills use `~/.claude/skills`.
- Claude Code supports additional frontmatter and substitutions, but keep them out of this shared core.
- Claude's documentation recommends keeping the entrypoint focused and linking supporting resources.

Official source: [Extend Claude with skills](https://code.claude.com/docs/en/skills).

### Gemini CLI

- Gemini discovers workspace and user skills under `.gemini/skills` and the `.agents/skills` alias.
- Its guidance emphasizes precise discovery descriptions, progressive disclosure, and scoped security.
- Expect the host's activation and consent behavior; the shared skill must not attempt to bypass it.

Official sources: [Agent Skill best practices](https://geminicli.com/docs/cli/skills-best-practices/) and [Managing Agent Skills](https://geminicli.com/docs/cli/using-agent-skills/).

### Grok

- Grok discovers `.grok/skills`, configured paths, plugin skills, and supported compatible skill locations.
- Grok supports extra frontmatter and Claude Code compatibility, but the shared core does not depend on those extensions.
- Keep destructive Git operations subject to explicit confirmation even if Grok exposes the required command tools.

Official source: [Skills, Plugins & Marketplaces](https://docs.x.ai/build/features/skills-plugins-marketplaces).

## Compatibility checks

1. Validate the canonical `SKILL.md` and every relative link.
2. Confirm natural-language discovery and explicit invocation on each installed agent.
3. Test one explanation request, one read-only repository inspection, and one mutation request that must respect authorization.
4. Verify that provider-specific references load only when relevant.
5. Check that a dirty worktree is preserved.
6. Confirm destructive requests stop for exact-target confirmation.
7. Recheck official platform documentation and record a new verification date when distribution behavior changes.
