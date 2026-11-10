# claude-skills

This repository is a Claude Code plugin marketplace. Each plugin holds one or more skills.

## Install

1. Add the marketplace in Claude Code:

   ```
   /plugin marketplace add chiajung-wang/claude-skills
   ```

2. Install a plugin:

   ```
   /plugin install <plugin-name>@chiajung-skills
   ```

To get updates later, run `/plugin marketplace update chiajung-skills`.

## Plugins

| Plugin | Skills | Purpose |
|---|---|---|
| [learning-framework](plugins/learning-framework) | `generate`, `expand` | Build a layered "zoom lens" learning map for any domain, then go deeper one block at a time. |

## Add a new plugin

1. Make a folder `plugins/<plugin-name>/`.
2. Add `plugins/<plugin-name>/.claude-plugin/plugin.json` with a name, a version, and a description.
3. Add one folder for each skill: `plugins/<plugin-name>/skills/<skill-name>/SKILL.md`.
4. Add an entry for the plugin to `.claude-plugin/marketplace.json`.
5. Add a row to the table above.
6. Run `claude plugin validate .` and `claude plugin validate plugins/<plugin-name>`.

To add a skill to an existing plugin, do step 3 only. Then increase the plugin version in its `plugin.json`.

## License

MIT. See [LICENSE](LICENSE).
