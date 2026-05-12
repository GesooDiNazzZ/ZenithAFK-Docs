# Zone Configuration Reference

Each zone has its own file at `plugins/ZenithAFK/zones/<zone-name>.yml`.

## Full Example

```yaml
# ─── Zone Region ────────────────────────────
region:
  world: "world"
  min-x: -100
  min-y: 64
  min-z: -200
  max-x: 100
  max-y: 90
  max-z: 200

# ─── General ─────────────────────────────────
enabled: true
permission: ""
max-players: -1              # -1 = unlimited
ip-limit: 0                   # 0 = disabled

# ─── Rewards ─────────────────────────────────
reward-interval: 180          # seconds between rewards
rolls-per-interval: 1         # how many rewards per roll
reset-timer-on-reward: true   # reset countdown after reward

# ─── Streak & Combo ─────────────────────────
streak-interval-minutes: 30   # minutes to level up streak (0 = disabled)
streak-max-level: 5            # maximum streak multiplier level

# ─── Safety & Limits ────────────────────────
session-time-limit: 0          # max minutes per session (0 = unlimited)
auto-kick-minutes: 0           # kick after X minutes AFK (0 = disabled)
daily-reward-limit: 0          # max rewards per player per day (0 = unlimited)

# ─── Enter Conditions ───────────────────────
enter-conditions:
  min-playtime-minutes: 0     # minimum total playtime (0 = none)
  min-level: 0                 # minimum XP level (0 = none)
  required-permission: ""      # additional permission node

# ─── Anti-Redirection ───────────────────────
redirection-grace-seconds: 5   # grace period after entering zone

# ─── Time-Based Activation ──────────────────
active-days: []                # empty = every day. e.g. [SATURDAY, SUNDAY]
active-hours: []               # empty = always. e.g. ["18:00-22:00"]

# ─── Display ────────────────────────────────
display:
  soft:
    title: "&#7C3AED⌚ &#8B5CF6AFK"
    subtitle: "&#7C3AEDZone: &#8B5CF6%zone%"
    action-bar: "&#7C3AED— &#8B5CF6Next: &#7C3AED%time%"
    bossbar:
      text: "&#7C3AED⌚ &#8B5CF6AFK &#7C3AED— &#8B5CF6Next: &#7C3AED%time%"
      color: PURPLE
      style: SEGMENTED_20
      direction: DECREASING
  hard:
    title: "&#FF4444⚠ Forced AFK"
    subtitle: "&#FF6666Move to exit AFK mode"
    action-bar: "&#FF4444Move to exit"
    bossbar:
      text: "&#FF4444⚠ AFK — Move to exit"
      color: RED
      style: SEGMENTED_20
      direction: DECREASING

# ─── Sounds ─────────────────────────────────
sounds:
  zone-enter: ENTITY_EXPERIENCE_ORB_PICKUP
  zone-leave: ENTITY_ITEM_BREAK
  reward-receive: ENTITY_PLAYER_LEVELUP

# ─── Commands ───────────────────────────────
enter-commands: []
leave-commands: []

# ─── Rewards Table ──────────────────────────
rewards:
  - chance: 60
    display: "&bDiamond x5"
    commands:
      - "give %player% diamond 5"

  - chance: 30
    display: "&a$500"
    money: 500

  - chance: 10
    display: "&6Netherite Ingot"
    commands:
      - "give %player% netherite_ingot 1"
```

## Field Reference

### Region

| Field | Type | Description |
|---|---|---|
| `world` | string | World name |
| `min-x/y/z` | int | Minimum corner coordinates |
| `max-x/y/z` | int | Maximum corner coordinates |

### General

| Field | Type | Default | Description |
|---|---|---|---|
| `enabled` | bool | `true` | Whether the zone is active |
| `permission` | string | `""` | Required permission to enter |
| `max-players` | int | `-1` | Max concurrent players (-1 = unlimited) |
| `ip-limit` | int | `0` | Max accounts per IP (0 = disabled) |

### Rewards

| Field | Type | Default | Description |
|---|---|---|---|
| `reward-interval` | int | `180` | Seconds between reward rolls |
| `rolls-per-interval` | int | `1` | Number of rolls per interval |
| `reset-timer-on-reward` | bool | `true` | Reset countdown after each reward |

### Streak & Combo

| Field | Type | Default | Description |
|---|---|---|---|
| `streak-interval-minutes` | int | `0` | Minutes between streak levels (0 = disabled) |
| `streak-max-level` | int | `5` | Maximum streak level |

### Safety & Limits

| Field | Type | Default | Description |
|---|---|---|---|
| `session-time-limit` | int | `0` | Max minutes per session (0 = unlimited) |
| `auto-kick-minutes` | int | `0` | Kick after X minutes AFK (0 = disabled) |
| `daily-reward-limit` | int | `0` | Max rewards per player per day (0 = unlimited) |
| `redirection-grace-seconds` | int | `5` | Grace period after zone entry |

### Enter Conditions

| Field | Type | Default | Description |
|---|---|---|---|
| `min-playtime-minutes` | int | `0` | Required total playtime (0 = no requirement) |
| `min-level` | int | `0` | Required XP level (0 = no requirement) |
| `required-permission` | string | `""` | Additional permission node |

### Time-Based

| Field | Type | Default | Description |
|---|---|---|---|
| `active-days` | list | `[]` | Days when the zone is active (empty = always) |
| `active-hours` | list | `[]` | UTC time ranges when zone is active (empty = always) |

### Boss Bar

| Field | Values | Description |
|---|---|---|
| `color` | PINK, BLUE, RED, GREEN, YELLOW, PURPLE, WHITE | Bar color |
| `style` | SOLID, SEGMENTED_6/10/12/20 | Bar segmentation |
| `direction` | INCREASING, DECREASING | Fill direction |

### Reward Entry

| Field | Type | Required | Description |
|---|---|---|---|
| `chance` | int | Yes | Probability weight (relative to other rewards) |
| `display` | string | Yes | Name shown in messages and preview GUI |
| `commands` | list | No | Console commands (`%player%` placeholder) |
| `money` | double | No | Vault economy deposit amount |
| `items` | list | No | ItemStack definitions |