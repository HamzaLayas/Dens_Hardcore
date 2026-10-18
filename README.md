# Den's Hardcore

A Valheim mod by **SterbenDen**.

[Download the install ZIP](https://github.com/HamzaLayas/Dens_Hardcore/releases/download/v1.2.1/Dens_Hardcore-1.2.1.zip)

Keep the Hardcore challenge with recoverable graves, reduced skill loss, and a map shared through Cartography Tables. Choose each feature through Valheim's existing world modifiers.

Install **BepInEx 5** and the same version of Den's Hardcore on the server and every player's PC. Single-player is supported too. A modded server rejects players who are missing the required compatible mod.

## Install or update

1. Close Valheim and stop the server. Back up your world before updating mods.
2. Install [BepInExPack Valheim 5.4.2351](https://valheim.hexium.gg/mods/denikson/BepInExPack_Valheim).
3. When upgrading, remove the old `CartographyMap.dll` and `CartographyMap.Core.dll` copies from `BepInEx/plugins/CartographyMap/` and any other plugin folders. Keep your configuration, saved table maps, and other mod data.
4. Extract `Dens_Hardcore-1.2.1.zip` into the Valheim game folder and, for multiplayer, the dedicated-server folder. Replace the existing Den's Hardcore DLLs; keep only one copy of each.
5. Check the world's modifiers, then restart the world/server after changing options or updating.

The install contains only these two mod files:

```text
BepInEx/plugins/Dens_Hardcore/Dens_Hardcore.dll
BepInEx/plugins/Dens_Hardcore/Dens_Hardcore.Core.dll
```

The existing BepInEx configuration filename and saved-map data are retained. Do not delete your configuration or the saved data in the `CartographyMap` cache folder when removing the old DLLs.

## World modifiers

The host chooses the following independent options in **World modifiers**. The mod uses the game's existing controls; it does not add extra checkboxes.

| Control | What it does |
| --- | --- |
| **Death penalty → Hardcore** | By default, carried items go into a recoverable grave, each death reduces current skill levels by **5%** instead of resetting them, and Corpse Run and No skill drain are disabled. Level 50 becomes 47.5. The host can adjust these rules in BepInEx. Other death-penalty choices keep their vanilla behavior. |
| **Cartography Table map** | Replaces the game's **No map** checkbox. Check it so **M** opens your last saved table map. Exploration keeps recording for your next table update. The minimap, player marker, and ship marker are hidden; the map does not follow your character. Uncheck it to use the normal vanilla map. |

You can choose **Hardcore** under Death penalty without selecting the complete Hardcore preset. The two options work independently. Selecting the regular **Hardcore** preset keeps its other values and its Hardcore label; the mod does not change the preset's saved settings.

Dedicated servers use the same native world settings: `-modifier deathpenalty hardcore` selects the custom Hardcore death behavior, and `-setkey nomap` selects the Cartography Table map. Restart the server after changing its world settings.

## BepInEx configuration

The mod uses `BepInEx/config/com.sterbenden.cartographymap.cfg`. These are the defaults:

```ini
[Replacements]
Use custom Hardcore death penalty = true
Use table map for No map = true

[Gameplay]
Skill loss percent = 5
Keep carried items in grave = true
Remove Corpse Run = true
Remove No skill drain = true
Default sign pin icon = Fire

[Client]
Show saved-map banner = true
```

`[Replacements]` controls whether the mod replaces the matching vanilla behavior. It does not select a world's death penalty or map option; use **World modifiers** or the dedicated-server settings above for those choices.

The host can tune the following gameplay settings:

| Setting | Effect |
| --- | --- |
| **Skill loss percent** | Any value from **0 to 100**, including decimals. **0** keeps skills; **100** deliberately resets them. The default **5** removes 5% of each current skill level. |
| **Keep carried items in grave** | `true` preserves carried items in a recoverable grave. `false` restores vanilla Hardcore item loss. |
| **Remove Corpse Run** | `true` removes the recovery buff. `false` allows the normal Corpse Run buff. |
| **Remove No skill drain** | `true` removes protection against skill loss from repeated deaths. `false` restores vanilla No skill drain and its cooldown protection; deaths outside that protection still use the configured skill-loss percentage. |
| **Default sign pin icon** | Choose **Fire**, **Base**, **Hammer**, **Dot**, or **Portal** for newly pinned signs. Existing pins keep their chosen icons. |

The death settings apply only while the custom Hardcore death penalty is active. The sign-icon default applies when using Cartography Table maps. Defaults keep the mod's usual behavior.

Set a replacement to `false` in the world's section to restore that control's vanilla behavior. With `Use table map for No map = false`, the checkbox returns to **No map** and disables the map when checked. With `Use custom Hardcore death penalty = false`, the Hardcore death penalty again uses vanilla item-loss rules and the full skill reset.

Select or start a world once to create its `[World <world ID>]` section with the replacement and gameplay entries. Edit that section for an existing world. `[Replacements]` and `[Gameplay]` supply initial values only for world entries that have not been saved; changing them does not overwrite saved per-world values. Stop the world/server before editing and restart afterward. The host or server controls these settings; joining players cannot override them. No configuration-manager mod is required.

`[Client]` is local to each player's PC. Set `Show saved-map banner = false` to hide the message above the saved map. This does not change the map, reveal exploration, or restore the minimap or player markers.

When upgrading, an existing **Hardcore** death-penalty selection or checked **No map** setting activates its Den's Hardcore replacement by default. To keep vanilla behavior, disable the corresponding replacement in the world's configuration section. The old extra-checkbox settings no longer choose the modes or disable these replacements. Existing configuration, saved table maps, and sign pins are retained.

## Cartography Tables and sign pins

- Read a Cartography Table to save its map for viewing with **M**. Before reading a valid table, the view is unexplored.
- Use **Record discoveries** to save your exploration and pending sign-pin changes to that table. Other players receive the update when they read it.
- Normal sign interaction still edits its text. Use the sign's alternate interaction to open **Map Pin Options**; follow the displayed keyboard or controller prompt.
- Enable a sign as a pin, choose Fire, Base, Hammer, Dot, or Portal, cross it off, or remove its pin. The sign text is the pin name. Sign and ward permissions still apply.
- Sign changes reach the saved map only after recording at a table. Reading alone does not publish pending changes. Each table keeps its own saved map.
- Pan and zoom the saved map normally. Direct map-pin editing is unavailable; edit sign pins at their signs.

Use this mod's sign-pin controls for table maps. AutoPinSigns is not required; its live-map overlay is a separate feature and can produce overlapping pins if both mods manage the same sign.

## Removing the mod or playing without it

Back up your world and stop the game/server before removing mods. To uninstall, remove `BepInEx/plugins/Dens_Hardcore/` from the server and every client, along with any old copies of the two mod DLLs. Keep your configuration and saved map data if you plan to reinstall.

Without Den's Hardcore, the world's saved vanilla settings take effect. **Hardcore death penalty restores vanilla item deletion and the full skill reset. A checked Cartography Table map is stored as No map, so the map becomes unavailable.** An unchecked map option keeps the normal vanilla map. Existing vanilla signs, tables, and graves remain usable.

## Q&A

**Which GitHub download should I use?**

Download `Dens_Hardcore-1.2.1.zip` to install the mod. It contains only the two required DLLs in their install folder. GitHub's automatic **Source code** archives contain the player guide and accompanying documentation and icon; use the install ZIP to play.

**Does everyone need to install the mod?**

Yes. Install BepInEx and the same Den's Hardcore version on the server and every player's PC. If you cannot connect, check both versions and restart after updating. Single-player works too.

**Do I have to use the complete Hardcore preset?**

No. Choose **Hardcore** under **Death penalty** to use the configured death rules: recoverable graves and 5% skill loss by default. Choose **Cartography Table map** separately. Other death-penalty choices keep their normal behavior.

**Why are there no extra mod checkboxes?**

The mod uses the existing death-penalty control and replaces **No map** with **Cartography Table map**. Check the map option for the saved table view, or uncheck it for the normal vanilla map.

**Where is the BepInEx configuration?**

Open `BepInEx/config/com.sterbenden.cartographymap.cfg`. The host edits `[World <world ID>]` to tune an existing world's skill loss, grave items, death buffs, and default sign icon. `[Replacements]` and `[Gameplay]` supply initial defaults and do not overwrite saved world entries. Native world modifiers select the modes. Stop the world/server before editing and restart afterward. Players can independently hide the saved-map banner through `[Client]`.

**Why is my map blank, and where is the minimap?**

With **Cartography Table map** checked, read a table to get a saved map. The minimap and player/ship markers are hidden. Uncheck the option for the normal vanilla map. If the table-map replacement is disabled in BepInEx, the checkbox instead uses vanilla **No map** behavior.

**Does the saved map reveal land as I explore?**

No. Your exploration is recorded for your next visit to a table. Use **Record discoveries**, then read the updated table. Other players receive it when they read that table.

**Why hasn't my sign pin changed on the map?**

Sign pins, icon changes, and crossed-off states reach a table when you use **Record discoveries**. Read the updated table to refresh your saved view. Changes do not appear immediately, and reading alone does not publish them.

**What happens to skills when I die?**

By default, the custom Hardcore death penalty reduces each current skill level by **5%** instead of resetting it: level 50 becomes 47.5. Items remain in a recoverable grave, and both death buffs are removed, so another death applies the reduction again. The host can change the percentage from **0** (keep skills) to **100** (full reset), choose vanilla item loss, or retain either buff. Keeping No skill drain restores its temporary protection against repeated skill loss. Disabling the death replacement restores the full vanilla Hardcore death penalty.

**Why do I see two copies or an older version after updating?**

Remove the old `CartographyMap.dll` and `CartographyMap.Core.dll` plugin copies before installing. Keep only `Dens_Hardcore.dll` and `Dens_Hardcore.Core.dll` in `BepInEx/plugins/Dens_Hardcore/`. Keep your configuration and saved map data.

**What happens if the mod is missing after an update?**

The saved vanilla world settings resume. Hardcore death penalty restores item deletion and the full skill reset; a checked table-map option becomes vanilla **No map**. Keep a world backup and matching mod installations on the server and every client when you want the replacements active.

## Credits

Den's Hardcore is Copyright (c) 2026 SterbenDen and is licensed under the [MIT License](LICENSE).

The Corpse Run icon is Valheim game artwork owned by Iron Gate AB. It is not covered by this repository's MIT license. Den's Hardcore is a community mod and is not affiliated with Iron Gate AB.

Source: [Valheim Wiki Corpse Run icon](https://static.wikia.nocookie.net/valheim/images/b/b2/CorpseRun.png?format=original). The original transparent artwork is enlarged to meet the package's 256 × 256 icon requirement.

[Downloads](https://github.com/HamzaLayas/Dens_Hardcore/releases) · [Report a problem](https://github.com/HamzaLayas/Dens_Hardcore/issues)
