# Windrose Character Editor

A save-game editor for [Windrose](https://store.steampowered.com/app/3349750/Windrose/) (Early Access). Edit your character's level, XP, stats, talents, inventory, and ships — without touching the save files by hand.

[![Latest release](https://img.shields.io/github/v/release/Chris971991/windrose-character-editor-releases?style=flat-square)](https://github.com/Chris971991/windrose-character-editor-releases/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/Chris971991/windrose-character-editor-releases/total?style=flat-square)](https://github.com/Chris971991/windrose-character-editor-releases/releases/latest)

---

## Quick install

Download from the [latest release](https://github.com/Chris971991/windrose-character-editor-releases/releases/latest):

| File | What it is |
|---|---|
| `Windrose-Character-Editor-X.Y.Z-x64.exe` | **Installer** (recommended) — install wizard, Start Menu + desktop shortcuts, sets up auto-updates. Per-user install, no admin required. |
| `Windrose-Character-Editor-X.Y.Z-portable-x64.exe` | **Portable** — single .exe. Run from anywhere (incl. USB drives), no install. |

> **First-run SmartScreen warning**: Windows will say *"Windows protected your PC"* the first time. Click **More info** → **Run anyway**. The app is currently unsigned; this warning is normal for early indie releases.

You don't need Node.js, Python, .NET, or any modding tools. Just Windrose installed via Steam.

---

## What it can do

- **Character**: rename, change level + XP, edit all 6 stats (Strength / Agility / Precision / Mastery / Vitality / Endurance), assign points across the talent tree
- **Inventory**: swap any item, change quantities, change equipment level (1–max quality), set up the action bar and main inventory exactly how you want
- **Ships**: rename ships, swap hulls, edit cannons / hull plate / boarding crew / sails / flags / hull colors, manage cargo and consumables, set the flagship, repair damaged ships, add new ships to your fleet, delete ships you don't want
- **Live derived stats**: as you edit, the right-side panel recalculates Health, Stamina, Defence Power, Critical Hit Chance, weapon damage, etc. using the game's actual PAK-derived math — so you can see the real impact of every change before you save
- **Safety**: refuses to write while the game is running, makes an automatic backup before every save, restorable from a built-in backups menu

---

## Getting started

1. **Close Windrose.** The editor refuses to write while the game has the save file open. The header shows a yellow *"Game running — close to save"* pill when this is the case.
2. **Open the editor.** It auto-detects your save in `%LOCALAPPDATA%\R5\Saved\SaveProfiles\<your-Steam-ID>\…`. The full path appears below the header so you can confirm.
3. **Make an edit.** Try something small first — bump your level by 1, or add a stat point — and verify it shows up in-game before doing anything bigger.
4. **Click Save.** The header turns the Save button gold when you have unsaved changes. The editor takes a backup automatically before writing, then commits.
5. **Launch Windrose** and confirm the changes landed.

If the server rejects your edits when you connect to a guild server, scope shifts to single-player or your-own-server use only.

---

## Header

The top bar holds the bread-and-butter controls.

| Element | What it does |
|---|---|
| Windrose logo + **Character Editor** title + version chip | Quick visual confirmation of which version you're running |
| **Character name** input | Rename your character (commits on Save) |
| **Update pill** | Appears when a newer release is available (Checking → Downloading → "vX.Y.Z ready · Restart"). Click *Restart* to apply. |
| **Catalog update pill** | Appears when fresher game-data is available between editor releases. Click to download — no app restart needed. |
| **Lock indicator** | Green *"Save unlocked"* when the game is closed; amber *"Game running — close to save"* when it isn't |
| **Backups** | Opens the backups browser (see below) |
| **Reload** ⟳ | Re-reads the save from disk, discards any unsaved edits |
| **Reset** | Clears unsaved edits without re-reading from disk |
| **Save** | Writes pending edits to disk. Disabled while the game is running or there's nothing to save. |

Below the buttons: full save path, account ID, save version, blob size, and your current recipe-unlock counts — at-a-glance reference info.

---

## Character tab

The bigger of the two tabs. Three-column layout.

### Left column — Equipment

Click any slot to open the **Item Picker** (see below). Slots are organised:

- **Armor** (5): Head, Torso, Hands, Legs, Boots
- **Accessories** (3): Necklace, Ring, Backpack
- **Ammo** (2): Projectiles, Gunpowder

Each slot shows the item's icon, name, count badge if stacked, and a small gold dot when you have unsaved changes. Hover for a full info popover. The **×** in the top corner clears the slot.

### Middle column — Talent radial + Action bar + Main inventory

**Talent radial** — the big circular tree at the top, modeled after the in-game version. Four branches (Fencer / Crusher / Marksman / Toughguy) at 4 compass points.

- **Left-click** a talent dot to add a rank (capped at the talent's max, usually 3)
- **Right-click** a talent dot to remove a rank
- **Multi-perk talents** (the ones with a circular split): clicking a different perk switches your active perk to it at rank 1
- Branch totals are shown at each branch's centre — useful for tracking ring-2 / ring-3 requirements
- Locked talents (greyed out) need more points spent in the same branch first

**Action bar** (8 slots) — your hotbar. Holds consumables, potions, throwables, weapons.

**Main inventory** (32 slots) — everything else. Stack-able items (food, resources, ammo) show a count badge.

For any slot, click to swap, edit count, or change the item level (for equipment with quality tiers).

### Right column — Progression + Derived stats + Stats

**Progression** card

- Level rhomb showing current level, with XP fill rising as you approach the next threshold
- Level + XP number inputs (free-edit, no spending budget enforced)
- **Stat Points** and **Talent Points** spent / budget readouts

**Derived Stats** panel — live-computed from your character + talents + equipped gear, using the game's actual math from the PAK files. As you edit anything in the middle panel, these update instantly:

- **Vitals**: Health, Stamina, Stamina Recovery Rate, Defence Power, Max Posture
- **Combat**: Attack Power, Critical Hit Chance, Critical Damage Bonus, Crude / Slash / Pierce damage modifiers
- **Defence**: Stagger Defence, Max Corruption, Corruption Resist, Damage Resistance, etc.

A small **PAK · bundled / hot-patch** chip in the corner tells you which catalog source the values came from.

**Available Stat Points** — the 6 stats with `−` / `+` buttons. Free-edit; the editor doesn't enforce the in-game spending order.

---

## Ship tab

Switch via the *Character ⇄ Ship* tab pill at the top of the left column.

### Left column — Wharf (your fleet)

Two sections:

- **Docked** — ships that are deployed to islands in your world
- **Reserved & Sunken** — freshly-crafted ships, ships in storage, ships you've recovered from sinking

Each row shows the ship name, hull type, health, and badges for *Flagship* / *Aboard* / damage status. Click a row to load it for editing. Hover the pencil icon to rename inline.

**`+ Add ship`** opens a hull picker. Choose a hull, optionally name it, and the editor creates a fresh ship that lands in *Reserved & Sunken* — same state as if you'd just crafted one in the game's shipyard. The matching internal building entry is also created so the game treats it like a real ship.

**Repair All** appears whenever any ship has less than 100% HP. One click restores everyone.

Some ships can't be deleted from the editor: the starter Boat, your current flagship, and the ship you're currently sailing.

### Center / right — Ship detail

When a ship is selected:

- **Blueprint hero card** — large hull artwork, name (renameable), health bar, *Change hull* button, *Delete ship* button
- **Cannons & Hull** (4 slots): Big cannon, Small cannon, Hull plate, Boarding crew
- **Customization** (3 slots): Sails, Hull color, Flag (cosmetic — no level editing)
- **Consumables** (4 slots): Quick-use items the crew can deploy
- **Cargo Hold** (28 slots): general ship storage

All slots open the same Item Picker as the character side.

---

## Item Picker

The popup that appears when you click any slot. Same control across character and ship tabs.

**Left side** — what's currently in this slot

- Item icon, name, description (the in-game flavor text)
- **Item Level** slider (for items with quality tiers): drag from 1 to max, or use the Min / Max quick buttons
- **Quantity** slider (for stackable items): drag or type a number. Editor will warn if you go above the in-game stack cap.
- **Remove item** clears the slot
- **Done** commits your selection to your pending edits (still need to click **Save** in the header to actually write to disk)

**Right side** — compatible items

- Search bar (matches name, slug, or description)
- **Type** filter (All Types / Weapons / Tools / Food / Potions / Elixirs / Misc / Resources / Ammo) — only shows types relevant to the slot
- **Rarity** filter (Common / Uncommon / Rare / Epic / Legendary / Myth)
- 3-column grid of items. Hover any tile to see a full info popover with stats, effects, set bonuses, etc.

While the list loads, you'll see spinning loader tiles in the grid. The first time you open a picker per session takes a moment; after that it's instant.

---

## Backups

Click **Backups** in the header to open the browser.

Two sources of backups appear:

- **Editor** backups — automatic snapshots taken before every save the editor makes. Stored at `%LOCALAPPDATA%\R5\Saved\SaveProfiles\<SteamID>_Backups_Editor\<timestamp>\`.
- **Game** backups — Windrose's own auto-saves. Stored at `%LOCALAPPDATA%\R5\Saved\SaveProfiles\<SteamID>_Backups\`.

Each row shows the timestamp, source, size, and a **Restore** button. Click *Backup now* to take a manual snapshot at any time.

When you restore:

1. The editor takes a fresh *prerestore* backup of your current state first (so you can undo the undo)
2. Copies the chosen backup over your live save
3. The editor reloads from disk

Restore is disabled while the game is running.

---

## Auto-updates

The editor checks the GitHub release page on every launch.

- If you're on the latest version, the update pill stays hidden
- If a newer version is available, you'll see the update pill walk through *Checking… → Downloading vX.Y.Z (NN%)… → vX.Y.Z ready · Restart*
- Click **Restart** to apply — the editor closes, swaps in the new version, and relaunches automatically

The **catalog update pill** is independent of the editor version. When Windrose patches the game and a fresher set of stat curves is published, this pill appears so you can pull just the data without reinstalling. No restart needed — just click and reload.

---

## Safety

- **Game-lock detection**: the editor checks for the RocksDB `LOCK` file before any save. If Windrose has the save open, the Save button is disabled and the header shows a *"Game running — close to save"* warning.
- **Pre-save backup**: every save creates a timestamped copy of the entire RocksDB tree (Accounts + Players) before writing.
- **Round-trip self-check**: before applying edits, the editor's save layer parses the unmodified blob, re-serialises it, and bails if the bytes aren't identical. Catches parser bugs that would otherwise silently corrupt the save.
- **Field preservation**: the editor only mutates fields it understands. Polymorphic blobs, unknown nested arrays, and the persistent blackboard pass through untouched.
- **Equipment stack guard**: refuses to set count > 1 on equippable items (which use single-item slots) — prevents invalid stack states that would crash the game on next inventory open.
- **Asset-path validation**: every item path is checked against the game's actual asset manifest before saving. Invalid paths are rejected before they hit the disk.

---

## Troubleshooting

**Editor says "Game running — close to save"** — Windrose still has the save file open. Quit the game completely (check the system tray and Task Manager if it's still running in the background).

**Editor can't find my save** — Make sure you've launched Windrose at least once on this Windows account. The save lives at `%LOCALAPPDATA%\R5\Saved\SaveProfiles\`. If you've moved your Steam install or use a non-default save location, the editor's settings file at `%APPDATA%\windrose-character-editor\settings.json` lets you override the path.

**SmartScreen blocks the .exe** — Click **More info** → **Run anyway**. The app is unsigned for now (code-signing certificate is on the to-do list).

**Auto-update isn't working** — Check `%APPDATA%\windrose-character-editor\logs\main.log` for `[updater]` lines. The header pill should also show an error tooltip if the check fails. Failing that, just download the latest installer manually from the [release page](https://github.com/Chris971991/windrose-character-editor-releases/releases/latest) and run it over your existing install.

**The picker is slow to load the first time** — That's the per-item data hydration. Once loaded, it's instant for the rest of your session.

**Game rejects my edited character on a guild server** — The server may run its own progression validation. The editor is intended for single-player and your-own-server use; results on shared servers vary by server config.

**My in-game level shows 14 but the editor shows 15 (or vice versa)** — The save stores levels 0-indexed, the in-game UI is 1-indexed. The editor follows the in-game convention. So if the editor says level 15, that's what the game also shows.

---

## Compatibility

- **Game**: Windrose 0.10.0+ (Early Access)
- **OS**: Windows 10 / Windows 11 (64-bit)
- **Game install**: Steam (any Steam library location works — the editor finds it automatically)

---

## Privacy & disclaimer

- **No telemetry, analytics, or phone-home behaviour.** The editor only contacts GitHub for update checks and gaming.tools for item icon / cosmetic-string fetches. All saves are processed locally on your machine.
- **Single-player / your-own-server use is the intended scope.** Editing your character may be considered cheating by other players or admins on shared servers — use accordingly. Be courteous to your guild and ask first.
- **Be cautious with big edits.** Start small (level +1, or a single stat point) and confirm the change works in-game before scaling up. The editor's safety net is the auto-backup, not a guarantee.

---

## Bug reports & feature requests

Open an [issue on this repo](https://github.com/Chris971991/windrose-character-editor-releases/issues). Include:

- Editor version (visible next to the *Character Editor* title in the header)
- Windrose version (from your Steam library properties)
- What you were doing when it broke
- A copy of `%APPDATA%\windrose-character-editor\logs\main.log` if it's an auto-update or runtime error

---

## License

[MIT](./LICENSE).
