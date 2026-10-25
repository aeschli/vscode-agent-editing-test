# Custom agent editing test repository

This repository contains custom agent files and a workspace skill for:

- [Target-aware custom agent file editing](https://github.com/microsoft/vscode/issues/344131)
- [Live model, tool, and skill editing for custom agents](https://github.com/microsoft/vscode/issues/344130)

Use a current VS Code Insiders build with GitHub Copilot enabled. Open this repository as a folder and edit the files under [`.github/agents`](./.github/agents).

## Files

| File | Purpose |
| --- | --- |
| [`shared.agent.md`](./.github/agents/shared.agent.md) | Minimal agent without an explicit target |
| [`local.agent.md`](./.github/agents/local.agent.md) | Local/VS Code attributes, handoff, and body references |
| [`copilot.agent.md`](./.github/agents/copilot.agent.md) | GitHub Copilot schema, hooks, placeholders, and static tools |
| [`inventory.agent.md`](./.github/agents/inventory.agent.md) | Live model, tool, and skill inventory testing |
| [`validation-snippets.md`](./validation-snippets.md) | Valid and invalid snippets to paste during testing |
| [`SKILL.md`](./.github/skills/agent-editing-review/SKILL.md) | Distinctive workspace skill used by inventory tests |

## Suggested workflow

1. Start with the committed files and confirm they have no unexpected diagnostics.
2. Follow one linked test-plan item at a time.
3. Use [`validation-snippets.md`](./validation-snippets.md) for negative cases.
4. Use source control discard or `git restore .` between scenarios.

Do not run the schema-only Copilot agent. It contains illustrative MCP server definitions intended for editor validation, not for connecting to real services.
