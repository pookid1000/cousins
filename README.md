# The Ella Questions

An interactive page made for Ella — thirteen questions set at Cousins Beach, with dials,
multiple choice, written answers, and a report at the end generated from whatever she picks.

Built as a single self-contained HTML file. No build step, no dependencies, no backend.

## Running it

Open `index.html` in a browser. That's the whole thing.

## Deploying to GitHub Pages

1. Push this repo to GitHub.
2. **Settings → Pages → Source: Deploy from a branch**, branch `main`, folder `/ (root)`.
3. Wait a minute, then it's live at `https://<username>.github.io/ella-questions/`.

The page carries `<meta name="robots" content="noindex, nofollow">` so search engines skip
it. Anyone with the link can still open it — GitHub Pages sites are public.

## How it's put together

Everything lives in `index.html`:

- **`STEPS`** — the whole script. Each entry is one screen. Edit this array to change,
  reorder, add or remove questions; the progress lights and question numbering recount
  themselves automatically.
- **`WANTS`** — the eight "pick three" options. Each one carries the `promise` that gets
  written back to her in the report.
- **`DIAL_BANDS`** — the lines that appear under each dial as it turns, keyed by threshold.
- **`NOTES`** — the handwritten reminders that rotate under every question.
- **`verdictOf()`** — scores her answers into `romance` and `chaos` and picks one of five
  archetypes for the report's title and opening paragraph.
- **`renderSummary()`** — builds the final report: the dial readings, her answers as pull
  quotes, the promises, the "noted for the record" callbacks, and the letter.

### Step types

| type | what it renders |
|---|---|
| `intro` | opening screen |
| `choice` | one-of-four buttons, each with a reaction line |
| `dial` | draggable knob (pointer, click, or arrow keys), 0–100 |
| `text` | free writing, skippable |
| `multi` | pick up to `max` |
| `note` | full-screen handwritten interruption |
| `chosen` | the staggered "I choose you" sequence |
| `summary` | the generated report |

## Notes

- Answers are held in memory and mirrored to `localStorage` so she can close the tab and
  pick up where she left off. Nothing is sent anywhere — there is no server. If you want to
  read what she wrote, she has to show you the page.
- Fonts come from Google Fonts (Bodoni Moda, Jost, Caveat). Offline, it falls back to
  Didot/Georgia, Futura/system-ui, and a script face.
- Respects `prefers-reduced-motion`: the drifting lights freeze and the reveals stop
  staggering.
- Single committed visual theme (dusk), so it looks the same in light and dark mode.
