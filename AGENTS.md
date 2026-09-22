# DirtView docs — writing instructions

Instructions for anyone (person or AI tool) writing in this repo.

## About this project

- Mintlify docs site for DirtView, published at docs.dirtview.com
- Pages are MDX with YAML frontmatter; configuration lives in `docs.json`
- The sidebar mirrors the DirtView University video curriculum, series 00 → 90
- One page per video, so the written guide and the video always match

## Audience

Construction workers, foremen, project managers and administrators. Many are not
technical. Many read on a phone, outdoors, with one hand, while something is waiting
on them. A meaningful share work primarily in Spanish.

Write for that person. Not for a developer, and not for a buyer.

## Tone

- **Stupidly straightforward.** If a sentence needs re-reading, rewrite it.
- Short sentences. One idea each.
- Second person: "you". Active voice.
- Use the words the trade uses — sheet, spec section, ball in court, RFI, submittal,
  T&M ticket. Don't invent friendlier substitutes for words people already say.
- No developer jargon. No "leverage", "utilize", "seamless", "robust".
- Never assume the reader caused the problem.

## Page shape

Every guide page follows the same skeleton, in this order:

1. Frontmatter: `title`, `description`, `icon`
2. `import { Video } from '/snippets/video.mdx';`
3. `<Video id="NN.N" />` — the video first, so someone can watch instead of read
4. A `<Note>` with the one-line version of the answer
5. The steps, as `<Steps>`
6. What goes wrong, as `<Warning>` or `<AccordionGroup>`
7. `## Next` with two `<Card>`s

## Titles are questions

Title every page as the question a user would type into the search box.

- Good: "Where does this file go?"
- Bad: "Documents & Media overview"

This is what makes the site usable one answer at a time, and it's how support links
to it.

## Open on the confusion

Don't narrate the happy path. Lead with the thing people get wrong, then resolve it.
"These two lists look the same" is a better opening than "The Specifications screen
has two lists."

The curriculum names the specific misconception each page exists to clear. Keep it.

## Terminology

Use these exactly; they are load-bearing in the product:

| Use | Not |
| --- | --- |
| company level / project level | global / local |
| Ball in Court | assignee, owner |
| status | state, stage |
| Uploaded / Published (specs) | draft / live |
| submission / template (forms) | entry / blank |
| Employee / External Contact | user / contact |
| sheet | page, drawing (one sheet is a sheet) |
| Quantity field vs. Number field | never use them interchangeably |

Bold for UI elements: click **Submit**. Code formatting for file names and paths.

## Honesty rules — these matter more than polish

- **Never guess product behaviour.** If you don't know what a control does, write
  `{/* TODO: confirm ... */}` naming exactly what needs checking. An invented answer
  gets repeated in a progress meeting and then in a claim.
- **Don't overclaim AI features.** Say what a human still has to check. Every AI page
  ends up in front of a skeptical superintendent.
- **Don't document what isn't shipped.** Project Schedule and Recent Activity are
  behind a *Coming soon* overlay. Leave them out until they ship.
- Where a number affects money or safety, say what it is *not*. Impact Cost is an
  estimate; the measure tool is as good as its calibration.

## Spanish

- Spanish pages live under `es/` at the same relative path as the English page.
- Both languages share one video registry entry — don't duplicate IDs.
- Translate meaning, not words. A foreman's Spanish, not a manual's Spanish.
- Internal links inside `es/` point at `/es/...`.

## Videos

Never hard-code an embed in a page. Add the link to `snippets/video.mdx` and
reference the ID. That keeps one file as the source of truth for all 48 videos.

## Content boundaries

- Don't document internal admin tooling or anything on dev-only builds.
- Don't put customer names, project numbers or real addresses in examples. Use a
  single consistent fictional job across all examples, the same way the videos do.
