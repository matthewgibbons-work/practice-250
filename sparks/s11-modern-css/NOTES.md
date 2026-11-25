> Model answer, written by Claude for the instructor's practice repo.

# NOTES — S11 · Tokens and dark mode

## Intent
A December stargazing checklist for our campus astronomy club's first night out: five things to find in the sky, ticked off as you spot them. People use it outside, on a phone, in the dark, so a white screen ruins their night vision and lights up the whole group. It has to follow their phone's dark setting, stay readable, and show at a glance what they've already found.

Prediction: The white screen → `@media (prefers-color-scheme: dark)` and `color-scheme`. A new accent → custom properties on `:root` with `var()`. Contrast in both modes → new values for the color tokens in the dark block. No focus ring → `:focus-visible` with `outline`. Ticking an item → `:has(:checked)` on the list item, with `text-decoration`.

What it used: All five matched, and it used more than I guessed. The white screen: `color-scheme: light dark` on `:root`, a `<meta name="color-scheme">` in the `<head>` (so a dark phone doesn't flash white before the CSS loads), and a `@media (prefers-color-scheme: dark)` block that changes only the seven color tokens. A new accent: every color and spacing size is a token on `:root`, used with `var()`. Contrast: the dark values are all dim reds, because red light disturbs night vision least. No focus ring: `input:focus-visible, a:focus-visible` with a `--space-xs` accent outline and offset. Ticking: `.checklist li:has(:checked)` switches to the done colors and a colored left border, and a second rule puts `text-decoration: line-through` on the name. I didn't predict `accent-color`, which colors the checkboxes themselves from the same token.

## AI use
Copilot in VS Code (agent mode). I gave it my intent and the "done" list, not my prediction, with the brief's prompt: list the tokens, colors and spacing, with each color's light and dark value and the contrast ratio of each text pair in both modes, no JavaScript, and wait for me to agree. Its plan had seven color tokens, five spacing tokens, and eight pairs with ratios. I checked every ratio before I agreed (below), then had it build the page, the CSS file, and the hub link.

## Accepted / changed / rejected
- Accepted: a red-only dark mode (`--bg: #0b0606`, `--text: #e6b3b3`, `--accent: #ff6b6b`). I hadn't thought of night vision as a color choice, but it fits my intent better than a plain dark grey.
- Accepted: a ticked item shows done three ways (done colors, a line through the name, a thick left border), so color isn't the only cue. Every item has a left border in its own background color from the start, so ticking one doesn't shift the layout.
- Accepted: `max-width: 40rem` and `font-size: 1.25rem` stay typed in. They're a line width and a text size, not colors or spacing, so my done list doesn't cover them.
- Changed nothing in the code, but I corrected its numbers: its ratios were worked out by hand and were within 0.15 of mine, a little high in dark mode (the focus ring on the background is 7.26:1, not the 7.4:1 it claimed). Everything still passes.

| Pair | Light | Dark |
| --- | --- | --- |
| text on bg | 15.43:1 | 10.99:1 |
| text on surface (an item) | 16.96:1 | 10.30:1 |
| muted text on bg (intro) | 7.85:1 | 7.05:1 |
| muted text on surface (hints) | 8.63:1 | 6.60:1 |
| done text on done bg (a ticked item) | 8.29:1 | 6.35:1 |
| hint on done bg (a ticked item's hint) | 7.34:1 | 6.35:1 |
| link (accent) on bg | 9.04:1 | 7.26:1 |
| focus ring (accent) on bg, 3:1 needed | 9.04:1 | 7.26:1 |
| focus ring on surface | 9.93:1 | 6.80:1 |
| focus ring on a ticked item | 8.45:1 | 6.54:1 |

Worked out with the WCAG formula; WebAIM's checker gives the same to two places.

## Dig deeper
[`:has()` on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/:has): it selects the element *before* it when something inside matches, so `li:has(:checked)` is the list item, not the checkbox. Before `:has()`, CSS could only style things after or inside the checkbox, never the item around it.

## Open questions
The dark-mode checkboxes are filled with `accent-color`, but the unticked boxes still look grey. Is that the browser's own style, and can `accent-color` change it, or does that need more CSS?
