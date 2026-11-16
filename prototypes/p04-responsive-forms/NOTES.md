> Model answer, written by Claude for the instructor's practice repo.

# NOTES — P4 · Responsive + Forms

## Intent
A sign-up form for the Board Game Club's table at the campus club fair. Most people fill it in on their phone, standing at the table or walking away from it, so it has to work with one thumb on a small screen and tell them in words when something's missing. Before the form they need to know what they're signing up for (weekly game nights, no experience needed), and after it, what happens next.

## AI use
Claude Code. I gave it my fields and the "done" list and asked for a plan first: the fields with their types, the phone layout, and the width where it changes, with a reason. It proposed 50em (about 30em of form, 15em of panel, and gaps) and said it would ask me which phone-friendly attributes to use instead of choosing. After I answered (the panel's details, a green card-table palette, system fonts, a layout unlike my S08 page, and my next-step idea), it built the form, then the media query, then the thank-you page and the hub link.

## Accepted / changed / rejected
- Accepted: the 50em breakpoint and its reason. At 200% zoom on my laptop the page drops to one column, which is what I wanted.
- Accepted: an error message after each required field, shown only on `:user-invalid`, starting with a word so it isn't colour alone. The year group uses `fieldset:has(input:user-invalid)`, which I hadn't seen before.
- Accepted: the "Club nights" panel comes *before* the form on a phone. The brief suggests intro, form, panel, but people at the fair ask "when is it?" first, so I kept it.
- Accepted: each radio and checkbox row is at least 44px tall, so it's easy to hit with a thumb.
- Changed: nothing yet. I checked contrast for the cream, green, and dark red pairs in WebAIM.

## Next step: what I tried
My idea: the right `type` and `autocomplete` on every field the phone can fill (`tel` with `autocomplete="tel"` on the phone number, `name` and `email` already), plus `autocapitalize="words"` on the name, `spellcheck="false"` on the email, and `enterkeyhint="next"` on each field with `"send"` on the last. I checked it in Chrome's device toolbar, which doesn't show a phone keyboard, so I couldn't see the keyboards there. On a real phone I'd check two fields: does the phone field bring up the number pad, and does the email keyboard have an `@` and no autocorrect? What I'd try next: `inputmode="numeric"` is not needed because `type="tel"` already brings up the number pad, but I'd test whether Return really says "Next" and jumps to the radio buttons, or skips them.

## Dig deeper
`enterkeyhint` (https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/enterkeyhint) only changes the *label* on the keyboard's Return key ("next", "send", "go"). It doesn't make Return move to the next field; the phone decides that. So "next" is a promise the phone has to keep.

## Open questions
Pressing Return in a text field can submit the whole form (implicit submission). If someone presses "Next" on the email field and the phone submits instead, they land on the thank-you page with half the form empty, except `required` should stop that. Does it, on every phone?
