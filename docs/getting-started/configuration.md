# Configuration

The main config file is located at `plugins/ZenithAFK/config.yml`.

## Core Settings

```yaml
# AFK Detection
afk-detection:
  enabled: true
  idle-timeout: 300          # seconds before player is marked Hard-AFK
  check-interval: 10        # how often to check for idle players
  teleport-to-spawn: false   # teleport idle players to spawn
  spawn-location: "world:0:64:0"
  
  # Protection while Hard-AFK
  prevent-damage: true
  prevent-knockback: true
  prevent-collision: true
  prevent-movement: true
  
  # Exit conditions
  exit-on-rotation: true
  exit-on-command: true
  rotation-threshold: 15.0
  exit-commands:
    - "home"
    - "spawn"
    - "tpa"
    - "warp"

# Anti-macro/bot detection
anti-macro:
  enabled: true
  check-interval-seconds: 30
  rotation-threshold: 2.0
  violation-threshold: 200
  punishment: "kick"
  kick-message: "&cAnti-macro: suspicious movement detected"

# Playtime Tracking
playtime:
  enabled: true
  count-during-soft-afk: true
  count-during-hard-afk: false
  format: "formatted"   # formatted, short, or seconds

# Storage
storage:
  type: "yaml"    # yaml, sqlite, or mysql
  mysql:
    host: "localhost"
    port: 3306
    database: "zenithafk"
    username: "root"
    password: ""
    sync-interval-seconds: 30

# Update Checker
update-checker:
  enabled: true

# Language
language: "en"
```

## Language Files

English (`lang_en.yml`) and Italian (`lang_it.yml`) are bundled. You can create your own by copying either file and translating the values. Set `language` in config.yml to match your file name.

See [Lang Files Reference](../reference/lang-files.md) for all available messages.

## Zone Files

Each zone gets its own YAML file under `plugins/ZenithAFK/zones/`. See the [Zone Config Reference](../reference/zone-config.md) for the full schema.

## Vault Economy

Vault integration is **auto-detected** — no configuration needed. If Vault + an economy plugin are present, you can use the `money` field in rewards:

```yaml
rewards:
  - chance: 30
    display: "$500"
    money: 500
```

If Vault is not installed, the `money` field is silently ignored and the reward display falls back to the `display` string.