# Admin GUI

Open with `/shs gui` (player with `soapsstamina.admin`).

Requires `gui.enabled: true` in `config.yml`. If disabled, players see the message from `messages.yml` → `gui.disabled`.

## Pages

| Menu | Purpose |
|------|---------|
| Main | Navigation hub |
| Toggle Features | Enable/disable systems (paged) |
| Action Settings | Numeric drain and cost editors |
| Effects and Biomes | Exhaustion effects, biome multipliers, freeze/sweat |
| System Settings | Hunger, engine, UI, encumbrance, overexertion, scaling |
| Biome List | Add/remove/edit cold and hot biomes |
| Biome Edit | Per-biome type and drain multiplier |

Titles and button labels come from `messages.yml` → `gui`.

## Toggle page highlights

Movement: sprint, jump, swim, elytra, climbing, crawling, boat, riptide

Combat: attack, shield, winded, projectiles, bow, crossbow, trident, throwables, mace, damage-intake

Environment: water/lava contact, soul sand, honey, powder snow, slime bounce, biomes, altitude

Systems: hunger modes, exhaustion effects, overexertion, sounds, stamina food, dodge, sprint burst, bed rest

Weight: encumbered drowning/fall damage, scaling-weight, scaling-drain, MMOItems weight

UI: stamina UI, low stamina warning, player display choice, stamina bar

Left-click toggles on/off. Changes save to YAML and reload the plugin.

## Value editors

Action and system pages use click increments:

- Left-click: +small step
- Right-click: -small step
- Shift+left: +large step
- Shift+right: -large step

Some values cycle on click (e.g. UI type, scaling-drain stat-format).

## Biome editor

- Biome list: left-click add cold biome, right-click add hot biome (uses biome at player location).
- Edit page: cycle cold/hot, adjust multiplier, remove biome.

## Hunger toggle behavior

**Hunger** and **Hunger Bar** toggles share one `hunger.mode`. Turning one on turns the other off in the GUI and warns if you switch modes.

## Scaling-drain (v1.0.7)

On the Toggle Features page: **Stat vs Carry Weight Drain**.

On System Settings: sliders for `stat-per-point`, `stress-per-ratio`, `percent-reference`, and stat-format cycle (points vs percent).

## Tips

- Use the GUI for playtesting, then copy final values into your tracked config for production.
- Debug toggle is available; remember to turn it off before go-live.
- Console cannot open the GUI; use `/shs toggle` and `/shs config set` from console instead.
