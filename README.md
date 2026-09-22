# DirtView docs — docs.dirtview.com

Mintlify documentation site for DirtView. Written for construction workers, foremen,
PMs and admins — many of whom are non-technical, and some of whom work in Spanish.

## Structure

The sidebar mirrors the **DirtView University** video curriculum one-to-one, top to
bottom, so a written guide and its video always sit in the same place.

| Series | Folder | Pages |
| --- | --- | --- |
| 00 Orientation | `orientation/` | 4 |
| 10 Projects | `projects/` | 4 |
| 20 Drawings | `drawings/` | 5 |
| 30 Specifications | `specifications/` | 3 |
| 40 Forms | `forms/` | 6 |
| 50 RFIs, submittals & change orders | `approvals/` | 8 |
| 60 T&M tickets | `tm-tickets/` | 4 |
| 70 Files & communication | `files/` | 4 |
| 80 People & permissions | `people/` | 5 |
| 90 AI, voice & Procore | `ai/` | 6 |

Plus `index.mdx`, `quickstart.mdx`, `video-library.mdx`, `help/`, and the Spanish
tree under `es/`.

One page per video, titled as the question a user would type into search. That's
what makes the site linkable answer-by-answer, which is how support will use it.

## Publishing a video

**Edit one file: `snippets/video.mdx`.**

Find the video's ID in the `VIDEOS` map and paste in its share link:

```js
"50.1": { series: "50", title: "Writing an RFI that gets answered", runtime: "2:30", track: "Core", url: "https://www.loom.com/share/abc123" },
```

Every page using `<Video id="50.1" />` switches from a grey placeholder to a real
player. No page edits.

Loom, YouTube and Vimeo share links all work — paste the normal URL, not the embed
code. Update `runtime` to the real length while you're in there.

## Local preview

```bash
npm i -g mint
mint dev
```

Then open http://localhost:3000. Run `mint broken-links` before pushing.

## Publishing changes

The Mintlify GitHub app deploys the default branch to docs.dirtview.com
automatically. Install it from the Mintlify dashboard if it isn't connected yet.

## Spanish

Localization is configured in `docs.json` under `navigation.languages`. Spanish
pages live under `es/` at the same relative paths as their English counterparts.

Orientation (series 00), the welcome page, the quickstart and the language guide are
translated. To add a series:

1. Copy the English folder to `es/<folder>/`, keeping the same filenames.
2. Translate `title`, `description` and the body. Leave the `<Video id="...">` alone —
   the same registry entry serves both languages.
3. Point internal links at their `/es/...` equivalents.
4. Add the pages to the `es` group list in `docs.json`.

Series 00, 40, 60 and 90.1 are the field-facing ones and are being recorded in
Spanish as well — prioritize those folders.

## Before launch — what still needs filling in

Pages contain `{/* TODO: ... */}` comments marking anything that needs verifying
against the product before it goes in front of a customer. They don't render, so the
site is publishable as-is, but each one is a claim nobody should guess at.

```bash
grep -rn "TODO" --include=*.mdx .
```

Highest-stakes ones, roughly in order:

1. `projects/projects-list.mdx` — where the **% completed** figure comes from.
2. `approvals/create-a-submittal.mdx` — the exact difference between **version** and **revision**.
3. `approvals/submittal-review.mdx` — what sets the due date and who sees **Overdue**.
4. `people/certifications.mdx` — the expiry warning window and who gets notified. Compliance feature; must be exact.
5. `tm-tickets/approve-tickets.mdx` — what rolls into **Impact Cost**. It gets read in owner meetings.
6. `people/custom-roles.mdx` — the Permission Matrix axes and what each level grants.
7. `drawings/markup-a-sheet.mdx` — measure-tool calibration, and who can see your markup.
8. `help/support.mdx` — the actual support email, hours and status page.

Also confirm before launch:

- `docs.json` → `navbar.primary.href` currently points at `https://dirtview.com`. Change it to the real app URL.
- Screenshots. Every page has a commented `{/* SCREENSHOT: ... */}` or `<Frame>` marker where one belongs; drop the images in `images/` and uncomment. The single most valuable one is the annotated company-level vs. project-level screenshot on `orientation/how-dirtview-is-organized.mdx`.

## Deliberately not documented yet

**Project Schedule** and **Recent Activity** on the Project Dashboard are behind a
*Coming soon* overlay. Documenting or filming them now means redoing it, and it
invites questions the product can't answer yet. `projects/project-dashboard.mdx` says
so explicitly — update it the day they ship.

## House style

See `AGENTS.md`. The short version: one question per page, plain words, second person,
and open on the confusion rather than the happy path.
