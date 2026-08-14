# Design System Prompt: "Ledger" Style HTML Pages

Use this prompt to instruct any LLM to generate a single-file HTML document in this style. It's topic-agnostic — works for meal plans, itineraries, project timelines, workout programs, reading lists, onboarding guides, or any content that breaks into **numbered sequential sections, each containing a few sub-items with a label + description + optional metric.**

---

## The prompt (copy/paste and fill in the brackets)

```
Create a single-file HTML document using the "Ledger" design system below.

CONTENT: [describe your content — e.g. "a 4-week onboarding plan for new
hires, one week per section, each with 3-4 tasks"]

DESIGN SYSTEM — follow exactly:

FONTS (load via Google Fonts link tag):
- Display/headline font: 'Fraunces' (serif, weight 400-600, supports
  optical size axis opsz 9..144) — used for big numbers, headings, titles
- Body font: 'IBM Plex Sans' (weight 400-600) — used for all running text
- Mono/label font: 'IBM Plex Mono' (weight 400-500) — used for
  eyebrows, timestamps, tags, metrics, anything data-like

COLOR PALETTE (CSS custom properties, define at :root):
--paper:   warm off-white background (e.g. #f2ede3) — never pure white
--ink:     near-black warm charcoal for dark sections (e.g. #232019)
--charcoal: slightly lighter warm dark for secondary text (e.g. #3a352c)
--accent-primary: one saturated "brand" color for emphasis/numbers/tags
--accent-secondary: a second complementary saturated color for a
  second category of tag/status
--accent-pale: a very light tint of accent-primary for soft badges
--line: warm light gray-beige for hairline borders (e.g. #d8cfbc)
--gold: a muted warm gold/ochre for small highlight text

Pick accent colors that suit the CONTENT's subject matter — don't reuse
food-specific red/sage if the topic isn't food. E.g. a project timeline
might use deep blue + burnt orange; a fitness plan might use blue +
red for effort/recovery. Keep the palette to paper + ink + 2 accents +
1 highlight color, no more.

LAYOUT STRUCTURE:

1. HEADER (dark background using --ink, full-width, generous padding
   ~56px top):
   - Small mono "eyebrow" label above the title, uppercase, letter-spaced,
     colored --gold
   - Large serif H1 (clamp 34-56px), max-width ~700px, tight leading
   - One-sentence subline in muted light gray, max-width ~580px
   - A horizontal stat-row below: 3-4 flex columns, each showing a big
     serif number/value and a small mono uppercase label underneath,
     separated by thin vertical dividers
   - A thin decorative bottom border using repeating-linear-gradient
     striping the two accent colors — a small signature touch, not loud

2. NUMBERED SECTIONS ("days" in the original, but rename per content —
   "weeks", "modules", "stops", whatever fits):
   - Two-column grid per section: left column ~160px wide holds a large
     serif number (e.g. "01"), colored with accent-primary, plus a
     smaller label beneath it (e.g. day name, week title)
   - Right column holds a vertical stack of "entries" — each entry is
     its own mini-grid: a mono time/tag label on the left, then a bold
     name + smaller gray description, optionally a right-aligned mono
     metric/value
   - Sections are separated by thin top hairlines (--line), generous
     vertical padding (~34-38px) so it reads like a ledger or menu list,
     not cramped cards
   - Optional: a small pill/badge per section summarizing a running
     total or status, using --accent-pale background + accent border

3. NOTES/FOOTER SECTIONS (after the numbered list):
   - Same hairline-separated block pattern as above but single-column
   - Use for supplementary content: checklists (dash-prefixed list items
     with dashed bottom borders), a 2-3 column info grid (mono uppercase
     mini-headers + short paragraph each), or key-value lists

4. CLOSING CALLOUT (optional but recommended):
   - One final block using --ink as background again (bookends the
     header), rounded corners ~4px, padding ~32px
   - Short serif heading in --gold, one paragraph of muted light text
   - Use this for a single most-important takeaway or next step

TYPOGRAPHY RULES:
- Numbers and section identifiers: always Fraunces, never sans-serif
- Anything resembling data (times, metrics, tags, counts): always
  IBM Plex Mono, small size (11-13px), often uppercase with letter-spacing
- Body copy and descriptions: IBM Plex Sans, 13.5-15.5px, muted charcoal
  color rather than pure black

RESPONSIVE:
- Below 640px, collapse the two-column grids (number/label + content) to
  single column, stack stat-row items

TECHNICAL:
- Single HTML file, no external framework, plain CSS in a <style> block
- Load fonts via <link> to fonts.googleapis.com
- Use CSS custom properties (:root variables) for every color so the
  palette can be swapped in one place
- No JavaScript needed unless the content specifically calls for
  interactivity

TONE: The overall feel should read like a well-designed printed ledger,
menu, or field guide — warm paper tones, confident serif numerals,
functional mono labels, generous whitespace, thin hairline rules instead
of boxy card shadows. Avoid: rounded bubbly cards, drop shadows, bright
white backgrounds, generic SaaS-dashboard blue.
```

---

## Notes for whoever is filling this in

- **Swap the section unit freely.** "Day" → "Week," "Stop," "Chapter," "Phase," "Module" — whatever matches the content's natural sequence.
- **The stat-row in the header is doing real work** — it should preview the 3-4 numbers a reader most wants to know before they scroll (targets, totals, ranges, counts). Don't fill it with filler stats.
- **Two accent colors, used consistently** — e.g. one for "primary metric," one for "flag/warning." Reusing the same pair throughout is what makes the page feel designed rather than decorated.
- **Keep descriptions short** — one line, two at most, per entry. This layout is built for scanability, not paragraphs.
