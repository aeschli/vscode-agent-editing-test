---
name: LocalEditingAgent
description: Exercises Local and VS Code custom agent editing support.
target: vscode
argument-hint: Describe the local editing task
tools: [read, search]
agents: ["*"]
user-invocable: true
disable-model-invocation: false
advancedOptions:
  testScenario: agent-editing
handoffs:
  - label: Continue with the default agent
    agent: agent
    prompt: Continue this task using the default agent.
hooks:
  SessionStart:
    - type: command
      command: "echo local-agent-ready"
---

Use #tool:read and #tool:search to inspect this workspace.

When more general implementation help is needed, use the configured handoff.
