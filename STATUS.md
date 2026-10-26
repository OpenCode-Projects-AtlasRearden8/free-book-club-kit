# STATUS — Free Book Club Kit

Last updated: 2026-10-26

## What was built

A complete printable starter kit for hosting a book club in a living room or
library room. Nine HTML/CSS sheets in `src/` build into nine unbranded
US Letter PDFs in `printables/` via one local build script. No signups, no
network calls, no secrets, no personal data.

| Sheet (PDF) | Purpose |
| --- | --- |
| `host-plan-sheet.pdf` | One-page meeting plan: date, book, stop-at page, prep checklist, facilitation reminders |
| `member-card.pdf` | 4 cut-out member cards (name, genres, reader type, snack allergies) |
| `discussion-questions.pdf` | 12 any-book question stems + fill-in lines for the meeting's own questions |
| `pick-rotation-tracker.pdf` | 12-round rotation table with house rules and thumb key |
| `snack-seating-checklist.pdf` | Snacks, dietary notes, seating, lighting, tech, zero-effort fallbacks |
| `remote-call-notes.pdf` | 2 cut-out cards to keep remote members fully in the room |
| `club-charter.pdf` | One-page charter: purpose, seven rules, amendments, signature lines |
| `reminder-card.pdf` | 2 cut-out next-meeting invitation cards |
| `facilitation-tips.pdf` | Bonus sheet of friendly hosting/facilitation guidance |

Supporting files: `build.py` (build script), `tests/test_build.py`
(11-test suite), `README.md`, `LICENSE` (MIT), `.gitignore`.

## How to run it

```bash
pip install weasyprint          # local renderer only (no accounts/keys)
python3 build.py                # builds all 9 PDFs into printables/
python3 build.py --only club-charter   # subset build
python3 -m pytest tests/ -v     # verify every sheet builds a valid PDF
```

Print the PDFs at 100% scale ("Actual size") on US Letter.

## Verification results

- `python3 build.py` — builds all 9 sheets successfully (each reported with output size).
- `python3 -m pytest tests/` — **11 passed** (in ~10s). The suite verifies:
  - every sheet builds and produces a nonempty PDF with a `%PDF-` header
  - each sheet is exactly **1 page** and exactly **US Letter size (612×792 pt)**
  - expected per-sheet text is present in the extracted PDF text
  - PDFs are unbranded: no company, tooling, or personal-data tokens
  - HTML/CSS sources are unbranded and contain no external URLs (fully local)
  - build rejects unknown sheet names and is idempotent
- Visual QA: all 9 PDFs rasterized with `pdftoppm` and inspected — layouts
  fit their pages, cut-out cards align, checkboxes and write-in lines print
  correctly.

## Design notes

- Sheet design: US Letter, 0.5in margins, local system fonts only
  (Fraunces for headings, Karla for body, Caveat for handwritten accents) —
  so the build works offline with zero font downloads.
- Cut-out sheets (member cards, remote notes, reminder cards) use dashed
  borders and fit standard cutting patterns (2-up / 2×2).

## Known gaps / ideas for later

- No A4 page-size variant (sources are Letter; one CSS change plus test
  update would add it — the tests pin Letter size).
- No version with pre-printed discussion questions per book (templates are
  intentionally book-agnostic).
- No editable/interactive form-field PDFs; sheets are designed for
  handwriting after printing.
- WeasyPrint version differences (v70 used here to verify) may shift
  text-flow slightly on other versions; the 1-page test will catch overflow.
