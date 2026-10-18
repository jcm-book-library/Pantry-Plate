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

## How it connects
The data lives in the Google Sheet "Pantry & Plate" (`1CwGKMFKzxrI1DOm0SIUx-vn7lvu5hQb1wXZzB3pDny8`). This browser keeps a cache (`localStorage`, key `pp-data-v1`) so the app opens instantly and works offline, and sends changes to the sheet a moment after each edit.
- **Inside claude.ai:** it uses the Google Sheets connector.
- **On GitHub Pages:** it uses Google sign-in, with the OAuth Client ID saved in the browser (`mbl_config`, shared with Jackets & Manuscripts, so if that app is already set up on this site there is nothing to paste). The Client ID's Google Cloud project must list `https://jcm-book-library.github.io` under Authorized JavaScript origins. Sign-in lasts about an hour. After that, press **Connect** again.
- **Anywhere else:** it saves on the device only.

The first time it connects to an empty sheet, it fills the sheet with what is on the device (the starter set or your own items). After that the sheet wins, except for edits that haven't been sent yet. It refreshes when you come back to the page after a couple of minutes, or when you press **Refresh**.

| Tab | Columns |
|---|---|
| Pantry | ID, Item, Amount, Kept in, Level, Aisle, Use by, Restock, Example, Deleted, Updated |
| Recipes | ID, Recipe, Serves, Time, Tags, Ingredients, Method, Source, Base meal, Favourite, Times cooked, Last cooked, Added, Deleted, Updated |
| Shopping | ID, Item, Aisle, Note, Bought, Deleted, Updated |
| App Settings | Key, Value (the "cupboard picks" row holds the Clear the cupboard picks) |

Removed items are marked, not deleted: the app sets Deleted to TRUE and hides the row, so nothing is lost and row numbers are never reused. Ingredients and method steps are one per line inside a cell. "Start again from the starter set" marks every old row as deleted and adds the new ones.

## Ideas for later
- A weekly meal plan that builds the shopping list.
- Import straight from a link (needs a small server or the claude.ai connector, because recipe sites block direct fetches).
- Ask Claude for suggestions from the claude.ai version.
- Barcode or receipt scanning to fill the pantry.
