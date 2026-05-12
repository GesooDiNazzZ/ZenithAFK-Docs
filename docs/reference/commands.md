# Commands

All admin commands are under `/zenithafk` (alias: `/zafk`).

## Admin Commands

| Command | Description |
|---|---|
| `/zafk help` | Show the help menu |
| `/zafk wand` | Get the zone selection wand (Golden Axe) |
| `/zafk create <name>` | Create a new zone from current selection |
| `/zafk delete <zone>` | Delete an existing zone permanently |
| `/zafk redefine <zone>` | Resize a zone with current selection |
| `/zafk tp <zone>` | Teleport to a zone's center |
| `/zafk list` | List all zones with player counts |
| `/zafk info <zone>` | View zone details and settings |
| `/zafk stats [player]` | View AFK/playtime statistics |
| `/zafk edit <zone>` | Open the in-game GUI editor |
| `/zafk rewards <zone>` | Preview zone rewards (players); add rewards (admins) |
| `/zafk reload` | Reload configuration from disk |

## Player Commands

| Command | Description |
|---|---|
| `/playtime [player]` | View your own or another player's playtime |
| `/playtimetop` | View the playtime leaderboard |

## In-Game GUI Editor

The `/zafk edit <zone>` command opens a chest-based GUI where you can modify every zone setting without editing YAML:

- :gear: Reward interval & rolls per interval
- :busts_in_silhouette: Max players & permission gating
- :speech_balloon: Enter/leave messages
- :tv: Display settings for both Soft and Hard AFK states
- :moneybag: Streak configuration
- :triangular_flag: Enter conditions (playtime, level, permission)
- :shield: Anti-abuse settings (daily limit, auto-kick)
- :musical_note: Sound effects
- :gift: Reward management (add/remove)
- :arrows_counterclockwise: Zone reload button
- :truck: Teleport to center