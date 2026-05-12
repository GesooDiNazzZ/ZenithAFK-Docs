# Create Your First Zone

## 1. Get the Selection Wand

```
/zafk wand
```

This gives you a **Golden Axe** — the zone selection tool. Left-click to set position 1, right-click to set position 2 (same workflow as WorldEdit).

## 2. Select a Region

Walk to the two opposite corners of your desired AFK zone and click to define the 3D region. You'll see **particle previews** at the edges of your selection.

## 3. Create the Zone

```
/zafk create <name>
```

For example: `/zafk create vip_zone`

This creates the zone with default settings. Players standing inside will start earning rewards based on the default `reward-interval`.

## 4. Configure the Zone

You have two options:

### Option A: In-Game GUI Editor

```
/zafk edit <zone>
```

The GUI editor lets you modify everything without touching a YAML file:

- Reward interval & rolls per interval
- Max players & permission gating
- Display settings (title, subtitle, action bar, boss bar)
- Streak configuration
- Enter conditions (playtime, level, permission)
- Sound effects
- Add/remove rewards

### Option B: Edit the YAML File

Zone files are stored in `plugins/ZenithAFK/zones/<zone-name>.yml`. See the [Zone Config Reference](../reference/zone-config.md) for all available options.

After editing YAML, run `/zafk reload` to apply.

## 5. Test It

Stand inside the zone and verify:

- :white_check_mark: Boss bar appears with countdown timer (`mm:ss`)
- :white_check_mark: You receive rewards at the configured interval
- :white_check_mark: `/zafk info <zone>` shows correct player counts and settings
- :white_check_mark: `/zafk stats` shows your zone time

## Zone Enter Conditions

You can restrict who can enter a zone with **enter conditions**:

```yaml
enter-conditions:
  min-playtime-minutes: 60    # Player must have 1h+ playtime
  min-level: 10                # Player must be level 10+
  required-permission: ""      # Permission node (leave empty for none)
```

Players who don't meet the conditions receive a configurable denial message.