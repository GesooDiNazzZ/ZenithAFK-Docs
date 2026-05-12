# Developer API

ZenithAFK provides a clean, stable API for other plugins to interact with.

## Getting the API

```java
import io.gesoodinazzz.zenithafk.ZenithAFK;
import io.gesoodinazzz.zenithafk.api.ZenithAfkAPI;

ZenithAfkAPI api = ZenithAFK.getApi();
```

## Available Methods

```java
// Check AFK state
boolean isPlayerSoftAFK(UUID uuid);   // true if in an AFK zone
boolean isPlayerHardAFK(UUID uuid);    // true if idle (hard AFK)
boolean isPlayerAFK(UUID uuid);        // true if either soft or hard AFK

// Get timing data
long getPlayerAFKTime(UUID uuid);          // total AFK time in ms
long getPlayerActivePlayTime(UUID uuid);   // active (non-AFK) playtime in ms

// Get zone data
String getPlayerZone(UUID uuid);           // current zone name (or null)
int getZonePlayerCount(String zoneName);   // players in a zone
```

## Usage Example

```java
@Override
public void onEnable() {
    ZenithAfkAPI api = ZenithAFK.getApi();
    
    // Check if a player is AFK
    UUID uuid = player.getUniqueId();
    if (api.isPlayerAFK(uuid)) {
        player.sendMessage("You are currently AFK!");
    }
    
    // Get zone name
    String zone = api.getPlayerZone(uuid);
    if (zone != null) {
        player.sendMessage("You are in zone: " + zone);
    }
}
```

## Dependency

Add ZenithAFK as a dependency in your `plugin.yml`:

```yaml
depend: [ZenithAFK]
```

Or as a soft dependency if ZenithAFK is optional:

```yaml
softdepend: [ZenithAFK]
```

!!! warning "Always check if ZenithAFK is enabled"
    When using `softdepend`, always check `Bukkit.getPluginManager().isPluginEnabled("ZenithAFK")` before calling the API.