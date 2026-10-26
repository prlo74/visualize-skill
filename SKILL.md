---
name: "visualize"
description: "Turn the most recent long or text-heavy response into an inline visual summary (cards, stat tiles, charts, diagrams, checklists). Use when the user types /visualize or asks to visualize what was just said or done."
---

# Visualize the last response

Goal: someone who skipped the text understands the outcome in 10 seconds and knows what to do next.

## 1. Pick the source
- Default: the last substantive assistant turn in this conversation (and the work it reports on). If the user names a part ("just the comparison"), use only that.
- If there is nothing substantive before /visualize, say so in one line and ask what to visualize. Never visualize the conversation about visualizing.
- If the last turn is short (under ~150 words) with no real structure, say a visual won't add anything and offer to visualize an earlier, longer turn instead.

## 2. Inventory before drawing
Privately list what the source contains:
- Outcome / verdict (the one-sentence answer)
- Steps or phases completed
- Numbers (counts, money, %, dates, durations)
- Entities being compared (options, tools, people)
- Relationships (A feeds B, depends on, causes)
- Actions still open, and who owns each
- Risks, caveats, open questions
Drop filler, repeated hedging, and process narration.

## 3. Map content shape to visual form
| Content shape | Visual |
|---|---|
| Work completed in stages | Numbered stage cards, left to right, one-line outcome each |
| 1-4 standalone figures | Stat tiles (big number, short label) |
| 3+ numbers on a shared unit across categories | Bar chart |
| Values over time | Line chart |
| Parts of a whole | Single stacked bar (not a pie) |
| Options vs criteria | Comparison table, winner per row marked |
| System, pipeline, data flow | Box-and-arrow diagram |
| Branching logic / recommendation conditions | Decision tree |
| Dated events | Horizontal timeline |
| To-dos | Checklist rows with owner tags (You / Claude / Optional) |
| Warnings that change a decision | Callout box |

Rule: charts only when there are 3+ comparable numbers from the source on a shared unit. Two numbers are stat tiles. No numbers means no chart: the structure is the visual.

## 4. Layout
Top to bottom, in the order the reader needs it:
1. Headline: one sentence with the bottom line (result, verdict or recommendation).
2. What happened / what it is (stage cards, flow or diagram).
3. Where things stand (stat tiles, chart or table).
4. What's next (action rows with owner tags).
5. Caveats, only if they change a decision.
Limits: 3-5 sections. Card titles 6 words max, subtitles 15 words max, 4 items per row max. No paragraphs anywhere.

## 5. Fidelity rules
- Every number, name, file and date must come from the source. Never invent, re-round, or add data to fill out a chart.
- If source figures disagree (e.g. 101 items exported vs 99 notes built), show both and mark the gap instead of smoothing it over.
- Keep the source's uncertainty: if it said likely, estimate or unverified, label it that way.
- Don't add new recommendations. The visual summarizes; it doesn't advise.

## 6. Build
- Render inline with the visual/widget tool when available, loading its design guidance first (e.g. diagram, chart, interactive modules). Otherwise build one self-contained HTML page and publish or send it.
- Theme with CSS variables; must work in light and dark mode and at phone width.
- One accent color per meaning (e.g. owner tags). Don't color anything that carries no meaning.
- Small line icons per stage are fine. No emoji, no decorative graphics.
- For actions Claude could take, add a button that sends a follow-up prompt to chat (e.g. "Tell Claude", "How") when the tool supports sending prompts.

## 7. After rendering
At most one sentence of text: the one thing the visual can't show, or nothing. Never recap what the visual already says.

## 8. Self-check before sending
- Could someone act on this without reading the original?
- Does every chart have 3+ data points taken from the source?
- Is any number not in the source? Remove it.
- Is any action item or warning from the source missing? Add it.

## Reference pattern
A setup recap that worked well: "What we did" = 4 numbered stage cards (Research, Export, Build, Automate) each with a one-line outcome; "What's in it now" = 4 stat tiles; "Next steps" = rows with You / Optional tags, a title, a one-line reason, and an action button where Claude can help.
