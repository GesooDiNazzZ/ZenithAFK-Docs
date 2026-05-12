# Hard-AFK Detection

The Hard-AFK system detects **idle players** — even outside AFK zones — and takes action automatically.

## How It Works

When a player stops moving and rotating for longer than `idle-timeout` seconds, they are marked as **Hard-AFK**. At that point, ZenithAFK can teleport them to a designated area and apply a full protection suite.

## Configuration

```yaml
afk-detection:
  enabled: true
  idle-timeout: 300              # Seconds before marking as Hard-AFK
  check-interval: 10             # How often to check for idle players
  teleport-to-spawn: false       # Teleport idle players to spawn
  spawn-location: "world:0:64:0" # Where to teleport (world:x:y:yaw:pitch)
  
  prevent-damage: true           # Immune to PvP/PvE damage
  prevent-knockback: true        # No knockback from attacks
  prevent-collision: true        # Other entities can't push them
  prevent-movement: true         # Lock their position in place
  
  exit-on-rotation: true         # Looking around breaks Hard-AFK
  exit-on-command: true          # Typing commands breaks Hard-AFK
  rotation-threshold: 15.0       # How much head rotation exits AFK
  
  exit-commands:                  # These commands instantly break AFK
    - "home"
    - "spawn"
    - "tpa"
    - "warp"
```

## Exit Conditions

A player exits Hard-AFK mode when:

- :white_check_mark: They **look around** (rotation above threshold)
- :white_check_mark: They **type a command** (if `exit-on-command` is true)
- :white_check_mark: They type one of the **exit-commands** (e.g., `/home`)
- :white_check_mark: They have the `zenithafk.hardafk.bypass` permission

## Grace Period

After a player is force-teleported to the AFK area, there's a configurable **grace period** before rotation detection kicks in. This prevents an instant AFK loop if the player's camera jumps during the teleport animation.

Each zone has its own `redirection-grace-seconds` setting (default: `5`).

## Bypass Permission

Players with `zenithafk.hardafk.bypass` are never flagged as Hard-AFK, regardless of idle time.

## Relation to Soft-AFK

| State | Trigger | Display | Protection |
|---|---|---|---|
| **None** | Player is active | Normal gameplay | None |
| **Soft-AFK** | Player enters a zone | Zone display config | Zone-defined only |
| **Hard-AFK** | Player idle > timeout | Hard-AFK display | Full protection suite |

A player can be **both** Soft and Hard-AFK simultaneously (idle inside a zone). In this case, Hard-AFK display and protections take priority.