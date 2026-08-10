# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Renta Fija 2026-II** (course code 1F0115, Universidad del Pacífico) is a Fixed Income
course delivered as static HTML. Content is in Spanish. There is no build step.

- **index.html**: course map. One MAIN tab plus 16 week tabs, all generated at runtime
  from a `CRONOGRAMA` array. Week tabs carry no teaching content: each one is a launcher
  that shows the schedule of that week and links to its one-pager.
- **w#_onepager.html**: one document per week (1 to 7 and 9 to 13 exist; 8 and 16 are exam
  weeks, 14 and 15 are not published yet). Each one holds the full development of the topic.
- **assets/onepager.css**: the single stylesheet every one-pager links. Editing it changes
  all twelve documents at once. `index.html` keeps its own inline `<style>` because it is a
  different surface (dark app shell), but it uses the same tokens.
- **assets/Logo UP.jpg**: institutional mark, shown on a white plaque over dark surfaces.
- **Cronograma.pdf** and the syllabus PDF are the source of truth for dates, topics and
  assessment weights.

## Design system

Both surfaces share the same tokens. Anything outside this list is a bug.

**Palette** (institutional, no other colors allowed):

```
--ink   #000000    --navy  #061942    --corp  #1E3771
--mid   #0054B0    --vivid #0000FF    --steel #CED5DD
--gray  #D1D1D1    --off   #F2F2F2    --white #FFFFFF
```

Tints are built with `rgba()` over these values (`--pale`, `--pale-mid`, `--t-mute`, and so
on). `--vivid` is reserved for focus rings, text selection and the progress fill.

**Type**: three voices, declared as `--display`, `--ui` and `--body` / `--sans`.

| Voice | Face | Used for |
|---|---|---|
| display | Montserrat 600/700/800 | headings, week numbers, big figures |
| ui | Tahoma | labels, tabs, badges, dates, tabular data |
| body | Open Sans | running text |

**House rules** (these are explicit client requirements, do not relax them):

- No em dashes and no en dashes anywhere in copy. Use a comma, a colon, parentheses, or a
  middot `·` for label separators. Ranges read `10:30 a 13:20`.
- No colored borders on shapes. Separation comes from surface fills, weight and spacing.
  Neutral hairlines in `--steel` or `--gray` are fine.
- No emoji standing in for icons. Icons are authored SVG at 1.5 to 1.7 stroke width,
  `currentColor`, defined once in an SVG sprite and referenced with `<use>`.
- No eyebrow labels above headings, and no decorative "hero metric" boxes.

## index.html

Everything below MAIN is data driven, so most edits mean touching an array, not markup.

```js
const SEMANAS_AVANZADAS = [];             // semanas ya dictadas
const ONEPAGERS_PUBLICADOS = [1,2,...];   // one-pagers publicados
const CRONOGRAMA = [ /* 16 entradas */ ];
```

- **Mark a week as taught**: add its number to `SEMANAS_AVANZADAS`. The percentage counter,
  the progress bar, the week cell and the tab marker all update from that single list.
- **Publish a one-pager**: create `w#_onepager.html` and add the number to
  `ONEPAGERS_PUBLICADOS`. The button switches from "Próximamente" to a live link.
- **Change a date, room or topic**: edit the matching `CRONOGRAMA` entry. Exam weeks use
  `tipo:'examen'` with `rango`, `texto` and `cubre`.
- **Deep links**: `index.html#s7` opens week 7, `index.html#main` opens MAIN. One-pagers
  link back with `index.html#sN`.
- MAIN also carries the four syllabus units, the assessment table and the course
  bibliography. Those are static markup inside `#slide-0`.

## One-pagers

Every `w#_onepager.html` follows the same order:

1. `.doc-header` with title, week line and the section index (`.header-pills`).
2. `#resumen` (section-block, `.lead`)
3. `#keywords` (section-block, `.kw-list` with `.badge` variants)
4. `#conceptos` (section-block, `.concepts` list plus the `.applies` two-column block)
5. `#onepager` divider, then the numbered modules (`#module-01`, `#module-02`, ...), each
   with its `.section-block` subsections numbered `1.1`, `1.2` and so on.

Math is rendered with **MathJax 3** (`\( \)` inline, `\[ \]` and `$$ $$` display).
`index.html` has no math and loads no math library.

Vertical rhythm is owned by the stylesheet: `.section-body > * + *` sets the gap between
blocks. Do not add inline `margin` or `font-size` to the HTML; add or reuse a class instead.

## Common tasks

- **View locally**: open `index.html` in any modern browser. No server needed.
- **Add a week**: append an entry to `CRONOGRAMA`. Tabs, slides, the progress grid and the
  labels are all derived from it, so nothing else has to change.
- **Change the look of every one-pager**: edit `assets/onepager.css` only.
- **Check the work**: `node .agents/skills/impeccable/scripts/detect.mjs --json <files>`
  flags design regressions. A single `overused-font` warning on Montserrat is expected and
  accepted, since the typeface is a client requirement.

## Other files

`exercises.html` (week 6 exercises) and `resources/*.html` (explainers) predate this
revision and still use the old inline styles. They are reachable from a couple of
one-pagers but were left untouched on purpose.

## Git workflow

Files are versioned individually, there are no build artifacts, and `.gitignore` excludes
`backup/`. Commit messages reference the week and the kind of change, for example
"Update W3 concepts and bibliography".
