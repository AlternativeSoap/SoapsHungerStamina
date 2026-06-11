# Placeholders

Requires **PlaceholderAPI**. Identifier: `shs`.

Use on scoreboards, tab, chat plugins, and in `weight.yml` scaling placeholders.

## All placeholders (22)

| Placeholder | Returns | Example |
|-------------|---------|---------|
| `%shs_stamina%` | Current stamina (integer) | `78` |
| `%shs_stamina_max%` | Max stamina (integer) | `100` |
| `%shs_stamina_percent%` | Stamina 0-100 (integer) | `78` |
| `%shs_stamina_bar%` | Text bar from `ui.bar` settings | `████████░░` |
| `%shs_weight%` | Total inventory weight (1 decimal) | `42.5` |
| `%shs_encumbered%` | `NONE`, `NORMAL`, or `SEVERE` | `NORMAL` |
| `%shs_overexertion%` | Overexertion accumulation (1 decimal) | `8.3` |
| `%shs_overexerted%` | Actively overexerting | `true` / `false` |
| `%shs_stat_drained%` | Session total drained (1 decimal) | `254.3` |
| `%shs_stat_regened%` | Session total regened (1 decimal) | `180.7` |
| `%shs_stat_second_winds%` | Session second wind count | `2` |
| `%shs_stat_overexertions%` | Session overexertion events | `1` |
| `%shs_stat_time_at_zero%` | Session seconds at 0 stamina (1 decimal) | `12.5` |
| `%shs_well_fed%` | Well Fed buff seconds left (0 if off) | `25` |
| `%shs_well_rested%` | Well Rested buff seconds left (0 if off) | `90` |
| `%shs_dodge_cooldown%` | Dodge cooldown seconds left (0 if ready) | `1.2` |
| `%shs_sprint_burst_cooldown%` | Sprint burst cooldown seconds left (0 if ready) | `22.5` |
| `%shs_biome%` | Biome category: `COLD`, `HOT`, or `NEUTRAL` | `COLD` |
| `%shs_winded%` | Player is winded | `true` / `false` |
| `%shs_display%` | Display preference: `actionbar`, `bossbar`, `off`, or `default` | `bossbar` |
| `%shs_carry_burden%` | Load burden after stat relief (1 decimal, 0 = light) | `0.40` |
| `%shs_scaling_drain_mult%` | Action drain multiplier from scaling-drain (2 decimals) | `1.12` |

## Notes

**`%shs_stamina_bar%`** uses `config.yml` → `ui.bar.length`, `filled-char`, `empty-char`. Same settings as `%stamina_bar%` in `messages.yml`.

**`%shs_encumbered%`** tiers use `weight.yml` thresholds (default normal at 300, severe at 500). Per-player max cap can change with `soapsstamina.maxweight.<number>` or scaling-weight.

**`%shs_carry_burden%` and `%shs_scaling_drain_mult%`** only matter when `scaling-drain.enabled: true`. Burden `0` means the player's stat fully covers the load; `1.0+` means at or over effective carry cap after stat relief.

**Session stats** reset on disconnect. They are not persisted.

## Example layouts

```
Stamina: %shs_stamina%/%shs_stamina_max%
```

```
%shs_stamina_bar% %shs_stamina_percent%%
```

```
Weight: %shs_weight% [%shs_encumbered%] burden %shs_carry_burden%
```
