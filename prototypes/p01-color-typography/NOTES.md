> Model answer, written by Claude for the instructor's practice repo.

# NOTES — P1 · Color + Typography

## Intent
Two pages, far apart. The first is a museum label for an exhibit of 1980s home computers, read by adults standing in a gallery who want facts quickly: calm, quiet, and serious. The second is a fan page for a Saturday-morning robot cartoon, read by fans on their phones: loud and cheerful. The homepage is for my classmates and instructor, and shows why each page's colors and fonts fit its reader.

## AI use
The course agent (Claude Code, standing in for Copilot in the model repo). I gave it my intent and the done list: "Propose a plan first (each theme's palette with calculated ratios, and fonts); if it covers the done list, go ahead. Any explanation text the brief says should be mine, leave clearly marked placeholders for me." It left four placeholders on the homepage, and I wrote all four.

## Accepted / changed / rejected
- Accepted: both palettes. I recalculated all nine contrast pairs myself, and every one matches the table.
- Accepted: IBM Plex Sans with Source Serif 4 for the museum, and Bungee with Nunito for the fan page.
- Changed: I wrote the homepage's four "why" paragraphs myself, then deleted the dashed placeholder style the agent had added for them.
- Kept on purpose: yellow only for headings and links on the fan page. Yellow on blue passes (8.58:1), but white paragraphs are easier to read for long.

## Dig deeper
`font-family` fallbacks: https://developer.mozilla.org/en-US/docs/Web/CSS/font-family. If the Google font hasn't loaded yet, the browser uses the next font in the list, so Georgia stands in for Source Serif 4 and the page never shows an unstyled serif.

## Open questions
Bungee is only for headings, but the browser still downloads the whole font file. Is there a way to load only the letters I use?
