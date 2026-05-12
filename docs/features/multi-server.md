# Multi-Server Sync

ZenithAFK supports **cross-server data synchronization** via MySQL, allowing player data to persist across your entire network (BungeeCord, Velocity, etc.).

## How It Works

1. Each server writes player data to the shared MySQL database.
2. Every `sync-interval-seconds`, each server pulls the latest data for online players.
3. Conflicts are resolved using timestamps — the most recent write wins.

## Configuration

```yaml
storage:
  type: "mysql"
  mysql:
    host: "localhost"
    port: 3306
    database: "zenithafk"
    username: "root"
    password: "your-password"
    sync-interval-seconds: 30
```

| Setting | Default | Description |
|---|---|---|
| `host` | `localhost` | MySQL server address |
| `port` | `3306` | MySQL port |
| `database` | `zenithafk` | Database name |
| `username` | `root` | MySQL user |
| `password` | *(empty)* | MySQL password |
| `sync-interval-seconds` | `30` | How often to pull updated data from the database |

## What Gets Synced

All `PlayerData` fields are synchronized:

- Total playtime (active + AFK)
- Active playtime
- Per-zone time map
- Daily rewards received count
- Reward reset day (for daily limit)
- Streak level and streak start time
- Current zone name
- Last sync timestamp

## Setting Up

1. Create a MySQL database accessible from all servers.
2. Set `storage.type: "mysql"` in `config.yml` on every server.
3. Use the **same** MySQL credentials on all servers.
4. ZenithAFK automatically creates the required tables on startup.
5. Adjust `sync-interval-seconds` based on your needs:
    - **30 seconds** (default) — good balance of freshness and performance
    - **10 seconds** — nearly real-time, more DB queries
    - **60 seconds** — less DB load, slightly stale data

!!! warning "All servers must use the same database"
    Each server must point to the same MySQL database for sync to work. Using different databases means no sync.

## Storage Backends Comparison

| Feature | YAML | SQLite | MySQL |
|---|---|---|---|
| Best for | Small servers | Medium servers | Networks |
| Setup | Zero config | Zero config | DB required |
| Cross-server | :x: | :x: | :white_check_mark: |
| Auto-save | Every 5 min | Every 5 min | Every 5 min + sync |
| Async | :white_check_mark: | :white_check_mark: | :white_check_mark: |