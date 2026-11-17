> Model answer, written by Claude for the instructor's practice repo.

# NOTES — S09 · A form that asks

## Intent
An RSVP page for the Saturday Morning Archive watch party, for a classmate who sees the flyer and signs up on their phone between classes. Before they send it, they need to know when and where it is (9–11 a.m., the JFSB basement lounge) and that picking a morning is the one thing we really need; voting for shows is optional.

Prediction: For the vanishing labels I think it's a `<label>` with `for` matching the input's `id`. For the radio buttons with no question I think it's `<fieldset>` and `<legend>`, with every radio sharing one `name`. For red-from-the-start I think it's `:user-invalid` instead of `:invalid`. For the colour-only error I think it's `aria-describedby` on the input pointing at a hint, but I don't know how the words change without JavaScript.

What it used: The first three matched. Every field has a `<label for>`, both groups sit in a `<fieldset>` with a `<legend>` that asks the question, all three radios share `name="morning"`, and the error styles use `:user-invalid`. What I didn't guess was how the words change with no JavaScript: the hint holds two `<span>`s, and CSS swaps them. `input:user-invalid + .hint .hint-ok` hides the normal sentence and `.hint-error` shows "Check this: an email needs an @…". It also used `fieldset:has(:user-invalid)` to put a red border on the morning question and add " Choose one." after the legend with `::after`. I also missed that `required` goes on just one radio button, and that's enough for the whole group.

## AI use
VS Code with Copilot Free. I gave it my intent and the done list and pasted the brief's prompt: "Before you write any HTML, list each field you'd use: its label text, its type and autocomplete value, whether it's required, and which fields share a fieldset and what its legend asks. Wait for me to agree." It listed five fields and two fieldsets. I agreed after one change (below), then had it build `index.html`, `thanks.html`, and `style.css`. Then I asked: "How can the email hint say something different when it's wrong, without JavaScript?"

## Accepted / changed / rejected
Accepted: the two-span hint. The input's `aria-describedby="email-hint"` points at the whole `<p>`, and the hidden span has `display: none`, so a screen reader reads only the sentence that's showing. I typed `abc` and pressed Tab: the border went red and the words changed to "Check this:…".

Accepted: `:user-invalid`. I reloaded and nothing was red. Then I pressed Send with everything empty: the browser stopped on the name field, said what was wrong, and only then did the three required fields turn red.

Changed: its plan put a `placeholder="you@example.com"` in the email box as well as the label. The label was there, so it wasn't doing the label's job, but the hint already gives an example, and grey placeholder text was half the problem in the sketch. I took it out.

Changed: it marked the show checkboxes `required`, which would have made people vote for every show. They're optional now, and the legend says "(optional, pick any)".

Rejected: a "Your RSVP" summary on the thank-you page that read the answers from the URL. That needs JavaScript, which `AGENTS.md` rules out for 250, and the page only has to say what happens next.

## Dig deeper
`:user-invalid`: https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Selectors/:user-invalid
It matches a field that fails its rules only after the person has interacted with it: changed it and moved on, or tried to send the form. `:invalid` matches the moment the page loads, which is why every empty required field was red before anyone had typed.

## Open questions
The " Choose one." after the morning legend comes from CSS `::after`. Does a screen reader announce generated content in a legend, or does only sighted people get those words? Also, pressing Enter while a checkbox was focused sent the form. I thought only Enter in a text box did that.
