# Default Config Files

Shipped inside the JAR under `src/main/resources/` (extracted to `plugins/SoapsHungerStamina/` on first run).

## File layout

| File | Role |
|------|------|
| `config.yml` | Global behavior, UI, hunger mode, biomes, altitude, overexertion, context |
| `actions.yml` | Per-action stamina costs, regen, abilities |
| `weight.yml` | Encumbrance, armor weight, item database, scaling |
| `messages.yml` | MiniMessage strings for commands, UI, effects |
| `plugin.yml` | Plugin metadata, commands, permissions (not editable at runtime) |

## config.yml sections

`general`, `worlds`, `action-world-overrides`, `context`, `hunger`, `ui`, `sounds`, `gui`, `player-display-choice`, `engine`, `overexertion`, `effects`, `biomes`, `altitude`

Default hunger mode: `overflow`. Default UI: `BOSS_BAR`. Biomes and altitude: off. Exhaustion effects: off. Sounds: off.

## actions.yml sections

`regen-action-cooldown`, movement (sprint through riptide), combat (attack through damage-intake), interactions, environment, potion-modifiers, recovery (sneak, idle, stamina-food, dodge, sprint-burst, bed-rest)

Defaults: most movement and combat drains on. Dodge and sprint burst off. Boat off. Block interact off. Honey block off. Second wind off.

## weight.yml sections

`encumbrance`, `armor-weight`, `drowning`, `fall-damage`, `scaling-weight`, `scaling-drain`, `custom-items`, plugin weight overrides (`mmoitems-weight`, etc.), `items` (large material map)

Default encumbrance: 300 normal, 500 severe. scaling-weight and scaling-drain: off.

## messages.yml sections

`prefix`, `command`, `exhaustion`, `second-wind`, `encumbrance`, `winded`, `overexertion`, `ui`, `biome`, `altitude`, `gui`, `stamina-food`, `dodge`, `sprint-burst`, `bed-rest`

Uses MiniMessage (`<red>`, `<gradient:...>`, etc.). `%prefix%` expands in most strings.

## Safe edits

- Keep top-level keys in `weight.yml` unchanged; code reads exact paths.
- Valid `hunger.mode`: `overflow`, `bar`, `disabled`.
- Valid `ui.type`: `ACTION_BAR`, `BOSS_BAR`, `CHAT` (case-insensitive in config set).
- Valid sprint lock `unlock-mode`: `disabled`, `above-zero`, `threshold-percent`.

## Reload behavior

`/shs reload` reloads all four YAML files, refreshes weight cache, re-registers PlaceholderAPI expansion, and restarts the engine task.

Legacy `scaling-drain` keys (`per-point`, `cap`) are stripped from `weight.yml` on reload in v1.0.7+.

## Presets (not auto-installed)

Reference YAML in the source repo `presets/` folder:

- `vanilla-plus.yml`
- `pvp-balanced.yml`
- `rpg-combat.yml`
- `hardcore-survival.yml`

Copy sections manually; do not replace entire live files without review.
