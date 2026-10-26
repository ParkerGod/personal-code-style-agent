---
name: personal-coding-style
description: Follow a user's established coding preferences in a project, or learn evidence-backed personal preferences from the current workspace when asked.
---

# Personal coding style

Use the current workspace directly. This skill needs only the agent's normal file-reading and editing abilities; it has no server, web UI, MCP, or CLI dependency.

## When changing code

1. Read the repository's applicable agent instructions and relevant formatter, linter, and language configuration.
2. Inspect nearby code and tests that solve a similar problem. Treat those examples and project checks as the primary guide for this repository.
3. If available, read the user's personal profile at `~/.personal-coding-style/profile.md` (Windows: `%USERPROFILE%\.personal-coding-style\profile.md`). Apply it only where it fits the project. Repository instructions and checks take precedence over personal preferences.
4. Keep changes consistent with the surrounding code. Do not reformat unrelated files just to apply a personal preference.
5. In the final summary, mention a personal preference only if it materially affected the change, and explain any meaningful conflict with project conventions.

## When asked to learn preferences from this project

Analyze the already-open workspace; do not ask the user to paste code or type a repository path. Ask which workspace only if the active workspace is genuinely ambiguous or inaccessible.

1. Read project instructions, formatter/linter settings, language configuration, and tests first. Record explicit project requirements separately from personal preferences.
2. Inspect representative human-written code across relevant areas. Exclude generated, vendored, minified, and dependency files. Look for repeated patterns and counterexamples.
3. Propose a short set of actionable personal preferences supported by examples from independent files. For each, provide a brief explanation and workspace-relative evidence paths. Do not infer a personal preference from a single occurrence or from mandatory project configuration.
4. Present the candidates in chat and wait for the user's decision. Do not save inferred rules automatically.
5. After explicit acceptance, add only accepted rules to `~/.personal-coding-style/profile.md` (Windows: `%USERPROFILE%\.personal-coding-style\profile.md`). Preserve existing content. If the agent cannot write to that location, return a ready-to-save Markdown section instead. Never copy source code or absolute repository paths into the global profile.

## When asked to apply learned preferences to a project

Create or update the project's native instruction file (for Codex, root `AGENTS.md`) only when the user asks to make the preferences persistent in that project. Include concise rules that are useful to future coding tasks, preserve unrelated existing instructions, and keep project requirements separate from personal preferences. Do not overwrite an existing instruction file.

## Boundaries

- Learning from a repository produces proposals; it does not itself confirm or save preferences.
- Never change the user's global profile or project instruction files without an explicit request or acceptance.
- Prefer a few clear, reusable rules over exhaustive inventories or rigid templates.
