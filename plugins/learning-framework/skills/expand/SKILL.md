---
name: expand
description: Splits one block of an existing "zoom lens" learning framework into 3–7 child blocks, one level deeper. Use when the user wants to go deeper on a block ID such as 2.3 or 2.3.1, failed a block's self-check, or asks to expand part of a learning map made by the generate skill.
argument-hint: "<block-id> [why: core | failed self-check | curious]"
---

# Expand one block

The full prompt is in [expander.md](expander.md).

## Workflow

1. Read [expander.md](expander.md).
2. Get the block ID from the arguments. If there is no block ID, ask for it.
3. Find the framework folder. Look for `00-overview.md` in the current folder and its subfolders. If you find more than one, ask the user which one to use.
4. Read `00-overview.md` and the chapter doc that holds the target block. These two docs are the "Existing framework" input.
5. Get the goal from the overview. Get the reason for the expansion from the arguments. If there is no reason, ask the user.
6. Follow every rule in expander.md.
7. Insert the new child blocks into the chapter doc, directly after the parent block. Do not change any existing ID.
8. In the parent block, change "Leaf?: Expandable" to point to the new children.
9. Add the new IDs and titles to the framework tree in `00-overview.md`.
10. Reply with output items 1, 3, 4, and 5 of expander.md. Do not repeat the full child blocks in chat.
