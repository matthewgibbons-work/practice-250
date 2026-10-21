> Model answer, written by Claude for the instructor's practice repo.

# NOTES — S01 · Repo restructure

## Intent
I reorganized my DIGHT 250 repo so the new Sparks, Prototypes, and Release each have a place, and my old work is kept safe in `archive/`. It's for me, so I can find things all term, and for whoever grades it, so every assignment has its own folder and its own notes.

## AI use
GitHub Copilot Chat in VS Code (Copilot Free). I pasted the Spark 0 Start prompt from the course site and said "next" after each step. I asked it "why do the old links still work if everything moved?" and "what is a landmark?"

## Accepted / changed / rejected
I accepted the plan to move everything old into `archive/` together, because the relative links between the pages stay the same. It found that my episode guide linked to `/cartoon/` with a slash at the start, which would break once it moved, and changed it to `../cartoon/`. I accepted that after it explained the leading slash means "start at the top of the site." I changed the hub: I used a nickname instead of my real name since the repo is public, and I replaced the empty Prototypes list with a line saying P1 starts Oct 26.

## Dig deeper
Relative URLs: https://developer.mozilla.org/en-US/docs/Learn_web_development/Howto/Web_mechanics/What_is_a_URL. `../` means "go up one folder" and a path that starts with `/` starts from the root of the site, which on GitHub Pages isn't always my repo.

## Open questions
Desktop showed the moved files as deleted and new. The agent said Git figures out they're moves, but I don't really get how it knows that without me telling it.
