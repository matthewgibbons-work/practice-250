> Model answer, written by Claude for the instructor's practice repo.

# NOTES — S09 · Final Project intent brief

## Intent
An intent brief for my Final Project: a five-page site that defines the Digital Humanities for my grandpa, a retired history teacher who thinks DH means "putting old books on the internet." I chose the Valley of the Shadow, the Old Bailey, and the Colored Conventions Project because each one does something a library shelf can't: follow families across both sides of a war, search two centuries of trials for patterns, and bring in records his textbooks left out, with volunteers doing the work. I also looked at the Blake Archive, but it's about art, and Grandpa's question is about history.

## AI use
Claude Code. I wrote the brief in a text file first, then pasted it with the S09 prompt ("Turn this into a valid, accessible HTML page … Don't change my wording"). It asked three questions before writing anything: copy the definition placeholder as written, which way to show the links, and whether I wanted CSS. I said yes to a short `style.css`. Then I asked "Which of my 'done' lines would be hard to check, and why?"

## Accepted / changed / rejected
- Accepted: the page with my headings and wording exactly as I wrote them (I compared every line).
- Accepted: links shown as the URL in parentheses, the way I wrote them, instead of turning the project names into links, so my wording didn't change.
- Changed: my last "done" line said "in my reflections," which doesn't name a place, and depended on Grandpa's schedule. Now it says "on my reflections page," with my roommate as a backup.
- Rejected for now: rewriting the alt-text line. Claude's right that axe can't tell whether alt text fits, but I'll check that myself, image by image.

## Dig deeper
`ch` units (https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Styling_basics/Values_and_units): `1ch` is the width of the "0" character in the current font, so `max-width: 65ch` keeps lines around 65 characters, which is easier to read. Because it's tied to the font, the line length stays about the same when someone zooms or makes the text bigger.

## Open questions
How do I check every color pair, including visited and focus links, without missing one? And if a project's images aren't free to reuse, is my own screenshot allowed, or is that still their image?
