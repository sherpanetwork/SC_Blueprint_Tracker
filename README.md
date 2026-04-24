# Star Citizen Local Tools

Simple, browser-based tools for working with *Star Citizen* `.ini` files.

These tools are designed to help you:
- Track blueprint ownership
- Prioritize ships
- Modify `.ini` files without manual editing

Everything runs locally in your browser. No build step, server, or package install is required.

---

## Quick Start

1. Download or open one of the HTML tools from this repo  
2. Open it in your browser (double-click the file)  
3. Upload your `.ini` files  
4. Make your changes  
5. Download the updated file  

That’s it.

---

## Tools Included

### Blueprint Tracker

Use `blueprint-owned-tool.html` to extract blueprint names from `contracts.ini`, mark the ones you own, and apply that status to matching blueprint lines in `global.ini`.

**Features:**
- Parses bullet-list blueprint names that appear after `<EM4>Potential Blueprints</EM4>` in mission descriptions
- Displays a checklist of all available blueprints
- Searches and filters the blueprint checklist
- Selects or deselects all currently visible blueprints
- Imports/exports your owned list as `blueprintsOwned.txt`
- Applies `Owned: - Blueprint Name` to matching bullet lines in `global.ini`
- Preserves the rest of `global.ini` as uploaded

**Workflow:**
1. Upload `contracts.ini`
2. Select owned blueprints
3. (Optional) import or export `blueprintsOwned.txt`
4. Upload `global.ini`
5. Apply changes and download updated file

---

### Ship Priority Tool

Use `ship-priority-tool.html` to search, select, and rank ships from `global.ini`, then rewrite matching vehicle-name lines with priority numbering.

**Features:**
- Extracts `vehicle_Name*` entries from `global.ini`, excluding `_short` entries
- Removes existing numeric prefixes while building the ship list
- Searches and filters by ship name or localization key
- Builds a ranked priority list with Add, Move Up, Move Down, and Remove controls
- Saves/loads rankings as `shipSorting.txt`
- Applies numbering like:
  ```
  vehicle_NameRSI_Polaris=1. RSI Polaris
  ```
- Preserves unranked lines and non-matching file content

**Workflow:**
1. Upload `global.ini`
2. Search and add ships to your priority list
3. Reorder with Move Up and Move Down
4. (Optional) save or load `shipSorting.txt`
5. Apply changes and download updated file

---

## Required Files

These tools rely on `.ini` files generated from community tools:

- `contracts.ini` → Used for blueprint extraction  
- `global.ini` → Used for applying blueprint ownership and ship sorting  

---

## Credits / Data Sources

This project would not be possible without the community tools that provide access to game data:

- **Contracts data (contracts.ini):**  
  https://github.com/MrKraken/StarStrings  

- **Global localization data (global.ini):**  
  https://github.com/StelardActek/sc-localizer  

Full credit goes to the maintainers of these repositories for their work.

---

## Disclaimer

This is a **fan-made project** and is not affiliated with, endorsed by, or sponsored by **Cloud Imperium Games (CIG)**, **Roberts Space Industries (RSI)**, or any related companies.

Star Citizen®, Squadron 42®, Roberts Space Industries®, and all related names and assets are the property of their respective owners. This project simply works with publicly available data from community tools and repositories.

This tool is provided **as-is**, with no guarantees. It may break, produce unexpected results, or stop working as the game/data changes. Use it at your own risk and always back up your files before making changes.

---

## Notes

- Files are processed locally—nothing is uploaded anywhere
- The downloaded result is created in the browser from the file you uploaded
- Blueprint matching allows whitespace differences inside a blueprint name, but the blueprint text still needs to match
- Ship priority matching is based on the `vehicle_Name*` localization key
- Always keep backups of your original `.ini` files

---

## License

This project is licensed under the MIT License. See `LICENSE` for details.
