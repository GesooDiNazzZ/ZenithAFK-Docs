# Playtime System

ZenithAFK includes a **built-in playtime tracking** system — no external plugins needed.

## Commands

| Command | Permission | Description |
|---|---|---|
| `/playtime [player]` | `zenithafk.playtime` | View your own or another player's playtime |
| `/playtimetop` | `zenithafk.playtimetop` | View the playtime leaderboard |

## Granular Control

Configure exactly what counts toward playtime:

```yaml
playtime:
  enabled: true
  count-during-soft-afk: true    # Count time in AFK zones
  count-during-hard-afk: false   # Count time while fully idle
  format: "formatted"             # formatted, short, or seconds
```

| Setting | Effect |
|---|---|
| `count-during-soft-afk: true` | Time spent in AFK zones counts toward playtime |
| `count-during-hard-afk: false` | Time spent fully idle does **not** count |

## Display Formats

| Format | Example |
|---|---|
| `formatted` | `142h 30m 15s` |
| `short` | `20m` |
| `seconds` | `1215` |

## Per-Zone Tracking

ZenithAFK tracks how long each player spends in **each zone** individually. View zone-specific breakdowns with:

```
/zafk stats [player]
```

This shows:

- Total playtime (active + AFK)
- Active playtime only
- Total AFK time
- Time per zone
- Current AFK state (NONE / SOFT / HARD)
- Current zone name

## Leaderboard

`/playtimetop` shows the top players ranked by playtime. The number of entries is configurable:

```yaml
playtime:
  leaderboard-limit: 10
```

## MySQL Sync

When using MySQL storage, playtime data is synchronized across servers. See [Multi-Server Sync](multi-server.md) for details.