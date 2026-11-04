> Model answer, written by Claude for the instructor's practice repo.

# NOTES — P2 · Box model + Flexbox

## Intent
A guide to five Saturday-morning cartoons from the late 80s, for someone who half-remembers a show and wants to find it again. They should be able to scan the cards on a phone, tap the one that looks familiar, and land on more about it.

## AI use
The course agent (Claude Code, standing in for Copilot in the model repo). I gave it my intent and the done list: "Propose a plan first (boxes, which elements are flex containers, card sizing); if it covers the done list, go ahead." It drafted the card text; I kept it short and checked each show's link.

## Accepted / changed / rejected
- Accepted: each card is `flex: 1 1 15rem`, so it starts at 15rem and grows to share the row. The page goes from one column to three with no media queries.
- Accepted: each card is itself a flex column with `margin-top: auto` on its link, so the links line up at the bottom even when one card's text is longer.
- Accepted: nav links as padded blocks inside the flex nav, 44.8 px tall in DevTools, and card link text that names the show ("Muppet Babies on Wikipedia"), not "Read more" five times.
- Spacing: three sizes, reused everywhere: `--space-s` 0.5rem (nav link padding, small gaps), `--space-m` 1rem (card padding, gaps between cards), `--space-l` 2rem (space above and below the card list).
- Noticed: with five cards, the last row has two cards that stretch wider than the three above. I left it, because nothing overlaps and it still reads in order.

## Dig deeper
`flex` shorthand: https://developer.mozilla.org/en-US/docs/Web/CSS/flex. `1 1 15rem` means "can grow, can shrink, start at 15rem". The 15rem is the starting size, not a fixed width, which is why the cards never overflow.

Stretch goal: the browser lines the cards up at 15rem each, plus the `gap`, and fits as many as it can in the row. When the next card's 15rem won't fit, it drops to a new line; then the cards on each line grow to fill the leftover space. So a narrow phone gets one per row, and a wide window gets three.

## Open questions
How would I stop the last row's cards from stretching wider than the others? Is that a job for Grid instead?
