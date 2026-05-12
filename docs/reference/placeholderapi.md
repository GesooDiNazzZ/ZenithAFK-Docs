# PlaceholderAPI

ZenithAFK provides full PlaceholderAPI integration. No additional expansion is needed — placeholders are registered automatically when PlaceholderAPI is present.

## Placeholders

| Placeholder | Description |
|---|---|
| `%zenithafk_prefix%` | AFK prefix (soft or hard variant) |
| `%zenithafk_suffix%` | AFK suffix |
| `%zenithafk_isafk%` | `true`/`false` (customizable text) |
| `%zenithafk_time%` | Total AFK time (formatted) |
| `%zenithafk_active_playtime%` | Active (non-AFK) playtime |
| `%zenithafk_playtime%` | Total playtime |
| `%zenithafk_playtime_raw%` | Raw playtime in milliseconds |
| `%zenithafk_zone%` | Current zone name |
| `%zenithafk_zone_players%` | Number of players in current zone |
| `%zenithafk_top_name_N%` | Playtime leaderboard — name at rank N |
| `%zenithafk_top_time_N%` | Playtime leaderboard — time at rank N |
| `%zenithafk_top_time_raw_N%` | Playtime leaderboard — raw ms at rank N |

Replace `N` with a number (1, 2, 3, ...) for leaderboard entries.

## Customization

All placeholder outputs are customizable via `plugins/ZenithAFK/placeholders.yml`:

```yaml
prefix:
  soft-afk: "&7[AFK]"
  hard-afk: "&c[IDLE]"
suffix:
  soft-afk: ""
  hard-afk: ""
isafk:
  true: "&7AFK"
  false: "&aOnline"
```

## Usage Examples

### TAB List

Show AFK status in player list:

```
%zenithafk_prefix% %player_name%
```

### Scoreboard

Display time in current zone:

```
Zone: %zenithafk_zone%
Next reward: %zenithafk_time%
```

### Chat Format

```yaml
format: "%zenithafk_prefix% %player_name% &7» &f%message%"
```

### Leaderboard

Top 3 players in a scoreboard or sign:

```
1. %zenithafk_top_name_1% — %zenithafk_top_time_1%
2. %zenithafk_top_name_2% — %zenithafk_top_time_2%
3. %zenithafk_top_name_3% — %zenithafk_top_time_3%
```