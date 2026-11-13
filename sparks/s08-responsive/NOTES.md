> Model answer, written by Claude for the instructor's practice repo.

# NOTES — S08 · Responsive at 320px

## Intent
A page for the winter club fair, for a freshman walking between the tables with their phone out. They've just talked to a club and want to know one thing before they sign up: when and where it meets, and whether that clashes with their classes. So the meeting-times table goes first, with how to sign up right after it.

Prediction: For one column on a phone I think it's nothing at all, just no `display: grid` in the base CSS. For the sidebar coming back I think it's `@media (min-width: …)` with `display: grid` and `grid-template-columns` inside it. For the table I think it's `overflow-x: auto` on a box around it, plus `max-width` on the page.

What it used: One column was right: the base CSS has no grid, only `max-width: 70rem` and some padding on a `.page` wrapper, and the header, main, sidebar, and footer just stack in HTML order. The sidebar was right too: `@media (min-width: 50em)` turns on `display: grid`, `grid-template-columns`, and `grid-template-areas`. What I missed is that the column size matters as much as the media query. It used `minmax(0, 1fr) 16rem`, not `1fr 16rem`. With plain `1fr` the page scrolled sideways from 800px up to about 1050px, because the main column wouldn't get narrower than the table. The table part matched (`overflow-x: auto` on a `div` around it), but `max-width` on the page doesn't help the table at all. It just stops the page getting too wide on a big screen. I also didn't guess `white-space: nowrap` on the cells, which keeps times like "8–9:30 p.m." on one line and lets the box scroll instead.

## AI use
Claude Code. I gave it my intent and the done list and said: "Propose a plan first: the one-column base, the width where the sidebar comes in and why, and how the table fits at 320px. Don't write HTML or CSS until I agree." I asked why it picked 50em. After I agreed I had it build `index.html` and `style.css`, then asked it to check every width from 320 to 1200 for sideways scrolling, and to try the same page with `1fr` instead of `minmax(0, 1fr)` so I could see the difference.

## Accepted / changed / rejected
Accepted: the 50em breakpoint, because of the reason it gave. Under 50em, a 16rem sidebar would leave the main column under about 30rem, which is cramped for the table. Over 50em, the one-column text runs past about 70 characters a line, which is too long to read. That's where the content breaks, not "a tablet is 768px." I also kept it in `em` so someone with big text gets one column sooner.

Accepted: `minmax(0, 1fr)`. I didn't believe it mattered until it showed me the `1fr` version: at 820px the page was 1052px wide and dragged sideways. With `minmax(0, 1fr)` nothing scrolls sideways at any width from 320 to 1200, and only the table scrolls inside its box.

Accepted: the table box has `tabindex="0"`, `role="region"`, and `aria-labelledby` pointing at the caption. I pressed Tab once and it got an orange outline, then the right arrow scrolled it.

Changed: nothing in the code this time. The first version passed the 320px check, the width sweep, and the keyboard test, so the thing I'd change is still a question (the caption, below).

Rejected: nothing hidden. The sidebar is below the main section on a phone, not gone, because the sign-up steps are what someone at the fair needs right after the times.

## Dig deeper
`@media` and the `min-width` feature: https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/@media
In a media query, `em` means the browser's default font size, not the font size of any element, so `50em` is 800px for most people but bigger if someone set a larger text size. That's why my breakpoint follows the reader's font settings and a `px` one wouldn't.

## Open questions
When the table scrolls sideways, the caption scrolls away with it, so on a phone you can scroll until "Weekly meetings" is half off the left edge. I'm not sure if the caption should go outside the scrolling box, or if that breaks `aria-labelledby` pointing at it. I also don't fully get why a grid column won't shrink below its content unless you say `minmax(0, …)`. What is the "auto" minimum that `1fr` has?
