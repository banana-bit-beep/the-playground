# Byte Night: how far can you get without JavaScript?

Hi both,

Before we start the JavaScript sessions, I want to show you how much modern HTML and CSS can do on their own. Plenty of things people reach for JS for (accordions, pop-ups, carousels, form checking, dark mode) are now built into the browser.

You're each taking **two topics** and working on the same starter page, **Byte Night**, a made-up tech meetup. We'll do it in two rounds: one topic each, then a **short presentation** each showing what you built and what you learned, then a break and the same again with your second topic.

Steve

---

## The plan

| Time | What |
|---|---|
| 0:00–0:10 | Work review |
| 0:10–0:15 | Brief, split the topics, open the starter |
| **Round 1** | |
| 0:15–0:45 | **Learner A: Topic 1 · Learner B: Topic 3** |
| 0:45–0:50 | Prep your presentation |
| 0:50–1:00 | Presentations (5 mins each) |
| 1:00–1:10 | Break |
| **Round 2** | |
| 1:10–1:40 | **Learner A: Topic 2 · Learner B: Topic 4** |
| 1:40–1:45 | Prep your presentation |
| 1:45–1:55 | Presentations (5 mins each) |
| 1:55–2:00 | Wrap-up: so what *is* JavaScript for? |

Finished a topic early? Push on to the **Could** tasks, or start the Git extra near the bottom of this sheet.

## Getting started

1. Open the `byte-night-starter` folder in VS Code.
2. Open `index.html` with Live Server, or just in your browser.
3. Look for the `<!-- LEARNER A -->` and `<!-- LEARNER B -->` comments. They show you which bits of the page are yours.
4. Each of you has your own CSS files, so you won't tread on each other's toes:

| File | Who | Topic |
|---|---|---|
| `css/base.css` | Given | Plain defaults, leave alone (Learner B can refactor it in Topic 4) |
| `css/components.css` | Learner A | Topic 1 |
| `css/forms.css` | Learner A | Topic 2 |
| `css/layout.css` | Learner B | Topic 3 |
| `css/theme.css` | Learner B | Topic 4 |

**The rule: no JavaScript at all.** No `<script>` tags and no `onclick`.

Each topic has three levels. Get the **Must** done first, then go as far as you can.

---

# Learner A: Behaviour without JavaScript

## Topic 1: Interactive components

**Must**
- **FAQ accordion.** Turn each question and answer in the FAQ into a `<details>` with a `<summary>`. Style it so it looks clickable (cursor, padding, a border between items).
- **Speaker bio popovers.** Give each bio paragraph a `popover` attribute and an `id`, then point its "Read bio" button at it with `popovertarget="that-id"`. Click the button and the bio pops up, with no JS.

**Should**
- Style the open state of the accordion with `details[open] summary`, and swap the arrow marker for your own using `summary::marker` or `summary::before`.
- Style the popover itself, and dim the page behind it with `[popover]::backdrop`.
- **Gallery carousel.** Make `.slides` scroll sideways (`display: flex; overflow-x: auto;`) and make it click into place on each slide with `scroll-snap-type` and `scroll-snap-align`.

**Could**
- Give all the `<details>` the same `name` attribute and see what happens to the accordion.
- Add a close button inside each popover using `popovertarget` and `popovertargetaction="hide"`.
- Make each slide take up most of the width so the next one peeks in from the side.

### MDN resources

**Start with these guides**
- [Using the Popover API](https://developer.mozilla.org/en-US/docs/Web/API/Popover_API/Using): the whole popover topic, step by step
- [Basic concepts of scroll snap](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Scroll_snap/Basic_concepts)
- [Creating CSS carousels](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Overflow/Carousels): useful for the Should and Could tasks

**Reference**
- [`<details>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/details) and [`<summary>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/summary). Check the `name` attribute on `<details>` for the Could task.
- [`::details-content`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Selectors/::details-content): style or animate the bit that opens
- [`popover` attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/popover)
- [`::backdrop`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Selectors/::backdrop)
- [`scroll-snap-type`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/scroll-snap-type) and [`scroll-snap-align`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/scroll-snap-align)
- Bonus: [`@starting-style`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/@starting-style) shows how to animate a popover opening

## Topic 2: Forms that check themselves

**Must**
- Give every field the right `type`: `email` for email and `number` for years of experience.
- Add validation attributes: `required`, `min`/`max` on experience, and `required` on the ticket radios (only one radio needs it).
- Add a UK postcode `pattern`. Start simple, such as letters then numbers, then improve it.
- Try submitting with rubbish in it and see what the browser does for you.

**Should**
- Style valid and invalid fields with `:user-valid` and `:user-invalid`, e.g. a red or green border.
- Add a hint under a field, such as `<small class="hint">Like M1 0AA</small>`, that only shows when the field is invalid: `input:user-invalid + .hint`.
- **The pizza trick.** Hide the dietary requirements field and only show it when "I'm staying for pizza" is ticked. Use `:has()`, for example `form:has(#pizza:checked) .dietary`.

**Could**
- Highlight the selected ticket option with `label:has(input:checked)`.
- Grey out the Register button while the form has any invalid fields: `form:has(:invalid) button`.
- **Break it.** Write down five test cases (inputs plus the expected result) and try them. Can you get bad data through? Hint: right-click → Inspect, then delete `required`...

### MDN resources

**Start with these guides**
- [Client-side form validation](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation): the main one for this topic
- [The HTML5 input types](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Forms/HTML5_input_types)
- [UI pseudo-classes](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Forms/UI_pseudo-classes): styling valid, invalid, required and so on

**Reference**
- [`<input>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input): every type and attribute in one place
- [Using HTML form validation](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Constraint_validation): more depth on validation attributes
- [`:has()`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Selectors/:has)

**For the "break it" discussion**
- [Input validation (MDN Security)](https://developer.mozilla.org/en-US/docs/Web/Security/Defenses/Input_validation): why you check on the server as well

---

# Learner B: Layout and look

## Topic 3: Layout with Grid

**Must**
- **Speaker grid.** Lay out `.speaker-grid` with CSS Grid so the cards sit side by side and wrap by themselves, with no media queries. Look up `repeat(auto-fit, minmax(…, 1fr))`.
- **Page layout.** Use `grid-template-areas` on `main` so that on wide screens **Schedule** and **Venue** sit side by side, and everything else stays full width. On narrow screens it should all stack.

**Should**
- **Fluid type.** Make the `h1` and `h2` grow and shrink smoothly with the screen width using `clamp()`, e.g. `font-size: clamp(2rem, 6vw, 4rem);`
- Lay out the inside of each speaker card with Grid too: avatar on the left, text on the right.

**Could**
- **Container queries.** Make each speaker card respond to *its own* width rather than the screen's. Put `container-type: inline-size` on the card's parent, then use `@container (min-width: …)` to switch the card's layout. Then explain to Learner A why this is different from a media query.
- Use `gap` everywhere instead of margins and see how much CSS you can delete.

### MDN resources

**Start with these guides**
- [CSS grid layout (Learn)](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/CSS_layout/Grids): a friendly walk-through
- [Grid template areas](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Grid_layout/Grid_template_areas): the "ASCII art" layout method
- [Realising common layouts using grids](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Grid_layout/Common_grid_layouts): a responsive `grid-template-areas` example very close to your task
- [CSS container queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Containment/Container_queries)

**Reference**
- [Basic concepts of grid layout](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Grid_layout/Basic_concepts): covers `repeat()`, `fr` and `minmax()`
- [`grid-template-areas`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/grid-template-areas) and [`grid-area`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/grid-area)
- [`clamp()`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Values/clamp)
- [`container-type`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/container-type) and [`@container`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/@container)

**Test yourself afterwards**
- [Test your skills: CSS grids](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/CSS_layout/Test_your_skills/Grid)

## Topic 4: Theming and motion

**Must**
- **Design tokens.** Create CSS custom properties on `:root` for your colours (background, text, accent, borders), and do the same for spacing and border radius. Use them across the page with `var(--…)`, refactoring the colours in `base.css` if you like.
- Give Byte Night a proper look: pick an accent colour and style the hero, the buttons and the header.

**Should**
- **Dark mode.** Add `@media (prefers-color-scheme: dark)` and override *only your custom properties* inside it. If you set the tokens up well, that should be about five lines. Test it by switching your OS or DevTools to dark mode.
- **Transitions.** Make buttons, links and speaker cards react smoothly on `:hover` and `:focus-visible`, for example a colour change or a small lift.

**Could**
- **Hero entrance.** Use `@keyframes` to fade and slide the hero text in when the page loads.
- **Be kind.** Wrap your animation in `@media (prefers-reduced-motion: no-preference)` so people who've switched motion off don't get it.
- **A dark mode toggle with no JS.** Add a checkbox to the header and use `:root:has(#theme-toggle:checked)` to switch your tokens. You'll be borrowing Learner A's `:has()` trick, so ask them.

### MDN resources

**Start with these guides**
- [Using CSS custom properties (variables)](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Cascading_variables/Using_custom_properties)
- [Using CSS transitions](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Transitions/Using)
- [Using CSS animations](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Animations/Using)

**Reference**
- [`var()`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Values/var): including fallback values
- [`prefers-color-scheme`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-color-scheme)
- [`color-scheme`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/color-scheme): makes form controls and scrollbars go dark too
- [`transition`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/transition)
- [`prefers-reduced-motion`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-reduced-motion)
- [`:has()`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Selectors/:has): for the dark mode toggle

---

## Your presentations (5 minutes each, after each round)

You'll do one after each round. Keep it informal. Share your screen and cover:

1. **Show it:** a quick demo of what you built.
2. **Show the code:** one bit you're proud of, and how it works.
3. **One surprise:** something you didn't know HTML or CSS could do.
4. **One limit:** something you hit that you think *would* need JavaScript, or a server.
5. **One for work:** somewhere you could use this in your job.

After the second round of presentations we'll answer one question together: **if HTML and CSS can do all this, what's JavaScript actually for?**

---

## Extra: put it together with Git

If you finish early, or want to try this after the session:

1. One of you puts the starter in a GitHub repo and adds the other as a collaborator.
2. Each work on your own branch: `learner-a` and `learner-b`.
3. Open a pull request each, review each other's code, and merge both into `main`.
4. You'll *probably* get a merge conflict in `index.html`. Sorting it out together is part of the exercise.

---

## For your portfolio and OTJ

This session counts as off-the-job learning, so log it. Screenshots of your page, your code and your slides or notes are good evidence for:

- **S1**: logical and maintainable code (tokens, tidy CSS)
- **S2**: effective user interfaces
- **S6 / S5**: test scenarios and testing (Learner A's "break it" cases)
- **S17 / B5**: security awareness (why front-end validation isn't enough)
- **S14**: source control (if you do the Git extra)
- **S15 / B7**: explaining technical work to others (your presentation)
- **B8 / B9**: curiosity and CPD

Have fun with it.
