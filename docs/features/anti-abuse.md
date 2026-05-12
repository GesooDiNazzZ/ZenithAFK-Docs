# Anti-Abuse Features

ZenithAFK includes a full suite of anti-abuse features to keep AFK zones fair and prevent exploitation.

## Anti-Macro / Bot Detection

The anti-macro system monitors player head rotation patterns to detect automated scripts and bots.

```yaml
anti-macro:
  enabled: true
  check-interval-seconds: 30
  rotation-threshold: 2.0
  violation-threshold: 200
  punishment: "kick"
  kick-message: "&cAnti-macro: suspicious movement detected"
```

### How It Works

1. Every `check-interval-seconds`, the system samples the player's head rotation.
2. If the rotation change per tick is below `rotation-threshold` degrees, the violation score increases.
3. Once the cumulative violation score exceeds `violation-threshold`, the configured `punishment` is applied.

### Punishment Types

| Value | Action |
|---|---|
| `kick` | Kicks the player with the configured message |
| `none` | Detection only (for logging/analytics) |

!!! tip "Tuning the threshold"
    Default values (threshold `2.0`, violation `200`) are calibrated for typical survival gameplay. Increase the violation threshold if you get false positives with players who stand very still by nature.

## Anti-Redirection

When a player is teleported into an AFK zone (via Hard-AFK detection), the **anti-redirection** system prevents other plugins from immediately teleporting them out.

A **grace period** (configurable per zone, default 5 seconds) blocks external teleport events right after a player enters the zone. This prevents plugins like Essentials `/home` from interfering with the AFK flow.

```yaml
redirection-grace-seconds: 5   # Grace period after zone entry
```

## Daily Reward Limit

Cap how many rewards a player can receive per zone per day:

```yaml
daily-reward-limit: 10   # Max 10 rewards per player per day
```

- Resets at **UTC midnight** every day
- Set to `0` to disable the limit
- Tracked per-player, per-zone

## Auto-Kick

Automatically remove players who have been in a zone for too long:

```yaml
auto-kick-minutes: 120   # Kick after 2 hours in this zone
```

- Helps prevent 24/7 AFK farming
- Set to `0` to disable
- Players can re-enter after being kicked (unless `session-time-limit` is also set)

## Session Time Limit

Set a hard cap on how long a player can spend in a zone **per session**:

```yaml
session-time-limit: 60   # Max 60 minutes per session
```

- Once the limit is reached, the player is removed from the zone
- Set to `0` for unlimited sessions

## IP Limit

Prevent multi-accounting by limiting how many accounts per IP can use a zone:

```yaml
ip-limit: 2   # Max 2 accounts per IP
```

- Bypassed by `zenithafk.bypass.iplimit` permission
- Set to `0` to disable