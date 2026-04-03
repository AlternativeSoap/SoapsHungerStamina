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
| `%shs_overexertion%` | Current overexertion value (1 decimal) | `12.3` |
| `%shs_overexerted%` | Whether the player is overexerting | `true` or `false` |

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
  - `NORMAL` - over the encumbered threshold (default: 300)
  - `SEVERE` - over the severely encumbered threshold (default: 500)

- `%shs_overexertion%` shows how much overexertion the player has accumulated. Overexertion builds up when the player keeps draining stamina at zero. Once it exceeds the threshold (default: 15), damage starts.

- `%shs_overexerted%` returns `true` when the player is actively past the overexertion threshold and taking damage, `false` otherwise.

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

**Overexertion warning on a scoreboard:**
```
Strain: %shs_overexertion%
```

These work anywhere PlaceholderAPI placeholders are supported: scoreboards, tab lists, holograms, chat formats, BossBar plugins, etc.
