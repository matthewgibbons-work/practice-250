> Model answer, written by Claude for the instructor's practice repo.

# NOTES — P3 · Grid

## Intent
A home page for the Center Street Saturday Market (a made-up farmers market in Provo), for a BYU student who has never been and opens the site on Friday night to see if it's worth getting up for. In a few seconds they should know it's a market on Saturday mornings, be able to scroll the vendors on whatever screen they have, and spot the vendor of the week first, because that's the one stall I'd tell a first-timer to start at. Someone who's been before just wants this week's news and the hours, so those go in the sidebar.

Spec additions: seven vendor tiles (Canyon Orchard, Spring Creek Honey, Two Hens Farm, Tamale Abuela, Mt. Timp Bread Co., Hollow Pine Flowers, and Mesa Peppers as the vendor of the week). Sidebar: hours and location, plus "New this week."

## AI use
Claude Code. I gave it my intent and the done list and asked: "Propose a plan first: the area strings and the gallery's grid-template-columns. Don't write code until I agree." I read the strings (`"header header" "main aside" "footer footer"`, same order as my HTML) and said go. Then: "Build the page layout, then the gallery, then the inside of a tile. Leave the featured tile alone, I'm doing that myself." For the featured tile I didn't ask the agent for a fix. I used the brief's "Stuck?" hints and tested each try in DevTools myself.

## Accepted / changed / rejected
Accepted: the same page grid as S07 (`1fr 16rem` with three area strings) and `repeat(auto-fit, minmax(min(…, 100%), 1fr))` for the tiles, because I already knew why `min()` is there from S07.

Changed: the tile minimum started at `14rem`. On my 1024px laptop that gave only two columns, because main is about 697px wide and three 14rem tiles plus two gaps need 704px. I changed it to `13rem` to get three columns, and it still drops to one at 200% zoom. I also put `align-self: start` on the tile links. Before that, the featured tile's link was 659px wide, so clicking anywhere on that whole stripe opened it.

Rejected: `grid-auto-flow: dense` (more in Beyond). It fills the holes in the grid by moving later tiles up, so what you see stops matching the HTML and Tab jumps backwards.

## Beyond: what I tried
**Try 1, my own idea: stand out without getting bigger.** I gave the Mesa Peppers tile a light orange background, a 3px border in my accent color, and a "Vendor of the week" label. It was 4th in the HTML, because it was my 4th tile when I wrote them. At one column it worked fine, since nothing changed size. But on my laptop it was in the second row, right at the bottom of the screen, the same size as everything else. A first-timer would read three other vendors before reaching it, so it didn't really pass the "spot it at a glance" part.

**Try 2: `grid-column: span 2`.** Bigger seemed like the answer, so I tried the thing from the Live demo even though I knew it might break. At 512px wide (my laptop at 200% zoom) it forced a second column only 114px wide that slid under the sidebar, and the page scrolled sideways by 28px. Same failure as the demo.

**Try 3, after opening the "Stuck?" hints: `grid-column: 1 / -1`.** The first hint was the one that helped. `-1` means the last column line, so `1 / -1` means "from the first line to the last," however many columns there are. At three columns the tile is a full-width row, and at one column it's one column wide, so nothing scrolls sideways. But with the tile still 4th in the HTML, at two columns (800px) Two Hens Farm sat alone with a hole beside it, and then the featured row came after.

**Try 4: the second hint, `grid-auto-flow: dense`.** It filled the hole by pulling Tamale Abuela up next to Two Hens Farm. That looked tidy, but now Tamale Abuela showed up above Mesa Peppers while Tab still went to Mesa Peppers first. That's the Tab jumping the brief warned about, so I took it out.

**What I kept:** I moved the featured tile to be first in the HTML, kept `grid-column: 1 / -1`, gave it a bigger heading, and kept the colors and label from Try 1. Now it's the first thing under "This week's vendors" at every width. I checked at 2560, 1024, 800, 512, and 400px: never a hole, the order you see matches the HTML, Tab goes nav → Mesa Peppers → Canyon Orchard → …, and the gallery never makes the page scroll sideways.

**What I'd try next:** on a very wide screen the featured tile is one long stripe, and its text line gets long (I capped the paragraph at 40rem). I'd like it to be about two tiles wide when there's room and the full row when there isn't, but I don't know how to do that without a media query yet.

## Dig deeper
`grid-column` and negative line numbers: https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/grid-column
The numbers in `grid-column` are the lines between columns, not the columns themselves, so three columns have four lines. Negative numbers count from the end, so `-1` is always the last line of the grid you set up, and `1 / -1` covers the whole row whether `auto-fit` made one column or ten. `span 2` asks for two columns no matter what, which is why it adds a column when only one fits.

## Open questions
Below about 450px wide the whole page scrolls sideways again. That's not the gallery: the sidebar keeps its 16rem and `main` won't shrink past its content. I think that's the phone layout we do in P4. I also don't understand why `-1` still means "the last line" when `auto-fit` has collapsed some empty columns on a really wide screen. Is the last line still out past the empty ones?
