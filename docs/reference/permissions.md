# Permissions

## Admin Permissions

| Permission | Default | Description |
|---|---|---|
| `zenithafk.admin` | op | Access to all admin commands |
| `zenithafk.stats` | true | View AFK statistics |

## Player Permissions

| Permission | Default | Description |
|---|---|---|
| `zenithafk.playtime` | true | View playtime |
| `zenithafk.playtimetop` | true | View playtime leaderboard |

## Bypass Permissions

| Permission | Default | Description |
|---|---|---|
| `zenithafk.bypass.iplimit` | false | Bypass IP limit per zone |
| `zenithafk.hardafk.bypass` | false | Never flagged as Hard-AFK |
| `zenithafk.update-notify` | op | Receive update notifications on join |

## Zone Permissions

Each zone can have its own `permission` field:

```yaml
permission: "zenithafk.zone.vip"
```

Players must have the specified permission to enter the zone. Leave empty (`""`) for no permission requirement.

This is separate from `enter-conditions.required-permission` — both are checked.