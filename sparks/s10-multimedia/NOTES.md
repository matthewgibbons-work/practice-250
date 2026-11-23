> Model answer, written by Claude for the instructor's practice repo.

# NOTES — S10 · Clip of the week

## Intent
A "Clip of the week" page for our Tuesday Film Club: one clip from the film we're showing next, and cards for the films from earlier weeks. It's for club members deciding whether to come, often checking on a phone between classes. The captions are for anyone watching where they can't play sound (the library, the bus with no headphones) and for our member who is hard of hearing and can't follow fast dialogue by ear, which matters for a film famous for people talking over each other.

Prediction: The clip that plays on its own → take `autoplay` off and add `controls` to `<video>`. The missing captions → a `<track>` inside the video pointing at a `.vtt` file. Badges in the page's corner → `position: absolute` on the badge and `position: relative` on the card. The link with no words → `aria-label` on the link.

What it used: The first three matched. `<video controls>` with no `autoplay`, a `<track kind="captions" srclang="en" label="English">` pointing at `friday.vtt`, and `position: relative` on `.card` with `position: absolute; top; right` on `.badge`. I didn't predict `kind="captions"` versus `subtitles`: captions are for people who can't hear the sound, so they're the right kind here. The link was the miss: it used a `<span class="visually-hidden">` with the words ("Read about Charade on Wikipedia") and `aria-hidden="true"` on the arrow, not `aria-label`. Both give the link a name, but the hidden text is real text in the page, so it gets translated with the page and copied with it, and `aria-label` doesn't.

## AI use
Copilot in VS Code (agent mode). I gave it my intent and the "done" list, not my prediction, with the brief's prompt: list the page's parts in order, which element each one is, and which element each badge is positioned against, and don't write `friday.vtt`. Its plan: header and nav, the title card as a `<figure>` with `<img>` and `<figcaption>`, the clip as a second `<figure>` with `<video>`, then a list of cards, each badge positioned against its own `<li class="card">`. I agreed and had it build the page.

Captions: [Matthew: two or three sentences on writing `friday.vtt` by listening, how many cues, and what was hard about the timing.]

## Accepted / changed / rejected
- Accepted: `<video controls preload="metadata">` with a fallback paragraph and a download link inside it, for a browser that can't play MP4.
- Accepted: `padding-right` on each card's `<h3>` so the "New" badge always has its own space and never sits on the title, even when the title wraps at 200% zoom or 320px.
- Changed: it set the video's `height="360"`, copied from my title card. The clip is 640 × 480, so I changed it to `480`; with the wrong ratio the browser saves the wrong amount of space and the page jumps when the video loads.
- Changed: its first `alt` for the title card was "Title card with His Girl Friday in cream letters on a dark background." That describes the picture, not its purpose. Now it's "This week's film: His Girl Friday, 1940.", and the caption under it says when and where, so the two don't repeat each other.
- Rejected: it offered to "draft captions you can correct." I said no: it can't hear the clip, so anything it wrote would be a guess that looks finished.

## Dig deeper
`position: absolute` (https://developer.mozilla.org/en-US/docs/Web/CSS/position): an absolutely positioned element is placed against its *containing block*, which is the nearest ancestor whose `position` isn't `static`. If no ancestor has one, it's the page itself, which is exactly why every badge piles up in the page's top corner without `position: relative` on the card. `relative` on its own doesn't move the card at all; it just makes the card the badge's reference point.

## Open questions
The video shows a black box until you press play, because `preload="metadata"` doesn't load a frame. Should I add a `poster` image, and if so, does it need its own alternative text somewhere? And when captions are on, do screen readers read them, or only show them?
