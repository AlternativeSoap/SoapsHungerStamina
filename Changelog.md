# Changelog

## 1.0.7

- Added **scaling-drain**: an RPG stat (strength by default via `%mmocore_attribute_strength%`) offsets how much inventory weight increases action stamina drain. Enable with `scaling-drain.enabled: true` in `weight.yml` (requires PlaceholderAPI).
- Replaced legacy flat scaling-drain (`per-point` / `cap`). Those keys are removed from `weight.yml` on reload.
- When scaling-drain is on, encumbrance tier **drain multipliers no longer stack**. Slowness, sprint block, drowning, and fall damage penalties still apply.
- New placeholders: `%shs_carry_burden%`, `%shs_scaling_drain_mult%`.
- Admin GUI: scaling-drain sliders and stat-format cycle (points vs percent).
- Command: `/shs weight scaling-drain <key> <value>` for live tuning.

## 1.0.6

- Master UI switch (`ui.enabled`) to turn off all stamina bars and chat UI from one setting
- UI switch added to admin Features GUI
- Split disabled worlds into separate stamina and weight lists (`general.disabled-worlds.stamina` and `.weight`)
- Polished config and message comments
- Improved admin GUI search and hunger toggle display while filtering
- Fixed System Settings GUI so all values stay visible and editable
- Performance pass on engine and admin GUI

## 1.0.5

- Sprinting and stamina lock feel more solid; less sprint abuse at low stamina
- Separate PvP/PvE multipliers and in-combat regen control
- Anti-spam for jump, dodge, and throwables
- More action coverage: block interact, mace smash, slime bounce, lava contact, bed-rest timing
- Projectile, dodge, sprint-burst, bed-rest, stamina-food, and second-wind settings consolidated into `actions.yml`
- New-player easing for first minutes on the server
- Admin GUI: feature search/filter and better state handling
- `/shs config set` biome keys fixed
- Disabled-world checks normalized for reliable world-name matching
- Engine and weight performance improvements
- Startup warnings for unsafe weight scaling setups
- YAML files polished with clearer owner-focused comments
