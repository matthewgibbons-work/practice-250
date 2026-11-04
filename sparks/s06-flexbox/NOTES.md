> Model answer, written by Claude for the instructor's practice repo.

# NOTES — S06 · Flexbox header and cards

## Intent
A page about the drive-in's double features this season, for people deciding which Friday to go. The cards up top are a quick way in for someone who doesn't want to read the whole page: tap the double feature you care about and jump straight to its showtimes and what to bring.

## AI use
The course agent (Claude Code, standing in for Copilot in the model repo). I gave it my intent and the done list: "Propose a plan first (the page's sections, which elements become flex containers, which direction); if it covers the done list, go ahead."

## Accepted / changed / rejected
- Accepted: three flex rows (the header, the nav, and the card list), each with `flex-wrap: wrap` and `gap` instead of margins on every item.
- Accepted: the cards are a `<ul>`, and each links to a `<section>` with a matching `id`, so "Jump to Monster Night" lands on Monster Night.
- Accepted: the cards stay in date order in the HTML. Date order is what people planning a Friday want, and Tab follows it.
- Checked: I tabbed from the top to the bottom, and focus followed the order I see.

## Dig deeper
`flex-wrap`: https://developer.mozilla.org/en-US/docs/Web/CSS/flex-wrap. Without it, flex items squeeze onto one line however narrow the screen gets. With `wrap`, they move to a new line when they run out of room, which is what keeps the cards readable at 200% zoom.

## Open questions
`gap` works the same on the header, the nav, and the cards. When would I ever still want margins between flex items?
