# Reward System

ZenithAFK uses a **weighted probability** system for rewards. Each interval, the zone rolls rewards based on their probability weights.

## How It Works

1. A player stands in a zone for `reward-interval` seconds.
2. The zone rolls `rolls-per-interval` times, each time picking a reward based on chance weights.
3. Each reward's commands and/or items are delivered to the player.
4. The session timer resets (if configured) and the cycle starts again.

## Defining Rewards

```yaml
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

### Reward Fields

| Field | Type | Required | Description |
|---|---|---|---|
| `chance` | int | Yes | Probability weight (not percentage — values are relative) |
| `display` | string | Yes | Name shown in reward messages and preview GUI |
| `commands` | list | No | Console commands to execute. Use `%player%` placeholder |
| `money` | double | No | Amount to deposit via Vault economy (requires Vault) |
| `items` | list | No | ItemStack definitions to give/drop |

!!! note "Chance weights are relative"
    `chance: 60` and `chance: 30` means the first reward has a 66.7% chance, not 60%. The probability is `weight / sum_of_all_weights`.

## Vault Economy Integration

Vault is **auto-detected** — no configuration needed. Simply add a `money` field to any reward:

```yaml
- chance: 30
  display: "&a$500"
  money: 500
```

If Vault or an economy plugin is not installed, the `money` field is silently ignored and the display falls back to the `display` string.

## Streak & Combo Rewards

Keep players engaged by escalating rewards the longer they stay in a zone:

```yaml
streak-interval-minutes: 30   # Level up every 30 minutes
streak-max-level: 5           # Max streak multiplier
```

Streak level increases every `streak-interval-minutes` while the player stays in the zone continuously. Higher streak levels give bonus reward rolls — the player receives their normal rewards **plus** one extra roll per streak level.

Streak resets when the player leaves the zone or gets kicked.

## Reward Preview GUI

Players can preview all rewards for a zone:

```
/zafk rewards <zone>
```

This opens a GUI showing every reward with its display name, chance percentage, and streak indicator. Admins also see an **"Add Reward"** button that opens the Reward Wizard for in-game reward creation.

## Daily Reward Limit

Cap how many rewards a single player can receive per day (resets at UTC midnight):

```yaml
daily-reward-limit: 10   # Max 10 rewards per player per day in this zone
```

Set to `0` to disable the limit entirely.

## Auto-Kick

Automatically remove players who have been in a zone too long:

```yaml
auto-kick-minutes: 120   # Kick players after 2 hours in this zone
```

Set to `0` to disable.