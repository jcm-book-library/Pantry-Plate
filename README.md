# Pantry & Plate

My kitchen app: what's in the pantry, what to cook tonight, the shopping list, and recipes in Australian measures. It uses the same Proton Seasons look as Jackets & Manuscripts (the accent colour changes with the month).

## What it does
| Tab | What it's for |
|---|---|
| Tonight | Recipes ranked by what you have, favourites and what needs using. Shows use-soon and running-low items. |
| Pantry | Fridge, pantry and freezer items with a Plenty / Low / Out level, an optional amount and use-by date. Items marked "Always restock" go on the list as soon as they run low. |
| Recipes | Six base meals to start, plus anything you add or import. Star favourites, scale serves, see what's missing, add the missing items to the list, and log "I cooked this". |
| Clear the cupboard | Pick what needs using up. You get flexible meal ideas (fried rice, frittata, cupboard pasta, soup, curry, fritters, quesadillas, noodles) built from your picks, plus saved recipes that use them and online search links. |
| Shopping | Grouped in supermarket aisle order. Ticked items go into the pantry as "Plenty" when you put them away. Copy the list as text to send it. |
| Import & convert | Paste a recipe from any site. It converts US/UK measures to AU (20ml tablespoons, grams for flour, sugar and butter, °F to °C with fan-forced, inches to cm) and swaps US words (cilantro → coriander, ground beef → beef mince, and so on). Every change is highlighted before you save. |

## Files
| File | What it is |
|---|---|
| `app.html` | The app source. Edit this. The same file is published as the claude.ai artifact. |
| `index.html` | Built from `app.html` for GitHub Pages. Rebuild it with `python3 tools/build-pages.py`. |
| `manifest.webmanifest`, `icons/` | Home-screen install and icons. |

## Where the data lives
Version 1 saves everything in the browser on the device you use (`localStorage`, key `pp-data-v1`). Phone and laptop don't share data yet. Use **Your data and backups** at the bottom of the page to copy a backup and restore it on another device.

## Ideas for later
- Sync through a Google Sheet ("Kitchen Tracker"), the same way Jackets & Manuscripts does, so phone and laptop share one pantry and list.
- A weekly meal plan that builds the shopping list.
- Import straight from a link (needs a small server or the claude.ai connector, because recipe sites block direct fetches).
- Ask Claude for suggestions from the claude.ai version.
- Barcode or receipt scanning to fill the pantry.
