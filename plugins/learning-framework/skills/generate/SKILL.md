---
name: generate
description: Builds a new layered "zoom lens" learning framework for a domain, as an overview doc plus one chapter doc for each pillar (Levels 0–2). Use when the user wants a learning map, study plan, or curriculum for a topic, or asks to learn a new domain from the top down.
argument-hint: "[domain] [goal] [background]"
---

# Generate a learning framework

The full prompt is in [generator.md](generator.md). It is the single source for the block template, the priority tags, the tree IDs, and the home-block rule.

## Workflow

1. Read [generator.md](generator.md).
2. Get the four learner inputs from the arguments or the conversation: domain, goal, background, and time (optional).
3. If the domain, the goal, or the background is missing, ask the user for it. Do not build anything until you have all three.
4. Follow every rule in generator.md, including its quality check.
5. Ask the user for an output folder. If the user gives none, use `./<domain-slug>/`.
6. Write each doc as its own file in that folder. Do not print the `=== FILE: ... ===` markers. The file name replaces them.
7. Reply with the file list and the 3–5 blocks that the overview recommends to expand first.

## Notes

- Where generator.md says "the Expander prompt", tell the user to run `/learning-framework:expand <block-id>`.
- If the user gives a source document (for example, a playbook or a spec), build the framework from its content and its goal.
