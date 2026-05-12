# Display System

Every zone adapts its UI based on the player's AFK state. You can configure **separate display settings** for Soft AFK (in zone) and Hard AFK (idle detection).

## Display Types

| Type | Description |
|---|---|
| **Title** | Large centered title text |
| **Subtitle** | Smaller text below the title |
| **Action Bar** | Persistent text above the hotbar |
| **Boss Bar** | Animated progress bar at top of screen |

## Configuration

```yaml
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
    subtitle: "&#FF6666You are idle"
    action-bar: "&#FF4444Move to exit AFK mode"
    bossbar:
      text: "&#FF4444⚠ AFK — Move to exit"
      color: RED
      style: SEGMENTED_20
      direction: DECREASING
```

## Boss Bar

The boss bar shows a **countdown timer** with the `mm:ss` format (e.g., `02:47`) using the `%time%` placeholder.

### Boss Bar Options

| Option | Values | Description |
|---|---|---|
| `text` | Any string with placeholders | Boss bar text. Supports `%time%`, `%zone%`, `%player%` |
| `color` | PINK, BLUE, RED, GREEN, YELLOW, PURPLE, WHITE | Bar color |
| `style` | SOLID, SEGMENTED_6, SEGMENTED_10, SEGMENTED_12, SEGMENTED_20 | Bar segmentation |
| `direction` | INCREASING, DECREASING | Whether the bar fills up or drains |

## Placeholders

Available in all display fields:

| Placeholder | Description |
|---|---|
| `%time%` | Time until next reward (`mm:ss`) |
| `%zone%` | Current zone name |
| `%player%` | Player display name |
| `%interval%` | Total reward interval in seconds |

## Formatting

All display fields support:

- **MiniMessage** gradients: `&#7C3AEDHello &#8B5CF6World`
- **Hex colors**: `&#FF4444Red text`
- **Standard color codes**: `&cRed text`

## Sound Effects

```yaml
sounds:
  zone-enter: ENTITY_EXPERIENCE_ORB_PICKUP
  zone-leave: ENTITY_ITEM_BREAK
  reward-receive: ENTITY_PLAYER_LEVELUP
```

Set any sound to `""` to disable it.