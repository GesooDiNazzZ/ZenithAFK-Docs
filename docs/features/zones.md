# AFK Zones

AFK zones are the core of ZenithAFK. Players standing inside a zone earn **periodic rewards** based on the zone's configuration.

## Creating Zones

```
/zafk wand          # Get the selection tool (Golden Axe)
/zafk create <name> # Create a zone from your selection
/zafk edit <zone>   # Open the in-game GUI editor
/zafk info <zone>   # View zone details and player count
```

## Zone Properties

Every zone has its own YAML file (`plugins/ZenithAFK/zones/<name>.yml`) with these settings:

| Property | Type | Default | Description |
|---|---|---|---|
| `reward-interval` | int | `180` | Seconds between reward rolls |
| `rolls-per-interval` | int | `1` | How many rewards to roll per interval |
| `max-players` | int | `-1` | Max players in zone (-1 = unlimited) |
| `permission` | string | `""` | Required permission to enter |
| `ip-limit` | int | `0` | Max accounts per IP (0 = disabled) |
| `session-time-limit` | int | `0` | Max minutes in zone per session (0 = unlimited) |
| `auto-kick-minutes` | int | `0` | Kick after X minutes AFK (0 = disabled) |
| `daily-reward-limit` | int | `0` | Max rewards per player per day (0 = unlimited) |
| `streak-interval-minutes` | int | `0` | Minutes between streak level-ups (0 = disabled) |
| `streak-max-level` | int | `5` | Maximum streak multiplier level |
| `redirection-grace-seconds` | int | `5` | Grace period after TP before anti-redirection kicks in |

## IP Limit

Prevent players from logging in with multiple accounts to farm rewards:

```yaml
ip-limit: 2  # Max 2 accounts per IP in this zone at once
```

Players with `zenithafk.bypass.iplimit` permission bypass this limit.

## Session Timer

Each player's time in a zone is tracked individually. The session timer counts up toward the next reward and can optionally reset after each reward:

```yaml
reset-timer-on-reward: true   # Reset countdown after each reward
```

## Enter / Leave Commands

Execute console commands when a player enters or leaves a zone:

```yaml
enter-commands:
  - "say %player% entered the AFK zone!"
leave-commands:
  - "effect give %player% speed 10 1"
```

Available placeholders: `%player%`, `%zone%`

## Enter Conditions

Restrict zone access based on player attributes:

```yaml
enter-conditions:
  min-playtime-minutes: 60    # Must have 1h+ total playtime
  min-level: 10                # Must be level 10+
  required-permission: ""      # Custom permission node
```

Players who don't meet the conditions see a configurable denial message.

## Region Management

```
/zafk redefine <zone>   # Resize zone boundaries with current selection
/zafk delete <zone>      # Delete a zone permanently
/zafk tp <zone>          # Teleport to zone center
```

The selection wand uses **WorldEdit-style positioning** — left-click for pos1, right-click for pos2. Real-time particle previews show your selection borders.