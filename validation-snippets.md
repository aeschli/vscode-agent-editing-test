# Validation snippets

Paste these snippets into the matching agent file, observe completions, hovers, and diagnostics, then discard the edit.

## Target changes

```yaml
target: vscode
```

```yaml
target: github-copilot
```

## Local-only attributes

```yaml
argument-hint: Describe the task
agents: ["*"]
advancedOptions:
  testScenario: agent-editing
handoffs:
  - label: Continue
    agent: agent
    prompt: Continue with the default agent.
```

## Copilot-only attributes

```yaml
model-policy: required
skills: [agent-editing-review]
deferred-tool-loading: true
strict-tools-list: false
include-custom-instructions: true
github:
  toolsets: [repos, issues]
  permissions:
    issues: write
```

## Model inventory

Use completion to replace the placeholders:

```yaml
model: [unavailable-model, replace-with-an-available-model]
reasoning-effort: replace-with-a-suggested-value
```

## Tool inventory

```yaml
tools:
  - execute
  - read
  - edit
  - search
  - agent
  - web
  - todo
  - github/*
  - playwright/*
  - browser/clickElement
  - notebook/createJupyterNotebook
  - vscode/createAndRunTask
  - invented/tool
```

## Skill inventory

```yaml
skills:
  - agent-editing-review
  - invented-skill
```

Temporarily rename [`.github/skills/agent-editing-review`](./.github/skills/agent-editing-review), reload skill discovery if necessary, and verify that completion, hover, and diagnostics refresh. Restore the directory afterward.

## Valid agent-scoped MCP servers

```yaml
mcp-servers:
  local:
    command: node
    args: [server.js]
    tools: [search]
    env:
      MODE: test
    timeout: 10
    deferTools: auto
  remote:
    type: http
    url: https://example.com/mcp
    tools: [fetch]
    headers:
      Authorization: test-token
    deferTools: never
```

## Invalid nested values

```yaml
mcp-servers:
  local:
    command: [node]
    args: server.js
    timeout: 0
  remote:
    type: http
    tools: [fetch]
```

```yaml
hooks:
  preToolUse:
    - matcher: "["
      type: command
      bash: echo invalid
      timeout: 0
```

```yaml
github:
  toolsets: repos
  permissions:
    issues: [write]
```

## Body placeholders and references

```markdown
{{cwd}}
{{homedir}}
{{configDir}}
{{grepToolName}}
{{globToolName}}
{{shellToolName}}
{{shellCommandExamples}}
{{unknownPlaceholder}}

#tool:read
#file:README.md
[README](./README.md)
```
