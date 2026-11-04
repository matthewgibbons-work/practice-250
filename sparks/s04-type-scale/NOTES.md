> Model answer, written by Claude for the instructor's practice repo.

# NOTES — S04 · Type scale

## Intent
A type specimen for a 1950s drive-in movie night: big, friendly marquee headings, but body text that someone reading on their phone in a dark car can still read comfortably. The headings can show off; the paragraphs can't.

## AI use
The course agent (Claude Code, standing in for Copilot in the model repo). I gave it my intent and the done list and asked: "Propose a plan first (fonts with a reason for each, the scale, line height); if it covers the done list, go ahead."

## Accepted / changed / rejected
- Accepted: Righteous for headings. Its rounded, chunky letters look like a neon marquee, and it's only used big, where it's easy to read.
- Accepted: the system font for body text at 1.125rem with a line height of 1.6, because a phone in a dark car is a hard place to read.
- Accepted: sizes in `rem` (1.125, 1.5, 2, 3), so they all grow when the reader makes their browser text bigger.
- Changed: the agent wrote the "Why these fonts" section itself. The reasons were mostly mine, but the wording wasn't, so I rewrote it in my own words. It also said lines stop at about 65 characters, which I never asked about, so I took that out.

## Dig deeper
`line-height`: https://developer.mozilla.org/en-US/docs/Web/CSS/line-height. A number with no unit (1.6) is multiplied by each element's own font size, so headings and body text each get spacing that fits them. With `px` they'd all share one.

## Open questions
The scale jumps from 2rem to 3rem for the main heading. Is there a rule for choosing those steps, or is it just what looks right?
