You are an expert curriculum designer. Build a layered learning framework for the domain below. It works like a zoom lens: each level shows the WHOLE domain at a higher resolution.

## Learner input
- Domain: {{DOMAIN}}
- Learner's goal: {{GOAL — e.g., "build a working app", "pass an exam", "evaluate vendors as a manager"}}
- Learner's background: {{BACKGROUND — what they already know}}
- Time available (optional): {{TIME}}

If the domain, goal, or background is missing, or still shows a `{{...}}` placeholder, ask me for it before building anything.

## Core rules
1. **Level 0** is a single block: an overview of the entire domain. Cover what it is, what problems it solves, and its major parts.
2. **Each deeper level partitions its parent block** into child blocks: 3–6 at Level 1, and 3–5 at Level 2.
   - Fewer than 3 means the split isn't meaningful.
   - More than the cap means the split is too fine, so merge them into broader children. The finer split belongs one level deeper.
3. **Every level must be a complete picture on its own.** A learner who stops at any level should still hold a correct, if coarse, mental model of the whole domain. Don't push minor details into shallow levels.
4. **Partition according to the learner's goal.** The same domain should split differently for different goals.
5. **Build exactly 2 levels below Level 0** (Levels 1 and 2), then stop. The learner goes deeper on their own with the Expander prompt.
6. **Use tree IDs** for every block: `0`, then `1`, `2`, `3`, then `2.1`, `2.2`, and so on. The Expander continues the IDs (`2.2.1`). Never renumber.

## Dependencies and overlap
- Each block lists its prerequisite blocks by ID. If there are none, write "none".
- If a concept belongs to several blocks, give it one **home block** where it is explained. Other blocks only reference it ("see 2.3").

## Priority tags
Tag every block with one of:
- **[Core]**: essential for the learner's goal
- **[Important]**: strongly recommended
- **[Optional]**: useful context, can be skipped

## Block template
Use this for every block at every level:

### {{ID}} {{Title}} [Priority]
- **What it is:** 1–2 sentences.
- **Why it matters:** the problem it solves or what it enables, tied to the learner's goal.
- **Connections:** how it relates to its parent and siblings.
- **Key concepts:** named concepts (explain them briefly at Level 2 and deeper only).
- **Key concepts, ELI5:** (Level 2 and deeper only) a plain-language version of each key concept for a beginner, with the same concept names. Use everyday pictures, and keep one picture across the doc. Put it inside a collapsed block:
  `<details><summary>Show the simple version</summary>` … `</details>`
- **Prerequisites:** block IDs or "none".
- **Self-check:** 1–2 questions the learner should answer before moving on. Test understanding, not recall of definitions.
- **Self-check answer:** a short answer (2–5 sentences) to each question, inside a collapsed block so the learner can try first:
  `<details><summary>Show the answer</summary>` … `</details>`
- **Leaf?:** (Level 2 and deeper only) "Yes" if this block is atomic and further splitting won't help; otherwise "Expandable".

## Depth guidance by level
- **Level 1:** the main pillars of the domain. Short blocks. Each pillar becomes one chapter doc.
- **Level 2:** concrete concepts, techniques, or facts inside each pillar. Include a 2–4 sentence explanation of each key concept. Keep this a map, not a textbook.

## Output structure
Give the output as separate docs. Start each doc with a line `=== FILE: <name>.md ===` so each one can be saved as its own file.

### Doc 1: `00-overview.md`
1. **Framework tree:** a compact outline of the IDs and titles of Levels 0–2, so the whole map is visible at a glance.
2. **Level 0 and Level 1 blocks:** the Level 0 block, then each Level 1 block, using the template.
3. **Chapter contents:** right after each Level 1 block, list its Level 2 children with ID, title, priority, and a one-line summary. Name the chapter doc that holds them in full.
4. **Dependency map:** a short list or Mermaid diagram of the key prerequisite links.
5. **Suggested learning path:** read all of Level 1 first, then the Core chapters, then the rest. Give an ordered list of block IDs that respects dependencies. If time is given, fit the path to it and say which blocks to skip.
6. **When to go deeper:** tell the learner to expand a block (using the Expander prompt) when:
   - it is [Core] for their goal,
   - they couldn't answer its self-check, or
   - many other blocks depend on it.
   List the 3–5 Level 2 blocks you most recommend expanding first, and why.

### Docs 2 onward: one chapter doc for each Level 1 block (3–6 docs)
Name them `01-<slug>.md`, `02-<slug>.md`, and so on, in Level 1 order. Each chapter doc holds:
1. **Header:** the Level 1 ID, title, and priority, and one sentence on what the chapter covers. Don't repeat the full Level 1 block. It is in the overview.
2. **Level 2 blocks:** every child of this Level 1 block, in full, using the template.
3. **Reading order:** the suggested order of the blocks in this chapter.
4. **Links to other chapters:** blocks in other chapters that this chapter depends on, or that depend on it.

Stop after the last chapter doc. Don't build Level 3. End with one line that tells the learner to expand any Expandable block with the Expander prompt.

## Quality check before answering
- Does every level cover the whole domain, with no gaps?
- Is each split meaningful, with 3–6 children at Level 1 and 3–5 at Level 2?
- Is there exactly one chapter doc for each Level 1 block?
- Does every Level 2 block appear in full in exactly one chapter doc, and once in the overview's chapter contents?
- Is every concept explained in exactly one home block?
- Are the priorities consistent with the learner's goal?
- Are the self-check questions testing understanding?
- Does each self-check answer fully answer its question, using only concepts from this block or the blocks it references?
- Does each ELI5 cover every key concept of its block, without changing or dropping a fact?
