# Changelog

## 1.3.0

- After dying with the custom Hardcore death penalty, respawn at the world spawn instead of your bed. Quitting during the death screen also returns you to the world spawn; joining a world is unchanged. Hosts can turn this off per world with `Respawn at world spawn`.
- On the Cartography Table map, all shallow and deep water now appears explored, so fog covers only unexplored land. Hosts can turn this off per world with `Show water as explored`.
- Hide the bed spawn marker on the saved table map while death respawns use the world spawn.
- Keep the world running when saved sign-pin data is damaged. The damaged file is kept beside the original name, a valid backup is restored when available, and the message names the file.
- Refuse to record at a Cartography Table while a sign update is still pending, and repair tables whose sign-pin update never arrived, so tables stay readable for everyone.
- Prevent unexpected logouts and dedicated-server shutdowns on Hardcore worlds when the game's world-options screen is unavailable.
- Versions before 1.3.0 cannot join 1.3.0 worlds, and 1.3.0 cannot join worlds running an earlier version.
