# CLAUDE.md

This repository is a Claude Code plugin marketplace. It has no build, no tests, and no lint. `claude plugin validate` is the only check.

## Layout

- `.claude-plugin/marketplace.json` lists every plugin. Its name is `chiajung-skills`.
- `plugins/<plugin-name>/` holds one plugin: `.claude-plugin/plugin.json`, a `README.md`, and `skills/<skill-name>/SKILL.md`.

## Rules

- If you add a plugin, add it to `marketplace.json` and to the table in `README.md`.
- If you change a plugin, increase its `version` in `plugin.json`. Users only get the update after a version change.
- Before you commit, run `claude plugin validate .` and `claude plugin validate plugins/<plugin-name>`.

## learning-framework

The two prompts `generator.md` and `expander.md` hold all framework rules. Each `SKILL.md` adds only the Claude Code steps: get the inputs, read and write the doc files, and reply. Keep the framework rules in the prompt files.

`generator.md` is the single source for the block template, the priority tags, the tree IDs, the home-block rule, and the doc names. `expander.md` refers to them. If you change one of these items in `generator.md`, examine `expander.md` for the same item.

A copy of the two prompts also exists in the learning-framework repository. The two copies can drift apart.
