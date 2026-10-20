# Working on Pantry & Plate

**Read the house rules first:** [HOUSE-RULES.md](https://github.com/jcm-book-library/control-room/blob/main/HOUSE-RULES.md) in `control-room` (plain text: https://raw.githubusercontent.com/jcm-book-library/control-room/main/HOUSE-RULES.md). They cover Google Sheet safety, branches and pull requests into `main`, using cheaper models to save usage credits, and the build template. The notes below are this repo's own; where they are more specific, they win. The project charter is `project.json`.

Model use: see "Using models" in the house rules.
- **Lead session (strongest model):** plan, write the spec, make design and data-model decisions, review diffs, and handle tricky logic (sheet sync, conflict rules, the AU converter).

## Project basics
- `app.html` is the source. Rebuild `index.html` with `python3 tools/build-pages.py` after every change, and commit both.
- The look is shared with Jackets & Manuscripts (`jcm-book-library/my-book-library`): Proton Seasons tokens, Atkinson Hyperlegible + Figtree, dark only.
- Data: Google Sheet "Pantry & Plate" (`1CwGKMFKzxrI1DOm0SIUx-vn7lvu5hQb1wXZzB3pDny8`). The browser copy (`localStorage` key `pp-data-v1`) is a cache.
- Australian English and Australian measures throughout (20ml tablespoon, 250ml cup, °C with fan-forced).
