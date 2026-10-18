# Working on Pantry & Plate

## Use usage credits well: orchestrate across models
The owner wants work split across models so the strongest model is spent only where it adds value.

- **Lead session (strongest model):** plan, write the spec, make design and data-model decisions, review diffs, and handle tricky logic (sheet sync, conflict rules, the AU converter).
- **Subagents on a cheaper model (Sonnet):** implement a spec that is already written, move or refactor code, write tests, add recipes or reference data, and fix small bugs.
- **Subagents on the cheapest model (Haiku):** searches, file sweeps, reading logs, renames and other mechanical edits.
- Give each subagent a self-contained brief (files, the exact change, how to check it) so it doesn't re-read the whole repo. Ask for a short result back, not file dumps.
- Don't fan out agents for a job one agent can do in a few steps. Running more agents only pays off when the parts are truly independent.
- Say in the reply which parts were delegated, and to which model.

## Project basics
- `app.html` is the source. Rebuild `index.html` with `python3 tools/build-pages.py` after every change, and commit both.
- The look is shared with Jackets & Manuscripts (`jcm-book-library/my-book-library`): Proton Seasons tokens, Atkinson Hyperlegible + Figtree, dark only.
- Data: Google Sheet "Pantry & Plate" (`1CwGKMFKzxrI1DOm0SIUx-vn7lvu5hQb1wXZzB3pDny8`). The browser copy (`localStorage` key `pp-data-v1`) is a cache.
- Australian English and Australian measures throughout (20ml tablespoon, 250ml cup, °C with fan-forced).
