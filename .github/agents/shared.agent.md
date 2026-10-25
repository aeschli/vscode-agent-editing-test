---
name: SharedEditingAgent
description: Exercises attributes shared by custom agent formats without declaring a target.
tools: [read, search]
user-invocable: true
disable-model-invocation: false
hooks:
  SessionStart:
    - type: command
      command: "echo shared-agent-ready"
---

Review the current workspace and explain the next useful change.
