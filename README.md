# visualize

A Claude skill that turns a long, text-heavy response into a one-glance visual summary.

Type `/visualize` after Claude has given you a wall of text, and the skill rebuilds that answer as stage cards, stat tiles, charts, comparison tables, diagrams or checklists, so you can understand the outcome in about ten seconds and see what to do next.

## What it does

- Picks the last substantive assistant turn (or just the part you name, e.g. "just the comparison").
- Inventories what is in it: the verdict, steps completed, numbers, options compared, dependencies, open actions, risks.
- Maps each kind of content to the right visual form: stages become numbered cards, a few figures become stat tiles, 3+ comparable numbers become a bar chart, options vs criteria become a table, flows become box-and-arrow diagrams.
- Lays it out as headline, what happened, where things stand, what's next, and caveats, with 3-5 sections and no paragraphs.

## Rules it enforces

- **Fidelity:** every number, name, file and date must come from the source. Nothing is invented or re-rounded to fill a chart, and disagreeing figures are shown side by side.
- **No new advice:** it summarizes, it does not add recommendations.
- **No pointless charts:** a chart needs 3+ comparable numbers on a shared unit; otherwise the structure is the visual.
- **Short source guard:** if the last reply is under roughly 150 words with no structure, it says a visual won't help instead of forcing one.
- Works in light and dark mode and at phone width, with at most one sentence of text after rendering.

## Usage

Type `/visualize`, or ask Claude to "visualize what you just said."

## Install

This is a standard skill folder containing one `SKILL.md`.

- **Claude Code:** copy this folder to `~/.claude/skills/visualize/` (personal) or `.claude/skills/visualize/` in a project.
- **Claude apps:** zip the folder and upload it as a custom skill in your Claude settings.

The skill renders inline when a visual or widget tool is available, and otherwise falls back to building a self-contained HTML page.

## Files

- `SKILL.md`: the skill definition and instructions.
