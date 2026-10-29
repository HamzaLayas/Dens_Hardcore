# Changelog

## 1.4.0

- With the world's **No boss portals** modifier on (Portals → Hard), a boss summoned at an altar now disappears once no player has had its area loaded for 60 seconds, for example after everyone dies and respawns at the world spawn. Its portal block is released so portals work again, and every player sees a message. Fighting or kiting the boss nearby never removes it.
- The offering is not returned. Bosses that a location places itself, such as the Seeker Queen guarding her citadel, and bosses summoned before 1.4.0 are never removed.
- Hosts can change the wait with `Abandoned boss grace seconds` (0 to 600, default 60) or turn the rule off with `Despawn abandoned bosses = false` in a world's section.
- Abandoned-boss despawning is adapted from BossDespawn by Frogger, used under the MIT License.
- Versions before 1.4.0 cannot join 1.4.0 worlds, and 1.4.0 cannot join worlds running an earlier version.
