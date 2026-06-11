# Changelog

## 1.0.7

- Added **scaling-drain**: an RPG stat (strength by default via `%mmocore_attribute_strength%`) offsets how much inventory weight increases action stamina drain. Enable with `scaling-drain.enabled: true` in `weight.yml` (requires PlaceholderAPI).
- Replaced legacy flat scaling-drain (`per-point` / `cap`). Those keys are removed from `weight.yml` on reload.
- When scaling-drain is on, encumbrance tier **drain multipliers no longer stack**. Slowness, sprint block, drowning, and fall damage penalties still apply.
- New placeholders: `%shs_carry_burden%`, `%shs_scaling_drain_mult%`.
- Admin GUI: scaling-drain sliders and stat-format cycle (points vs percent).
- Command: `/shs weight scaling-drain <key> <value>` for live tuning.
- Code cleanup: unified movement drain calculator, shared PlaceholderAPI helpers, simplified GUI toggles.

## Earlier versions

Check `V1.0.6 Changelog.txt` and `V1.0.5 Changelog.txt` in the plugin source tree for prior release notes. Major additions in recent versions include dodge, sprint burst, bed rest, stamina food, projectile costs, biome/altitude systems, overexertion, and the admin GUI.
