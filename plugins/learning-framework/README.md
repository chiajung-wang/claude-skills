# learning-framework

This plugin builds a layered learning map for any domain. The map works like a zoom lens: each level shows the whole domain, at a higher resolution than the level above it.

## Install

```
/plugin install learning-framework --marketplace chiajung-wang/claude-skills
```

## Skills

- `/learning-framework:generate <domain>` builds Levels 0–2. It writes `00-overview.md` and one chapter doc for each pillar.
- `/learning-framework:expand <block-id>` splits one block into 3–7 child blocks, one level deeper. It updates the docs in place.

## How the map works

- **Level 0** is one block: an overview of the whole domain.
- **Level 1** splits the domain into 3–6 pillars. Each pillar gets one chapter doc.
- **Level 2** splits each pillar into 3–5 blocks.
- Every level is a complete picture. If you stop at any level, you still have a correct, coarse model of the whole domain.
- The split follows your goal. The same domain splits differently for "pass an exam" and for "build a working app".

Each block has a priority tag (`[Core]`, `[Important]`, or `[Optional]`), a self-check, and a collapsed answer. From Level 2 down, each block also has a collapsed ELI5 version of its key concepts.

## Use without Claude Code

The prompts are plain text. Paste `skills/generate/generator.md` or `skills/expand/expander.md` into any LLM chat, and fill in the `{{...}}` placeholders.
