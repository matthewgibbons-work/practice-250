> Model answer, written by Claude for the instructor's practice repo. **Stand-in (Oct 28):** built by Claude from the S03 brief so the S04 dry run has a page to start from; the S03 dry run itself ran outside this repo on Oct 26.

# NOTES — S03 · Theme palette

## Intent
A one-page style tile for a retro Saturday-morning cartoon theme: bright and playful, like cereal-box colors, but still readable on a phone in sunlight. It's for anyone browsing the Saturday Morning Archive, and I'll reuse the palette as the start of my P1 show page.

## AI use
GitHub Copilot Chat (Copilot Free). I pasted my intent and the "done" list and asked for four colors with roles and contrast ratios before any code, then for each color in hex, `rgb()`, and `hsl()`.

## Accepted / changed / rejected
I accepted the cream, navy, red, and yellow roles. I checked every ratio in WebAIM myself and put those numbers in the table, not the agent's. I checked the banner heading at the orange end of the gradient, because that's its worst point.

## Dig deeper
`hsl()`: https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Values/color_value/hsl. The last number is lightness, so the same hue at a lower lightness gives a darker version for a hover.

## Open questions
Does a gradient's contrast change in the middle, or is the worst point always one of the ends?
