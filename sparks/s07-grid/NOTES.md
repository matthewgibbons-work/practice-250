> Model answer, written by Claude for the instructor's practice repo.

# NOTES — S07 · Grid layout

## Intent
A trail guide for BYU students who want a hike close to campus but don't have a car-free afternoon to research it. The page shows four hikes as cards so you can compare distance and difficulty side by side, with the stuff you need before you leave (where to park, what the trails are like this week, what to bring) in a sidebar right next to them instead of at the bottom.

Prediction: For the page I think it's `display: grid` with `grid-template-areas` (like `"header header" "main aside" "footer footer"`) and `grid-area` on each part, plus `grid-template-columns` to make the sidebar narrower than the cards, something like `1fr 16rem`. For the cards I think it's another grid with `repeat(auto-fit, minmax(15rem, 1fr))` and `gap`, so I never say how many columns.

What it used: The page part matched: `display: grid` right on the `body`, `grid-template-columns: 1fr 16rem`, the three area strings I guessed, and `grid-area` on the header, main, aside, and footer. I hadn't thought about where the grid goes, though. It put it on `body` because those four are its direct children, and `grid-area` only works on direct children. The cards were mostly right too (`repeat(auto-fit, minmax(…, 1fr))` and `gap: 1rem`), but the first number ended up as `min(15rem, 100%)` instead of `15rem`. I didn't predict that because I was thinking about a wide screen. With plain `15rem`, once the main column got narrower than 15rem (about a 500px window, or 200% zoom on a small laptop) the card couldn't shrink and the whole page scrolled sideways. My guess was basically the At a glance table's example values, so I got it "right" without knowing why the sidebar is `16rem` and the cards are `1fr`.

## AI use
Claude Code. I gave it my intent and the done list and asked: "Propose a plan first: the area strings you'll use and which element goes in each. Don't write HTML or CSS until I agree." After I agreed, I asked it to build `index.html` and `style.css`. Then I asked it to test the page at narrower and narrower widths and tell me where it started scrolling sideways.

## Accepted / changed / rejected
Accepted: the area strings `"header header" "main aside" "footer footer"`. I could sketch the Wanted picture from them, and they go in the same order as the HTML (header, main, aside, footer), so Tab goes through the cards first and then the footer, the same order I read them in. I also kept the facts in an `<aside>` with its own heading, so a screen reader can jump to it as a landmark.

Changed: the cards first used `minmax(15rem, 1fr)`. It looked done on my laptop, but at 512px wide the page scrolled sideways, which is the thing the brief said people miss. Changing it to `minmax(min(15rem, 100%), 1fr)` means a card is 15rem unless the column is narrower than that, and then it just fills the column. Now the cards go 4 → 3 → 2 → 1 columns as the window narrows and nothing scrolls sideways.

Rejected: the agent also tried `minmax(0, 1fr)` for the main column. It stopped the sideways scroll at a phone width, but the main column shrank to nothing and the cards spilled over the sidebar, which is worse. I kept `1fr` because S08 is when we fix the phone layout.

## Dig deeper
`min()`: https://developer.mozilla.org/en-US/docs/Web/CSS/min
It picks the smallest of the values you give it, and it can mix units, so `min(15rem, 100%)` compares a fixed size with the size of the container and uses whichever is smaller. That's why it can go inside `minmax()`: the minimum still says "about 15rem", but it's never wider than the column.

## Open questions
Below about 500px wide the sidebar still takes 16rem and squeezes the cards into a tiny column. I'm not sure if the fix is a media query that changes the area strings, or making the sidebar column something like `minmax(…)` too. I'm also not sure why `1fr` for the main column refuses to go narrower than the cards inside it, but `minmax(0, 1fr)` doesn't.
