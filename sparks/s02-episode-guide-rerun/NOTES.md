> Model answer, written by Claude for the instructor's practice repo.

# NOTES — S02 · Episode Guide, re-run

## Intent
A short guide to *Animaniacs* Season 1 for a friend who has never watched it and wants to know which episodes to start with. My old version was just a list of titles; this one says why each episode is a good first pick.

## AI use
GitHub Copilot Chat (Copilot Free). I pasted my intent and the "done" list and asked for a plan first. Then: "Rebuild archive/episode-guide/ using only the two episodes on my old page. Don't add any episodes or air dates." Later: "Why is the title a `th` with scope row?"

## Accepted / changed / rejected
I accepted the table with a `<caption>` and `scope` on every header cell, and the `header`, `main`, and `footer` landmarks. It made the title column a row header, which I didn't know you could do. I changed its "Why start here" text, because it was generic ("a classic episode packed with laughs"), and wrote my own reasons. I rejected the air dates it offered to "fill in," because I couldn't check them, and the brief warned they can be made up.

## Dig deeper
`scope` on `<th>`: https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/th#scope. A screen reader uses it to say which header goes with a cell, so `scope="row"` on the title means each "why" cell is read with its episode title.

## Open questions
If I didn't put `scope` at all, would a screen reader still guess right on a simple table like this one?
