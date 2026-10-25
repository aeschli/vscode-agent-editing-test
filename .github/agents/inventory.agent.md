---
name: InventoryEditingAgent
description: Exercises live GitHub Copilot model, tool, and skill inventories.
target: github-copilot
model-policy: preferred
tools: [execute, read, edit, search, agent, web, todo, "github/*", "playwright/*"]
skills: [agent-editing-review]
user-invocable: true
disable-model-invocation: false
---

Use the configured workspace skill to review changes in this repository.

During testing, add `model`, `reasoning-effort`, and provider-specific tool entries using completion suggestions rather than committing machine-specific catalogue values.
