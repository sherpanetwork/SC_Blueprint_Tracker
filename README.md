# SC_Tools: Star Citizen Local Tools

Simple, browser-based tools for working with *Star Citizen* `.ini` files.

These tools are designed to help you:
- Track blueprint ownership
- Prioritize ships
- Modify `.ini` files without manual editing

Everything runs locally in your browser. No build step, server, or package install is required.

---

## Quick Start

1. Download the repo, or download the specific `.html` tool you want to use  
2. Open the `.html` file in your browser (double-click the file)  
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
- Can build the checklist from `contracts.ini` or a `global.ini` with contract descriptions
- Displays a checklist of all available blueprints
- Searches and filters the blueprint checklist
- Selects or deselects all currently visible blueprints
- Imports/exports your owned list as `blueprintsOwned.txt`
- Loads existing `Owned: - Blueprint Name` markers from `global.ini` automatically
- Applies `Owned: - Blueprint Name` to matching bullet lines in `global.ini`
- Preserves the rest of `global.ini` as uploaded

**Workflow:**
1. Upload `contracts.ini`, or upload `global.ini` if it contains the blueprint contract descriptions
2. Select owned blueprints
3. (Optional) import or export `blueprintsOwned.txt`; already-marked blueprints in `global.ini` are loaded automatically
4. Upload `global.ini`
5. Apply changes and download updated file

---

### Ship Priority Tool

Use `ship-priority-tool.html` to search, select, and rank ships from `global.ini`, then rewrite matching vehicle-name lines with priority numbering.

**Features:**
- Extracts `vehicle_Name*` entries from `global.ini`, excluding `_short` entries
- Removes existing numeric prefixes while building the ship list
- Loads existing numbered ship names from `global.ini` into the priority list automatically
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
4. (Optional) save or load `shipSorting.txt`; already-numbered ships in `global.ini` are loaded automatically
5. Apply changes and download updated file

---

## Required Files

These tools rely on `.ini` files generated from community tools. Starter copies are included in this repo, but you can also use fresh files from the sources listed in Credits / Data Sources.

- `contracts.ini` → Used for blueprint extraction  
- `global.ini` → Used for applying blueprint ownership and ship sorting  
- `global_with_contracts.ini` → Useful for the Blueprint Tracker if you do not already have a modified `global.ini`
- `4.7.2_LIVE_global.ini` → Clean game localization file useful for the Ship Priority Tool

---

## How This Works

These tools use Star Citizen's community localization support. CIG allows the game to load a localized `global.ini` file from the `StarCitizen/LIVE/data/Localization/<language>/` folder, with the active language set in `user.cfg`.

Instead of translating the game into another language, these tools make small, targeted edits to English localization text. The Blueprint Tracker marks matching blueprint lines as owned, and the Ship Priority Tool adds ranking numbers to ship names. The game then reads the edited English `global.ini` through the same localization system.

You can read CIG's community localization instructions here:
https://robertsspaceindustries.com/spectrum/community/SC/forum/1/thread/star-citizen-community-localization-update

---

## Fan Project Notice

This is an unofficial Star Citizen fan tool, not affiliated with the Cloud Imperium group of companies. Content not authored by this project is property of its respective owners.

Official Star Citizen website: https://robertsspaceindustries.com/

These tools are free, community-made, and not intended for commercial use, paywalls, subscriptions, donations, fundraising, or any other paid access.

---

## Installing the Updated `global.ini`

After using either tool, download the updated `global.ini` and place it here:

```text
StarCitizen/
└── LIVE/
    ├── user.cfg
    └── data/
        └── Localization/
            └── english/
                └── global.ini
```

If you already have a `user.cfg` file, do not overwrite it. Open your existing `user.cfg` and add this line at the end:

```text
g_language = english
```

If you do not have a `user.cfg` file, create one in the `StarCitizen/LIVE/` folder root and add that same line.

Always keep a backup of your original `global.ini` before replacing it.

---

## Credits / Data Sources

Tool created by **SesGreenwood**. If these tools help you out, in-game praise is always appreciated.

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
