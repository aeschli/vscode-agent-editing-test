---
name: CopilotEditingAgent
description: Exercises GitHub Copilot custom agent schema and body editing.
target: github-copilot
model-policy: preferred
reasoning-effort: medium
tools: [execute, read, edit, search, agent, web, todo, "github/*", "playwright/*"]
mcp-servers:
  local-example:
    command: node
    args: ["-e", "process.stdin.resume()"]
    tools: [search]
    env:
      MODE: test
    timeout: 10
    deferTools: auto
  remote-example:
    type: http
    url: https://example.com/mcp
    tools: [fetch]
    headers:
      Authorization: test-token
    deferTools: never
disable-model-invocation: true
user-invocable: false
github:
  toolsets: [repos, issues]
  permissions:
    issues: read
skills: [agent-editing-review]
deferred-tool-loading: true
strict-tools-list: false
include-custom-instructions: true
hooks:
  sessionStart:
    - type: command
      bash: echo copilot-agent-ready
---

Workspace: {{cwd}}

Home: {{homedir}}

Configuration: {{configDir}}

Search tool: {{grepToolName}}

File discovery tool: {{globToolName}}

Shell tool: {{shellToolName}}

Examples: {{shellCommandExamples}}

[This Markdown link](../../README.md) should remain valid.
