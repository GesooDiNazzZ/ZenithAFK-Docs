# Time-Based Zones & Enter Conditions

## Time-Based Zones

Schedule zones to be active only during specific days and hours. This is useful for:

- **VIP zones** that are only active on weekends
- **Event zones** that run during specific hours
- **Rotating zones** with different schedules

### Configuration

```yaml
active-days:
  - MONDAY
  - WEDNESDAY
  - FRIDAY
  - SATURDAY
  - SUNDAY

active-hours:
  - "18:00-22:00"
```

### Behavior

- When a zone is **inactive**, players cannot enter it
- Players already inside are **not kicked** when the zone becomes inactive, but they stop earning rewards
- Days use **English uppercase** names (MONDAY, TUESDAY, etc.)
- Hours use **24h UTC format** — `HH:MM-HH:MM`
- Leaving `active-days` or `active-hours` empty means **always active**

### Examples

**Weekends only:**
```yaml
active-days:
  - SATURDAY
  - SUNDAY
```

**Every day, evenings only:**
```yaml
active-days: []    # Empty = every day
active-hours:
  - "18:00-22:00"
```

**Multiple time windows:**
```yaml
active-hours:
  - "08:00-10:00"
  - "18:00-22:00"
```

## Enter Conditions

Restrict zone access based on player attributes. Players who don't meet the conditions see a denial message.

```yaml
enter-conditions:
  min-playtime-minutes: 60      # Must have 1h+ total playtime
  min-level: 10                  # Must be level 10+
  required-permission: ""        # Custom permission (empty = none)
```

### min-playtime-minutes

Requires the player to have a minimum total playtime on the server. Uses ZenithAFK's built-in playtime tracking. Set to `0` to disable.

### min-level

Requires the player to have reached a minimum XP level. Set to `0` to disable.

### required-permission

An additional permission node required to enter the zone (separate from the zone's `permission` field). Leave empty (`""`) to disable.

!!! note "Combined with zone permission"
    Enter conditions are checked **in addition** to the zone's `permission` field. A player must satisfy both the permission gate AND all enter conditions.