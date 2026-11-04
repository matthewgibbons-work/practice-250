> Model answer, written by Claude for the instructor's practice repo.

# NOTES — S03 · Theme palette

## Intent
A Saturday-morning cartoon page in the style of a 1990s cereal box: loud, sugary, and a little ridiculous. It's for someone my age scrolling on their phone between classes, so the colors have to be fun without the text ever getting hard to read.

## AI use
The course agent (Claude Code, standing in for Copilot in the model repo). I gave it my intent and the done list and asked: "Propose the four colors with roles and contrast ratios first (calculate them, don't guess); if they all pass, go ahead and build."

## Accepted / changed / rejected
- Accepted: Milk, Grape Night, Cereal Box Red, and Honey Yellow. I checked every pair myself and got the same ratios: 15.09:1, 5.47:1, and 11.24:1.
- Accepted: putting the heading's worst point (the red end of the gradient) in the contrast table, not just the dark end.
- Accepted: links stay underlined, so they don't rely on red alone.
- Rejected: nothing yet. Next time I'd try a brighter red; this one is closer to ketchup than to a cereal box, and it only just passes.

## Dig deeper
`hsl()`: https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/hsl. The middle number is how colorful it is and the last is how light, so I could see Milk and Honey Yellow are nearly the same hue (43 and 46) at very different lightness.

## Open questions
Why does red at 42% lightness still pass on cream, when yellow at 62% would fail? Lightness in `hsl()` doesn't seem to match how bright a color looks.
