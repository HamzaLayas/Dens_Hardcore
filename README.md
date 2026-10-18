# Den's Hardcore

A Valheim mod by **SterbenDen**.

Keep the Hardcore challenge with optional recoverable graves and a map shared through Cartography Tables.

Install **BepInEx 5** and the same version of Den's Hardcore on the server and every player's PC. Single-player is supported too. A modded server rejects players who are missing the required compatible mod.

## Install or update

1. Close Valheim and stop the server.
2. Install [BepInExPack Valheim 5.4.2351](https://valheim.hexium.gg/mods/denikson/BepInExPack_Valheim).
3. Extract `Dens_Hardcore-1.0.0.zip` into the Valheim game folder and, for multiplayer, the dedicated-server folder.
4. Replace any older Cartography Map installation. Keep only one copy of each mod DLL.
5. Start the world again after changing its options or updating the mod.

Both files belong in `BepInEx/plugins/CartographyMap/`:

```text
CartographyMap.dll
CartographyMap.Core.dll
```

The folder and DLL names stay the same when upgrading from Den's Cartography Map. Your saved table-map cache is retained.

## World options

The host chooses two independent options in **World modifiers**. Both require explicit selection and take effect when the world starts.

| Option | What it does |
| --- | --- |
| **Hardcore grave protection** | On a Hardcore world, carried items go into a recoverable grave. Hardcore skill penalties remain. Corpse Run and No skill drain are disabled, including protection against skill loss from repeated deaths. |
| **Cartography Table map** | **M** opens your last saved table map. Exploration continues recording for your next table update. The minimap, player marker, and ship marker are hidden; the map does not follow your character. |

Grave protection requires a world using the regular **Hardcore** preset. The options keep its vanilla Hardcore settings. Grave protection does not grant map access by itself. When the table-map option is off, the world's normal map rules apply; Hardcore has no map.

## BepInEx configuration

The mod creates `BepInEx/config/com.sterbenden.cartographymap.cfg`. Existing settings are imported automatically when upgrading, and your saved table maps and sign pins are retained. After selecting or starting a world, its `[World <world ID>]` section contains both options:

```ini
Hardcore grave protection = false
Cartography Table map = false
```

Stop the world/server, edit the values in its generated section, and restart. Set either value to `true` to enable it. The world-modifier checkboxes save to these same entries. This works for single-player, hosted games, and dedicated servers; joining players use the host's settings. Grave protection still requires the regular Hardcore preset.

The `[Defaults]` section contains the same options, initially `false`. It supplies initial choices only for worlds without saved mod settings. It never replaces saved per-world choices. No additional configuration-manager mod is required.

## Cartography Tables and sign pins

- Read a Cartography Table to save its map for viewing with **M**. Before reading a valid table, the view is unexplored.
- Use **Record discoveries** to save your exploration and pending sign-pin changes to that table. Other players receive the update when they read it.
- Normal sign interaction still edits its text. Use the sign's alternate interaction to open **Map Pin Options**; follow the displayed keyboard or controller prompt.
- Enable a sign as a pin, choose Fire, Base, Hammer, Dot, or Portal, cross it off, or remove its pin. The sign text is the pin name. Sign and ward permissions still apply.
- Sign changes reach the saved map only after recording at a table. Reading alone does not publish pending changes. Each table keeps its own saved map.
- Pan and zoom the saved map normally. Direct map-pin editing is unavailable; edit sign pins at their signs.

Use this mod's sign-pin controls for table maps. AutoPinSigns is not required; its live-map overlay is a separate feature and can produce overlapping pins if both mods manage the same sign.

## Removing the mod or updating without it

Back up your world and stop the game/server before removing or updating mods. To uninstall, remove `BepInEx/plugins/CartographyMap/` from the server and every client.

When Den's Hardcore is absent, the world runs its regular vanilla rules. **On Hardcore, normal item deletion on death returns, grave protection is inactive, and the map is disabled.** Existing vanilla signs, tables, and graves remain usable. Reinstall the compatible mod on server and clients to use its saved options again.

## Q&A

**Does everyone need to install the mod?**

Yes. Install BepInEx and a compatible version of Den's Hardcore on the server and every player's PC. If you cannot connect, check both versions and restart after updating. Single-player works too.

**Do I have to use Hardcore?**

Hardcore grave protection requires the regular Hardcore preset. The Cartography Table map is a separate option and can be used without grave protection.

**Where is the BepInEx configuration?**

Open `BepInEx/config/com.sterbenden.cartographymap.cfg`. Select or start the world once to create its `[World <world ID>]` section, then stop the world/server before editing and restart afterward. The host or server controls these settings; a joining player's configuration cannot override them. `[Defaults]` supplies initial choices for worlds without saved mod settings and never replaces their saved choices.

**Why is my map blank, and where is the minimap?**

With Cartography Table map enabled, you must read a table to get a saved map. The minimap and player/ship markers are hidden. If the option is disabled, vanilla rules apply, so a Hardcore world has no map.

**Does the saved map reveal land as I explore?**

No. Your exploration is recorded for your next visit to a table. Use **Record discoveries**, then read the updated table. Other players receive it when they read that table.

**Why hasn't my sign pin changed on the map?**

Sign pins, icon changes, and crossed-off states reach a table when you use **Record discoveries**. Read the updated table to refresh your saved view. Changes do not appear immediately, and reading alone does not publish them.

**Does grave protection remove Hardcore's other penalties?**

No. It preserves carried items in a grave, but keeps Hardcore skill penalties. It also removes Corpse Run and No skill drain, so another death can immediately cause more skill loss.

**What happens if the mod is missing after an update?**

The world uses its normal vanilla settings. On Hardcore, item deletion on death returns and the map is disabled. Back up your world and keep the mod installed on the server and every client when you want its options active.

[Downloads](https://github.com/HamzaLayas/Dens_Hardcore/releases) · [Report a problem](https://github.com/HamzaLayas/Dens_Hardcore/issues)
