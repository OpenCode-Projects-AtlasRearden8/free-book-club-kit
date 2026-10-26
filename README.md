# Free Book Club Kit

Printable PDFs for hosting a warm, low-stress book club in your living room,
library room, or wherever enough chairs gather. Print at 100% scale on US
Letter, and you have an instant club: plans, cards, questions, trackers, and
one charter to rule out the boring arguments.

Made the way we like everything at **Asdale Dynamics, LLC** — plain English,
friendly tone, nothing to install beyond what's listed below, zero signups,
zero network calls, and zero guilt for members who didn't finish the book.
Everything builds locally from plain HTML/CSS, and the PDFs are unbranded:
share them, gift them, staple them, laminate them.

## What's in the kit

| Sheet | What it's for |
| --- | --- |
| Host plan sheet | The whole evening on one page: date, book, stop-at page, chair count, prep checklist, and facilitation reminders |
| Member cards (4 per sheet) | Cut-out cards with name, genres, reader type, and snack allergies — part name tag, part icebreaker |
| Discussion questions | Twelve stems that work for any book, plus fill-in lines for this meeting's own questions |
| Pick rotation tracker | Twelve rounds of picks so everyone gets a turn and nobody picks twice |
| Snack & seating checklist | Crunchy things, cozy chairs, lamps on / music off, and the honored cheddar clause |
| Remote call notes (2 per sheet) | Cards propped up so remote members stay in the room instead of on the screen |
| One-page club charter | Purpose, seven rules, amendment policy, and signature lines for the founding members |
| Next-meeting reminder cards (2 per sheet) | Cut-out invites with date, stop-at page, and an RSVP-by-emoji system |
| Facilitation tips | Bonus sheet: keeping it warm, keeping it moving, and what to do when it goes sideways |

## Build it yourself (recommended way)

Requirements: **Python 3.10+** and **WeasyPrint** —

```bash
pip install weasyprint
python3 build.py
```

That renders every sheet in `src/` into `printables/` as separate
US Letter PDFs. Nothing touches the network; fonts come from your own system.

```bash
python3 build.py --only club-charter reminder-card   # just these two
python3 build.py --out /tmp/mine                      # different output folder
```

## Tests

Every sheet is checked to build — valid PDF, exactly one page, correct US
Letter size, expected text present, no branding, no personal data, no
external URLs:

```bash
pip install weasyprint pypdf pytest
python3 -m pytest tests/ -v
```

## Make it yours

The sources are plain HTML + one shared stylesheet. Edit text in
`src/*.html`, restyle in `src/shared.css`, re-run `python3 build.py`.
Changing the page size or adding your club's own house rules takes about
five minutes and one coffee.

## Facilitation tips, quickly

- Open every meeting with a one-sentence check-in — everyone's voice, in the air, at once.
- Ask easy questions together first, disagreements with page numbers second.
- Count to three before filling silence. Quiet moments are thinking moments.
- Save the last ten minutes: next pick, next host, a favorite passage — goodnight.

## Credits

Built and maintained by **Asdale Dynamics, LLC** as part of its
beginner-friendly, plain-English tools collection. Free to use at home,
at your library, and everywhere the snacks live. Licensed under the
MIT License (see `LICENSE`).
