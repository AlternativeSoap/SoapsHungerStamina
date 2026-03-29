# Placeholders

Requires [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) installed on your server. Placeholders register automatically when PlaceholderAPI is detected.

---

## Available Placeholders

| Placeholder | Returns | Example |
|---|---|---|
| `%shs_stamina%` | Current stamina (whole number) | `78` |
| `%shs_stamina_max%` | Max stamina (whole number) | `100` |
| `%shs_stamina_percent%` | Stamina as a percentage 0-100 | `78` |
| `%shs_stamina_bar%` | Text stamina bar using filled/empty characters | `████████░░` |
| `%shs_weight%` | Total inventory weight (1 decimal) | `42.5` |
| `%shs_encumbered%` | Encumbrance level | `NONE`, `NORMAL`, or `SEVERE` |

---

## Notes

- `%shs_stamina_bar%` only works when the text bar is enabled in config:
  ```yaml
  ui:
    bar:
      enabled: true
      length: 10
      filled-char: "█"
      empty-char: "░"
  ```
  If the bar is disabled, this placeholder returns an empty string.

- `%shs_encumbered%` returns one of three values:
  - `NONE` - under the weight limit
  - `NORMAL` - over the encumbered threshold (default: 100)
  - `SEVERE` - over the severely encumbered threshold (default: 150)

---

## Usage Examples

**Scoreboard line:**
```
Stamina: %shs_stamina%/%shs_stamina_max%
```

**Tab list:**
```
%shs_stamina_bar% %shs_stamina_percent%%
```

**Hologram with weight:**
```
Weight: %shs_weight% [%shs_encumbered%]
```

These work anywhere PlaceholderAPI placeholders are supported: scoreboards, tab lists, holograms, chat formats, BossBar plugins, etc.
