# Placeholders

Install [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/). SHS registers its placeholders automatically when PAPI is present.

---

## Available Placeholders

| Placeholder | Returns | Example |
|---|---|---|
| `%shs_stamina%` | Current stamina (whole number) | `78` |
| `%shs_stamina_max%` | Max stamina (whole number) | `100` |
| `%shs_stamina_percent%` | Stamina as a percentage 0–100 | `78` |
| `%shs_stamina_bar%` | Text stamina bar using filled/empty characters | `████████░░` |
| `%shs_weight%` | Total inventory weight (1 decimal) | `42.5` |
| `%shs_encumbered%` | Encumbrance level | `NONE`, `NORMAL`, or `SEVERE` |
| `%shs_overexertion%` | Current overexertion accumulation (1 decimal) | `8.3` |
| `%shs_overexerted%` | Whether the player is currently overexerting | `true` or `false` |
| `%shs_stat_drained%` | Session total stamina drained (1 decimal) | `254.3` |
| `%shs_stat_regened%` | Session total stamina regened (1 decimal) | `180.7` |
| `%shs_stat_second_winds%` | Session second wind trigger count | `2` |
| `%shs_stat_overexertions%` | Session overexertion event count | `1` |
| `%shs_stat_time_at_zero%` | Session seconds at 0 stamina (1 decimal) | `12.5` |
| `%shs_well_fed%` | Remaining Well Fed buff seconds (0 if inactive) | `25` |
| `%shs_well_rested%` | Remaining Well Rested buff seconds (0 if inactive) | `90` |
| `%shs_dodge_cooldown%` | Remaining dodge cooldown seconds (0 if ready) | `1.2` |
| `%shs_sprint_burst_cooldown%` | Remaining sprint burst cooldown seconds (0 if ready) | `22.5` |
| `%shs_carry_burden%` | Load burden after stat relief (0 = light, 1+ = at or over max carry) | `0.4` |
| `%shs_scaling_drain_mult%` | Current scaling-drain multiplier on action stamina | `1.12` |

---

## Notes

- `%shs_stamina_bar%` needs the text bar on in config:
  ```yaml
  ui:
    bar:
      enabled: true
      length: 10
      filled-char: "█"
      empty-char: "░"
  ```
  Bar off = empty string.

- `%shs_encumbered%`: `NONE` (under limit), `NORMAL` (over 300 by default), `SEVERE` (over 500 by default).

- `%shs_overexertion%`: builds while stamina is 0 and you're still draining. Damage starts past the threshold (default 25).

- `%shs_overexerted%`: `true` while actively overexerting.

- `%shs_carry_burden%`: only with `scaling-drain` on. `0` = stat covers the load; `1.0` = at carry cap after stat relief.

- `%shs_scaling_drain_mult%`: action drain multiplier from scaling-drain (`1.0` normal, higher = worse).

---

## Usage Examples

**Scoreboard:**
```
Stamina: %shs_stamina%/%shs_stamina_max%
```

**Tab:**
```
%shs_stamina_bar% %shs_stamina_percent%%
```

**Weight line:**
```
Weight: %shs_weight% [%shs_encumbered%]
```

Works anywhere PAPI placeholders do: scoreboards, tab, holograms, chat plugins, etc.
