> Model answer, written by Claude for the instructor's practice repo.

# NOTES — S05 · Box model

## Intent
A snack-bar menu page for the same drive-in night: what's on offer, with a nav at the top to jump between the hub, my S04 type page, and my archive. People use it on a phone with one thumb while holding a soda in the other hand, so every link has to be a big, easy target.

## AI use
The course agent (Claude Code, standing in for Copilot in the model repo). I gave it my intent and the done list: "Propose a plan first; if it covers the done list, go ahead. Any words on the page that the brief says should be mine, leave a placeholder for me."

## Accepted / changed / rejected
- Accepted: `box-sizing: border-box` on everything, so a box is the size I set, padding and border included.
- Accepted: nav links as `inline-block` with `padding: 0.75rem 1rem`. As plain inline links the padding didn't push anything away; as inline-blocks it makes the link itself bigger.
- Link size: hovering each nav link in DevTools shows 52.8 px tall, above the 44 px I aimed for and well above the 24 × 24 px minimum. The narrowest is "My hub", 95.2 px wide.
- Changed: nothing yet. I'd like the two menu sections further apart on a phone.

## Dig deeper
`box-sizing`: https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing. With the default `content-box`, a 300 px box with 20 px padding is really 340 px wide. `border-box` keeps it at 300.

## Open questions
Why does vertical padding on a plain inline link show up in DevTools but not push the next line down?
