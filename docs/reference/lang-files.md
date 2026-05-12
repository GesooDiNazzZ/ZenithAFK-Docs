# Language Files

ZenithAFK ships with **English** (`lang_en.yml`) and **Italian** (`lang_it.yml`) translations. You can create your own by copying either file and translating the values.

## Setting the Language

```yaml
# config.yml
language: "en"
```

Set this to the filename without extension (e.g., `it`, `de`, `fr`).

## Available Messages

All messages support MiniMessage hex colors (`&#RRGGBB`) and standard color codes (`&c`, `&l`, etc.).

### Zone Messages

| Key | Description |
|---|---|
| `zone.enter` | Shown when entering a zone |
| `zone.leave` | Shown when leaving a zone |
| `zone.denied` | Shown when denied entry |
| `zone.full` | Shown when zone is at max players |
| `zone.condition-denied.min-playtime` | Need more playtime to enter |
| `zone.condition-denied.min-level` | Need higher level to enter |
| `zone.condition-denied.required-permission` | Missing permission to enter |
| `zone.kicked-session` | Kicked due to session time limit |
| `zone.kicked-afk` | Kicked due to auto-kick timer |
| `zone.inactive` | Zone is currently inactive |
| `zone.ip-limit` | Too many accounts from this IP |

### Reward Messages

| Key | Description |
|---|---|
| `reward.received` | Shown when receiving a reward |
| `reward.limit-reached` | Daily reward limit reached |

### AFK Messages

| Key | Description |
|---|---|
| `afk.soft-enter` | Entering soft-AFK state |
| `afk.soft-leave` | Leaving soft-AFK state |
| `afk.hard-enter` | Entering hard-AFK state |
| `afk.hard-leave` | Leaving hard-AFK state |

### Playtime Messages

| Key | Description |
|---|---|
| `playtime.self` | Your own playtime display |
| `playtime.other` | Another player's playtime display |
| `playtime.top-header` | Leaderboard header |
| `playtime.top-entry` | Leaderboard entry format |

### Command Messages

| Key | Description |
|---|---|
| `command.no-permission` | No permission error |
| `command.player-only` | Console-only command error |
| `command.unknown-zone` | Zone not found error |
| `command.reload-success` | Reload confirmation |
| `command.create-success` | Zone created confirmation |
| `command.delete-success` | Zone deleted confirmation |

### Update Messages

| Key | Description |
|---|---|
| `update.available` | Update notification for admins |

## Adding a Language

1. Copy `lang_en.yml` to a new file, e.g., `lang_de.yml`.
2. Translate all message values to your language.
3. Place the file in `plugins/ZenithAFK/lang/`.
4. Set `language: "de"` in `config.yml`.
5. Run `/zafk reload`.