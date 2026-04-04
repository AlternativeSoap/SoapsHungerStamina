# Commands & Permissions

## Player Commands

### `/stamina`
Shows your current stamina, max stamina, percentage, and hunger level.

Permission: `soapsstamina.use` (default: everyone)

Alias: `/shs stamina`

### `/weight`
Shows your current total weight and max weight.

Permission: `soapsstamina.use` (default: everyone)

Alias: `/shs weight`

### `/weight info [material]`
Shows the weight of the item in your main hand, or a specific material if provided.

Permission: `soapsstamina.use` (default: everyone)

---

## Admin Commands

All admin commands need `soapsstamina.admin` (default: op).

### `/shs reload`
Reloads config.yml, actions.yml, messages.yml, and weight.yml from disk. No restart needed.

### `/shs gui`
Opens the in-game settings panel. Click items to toggle features and adjust values. Only works if `gui.enabled` is true in config.

The GUI includes a Biome Settings page where you can add, remove, and edit biomes directly. Click a biome to change its type (cold/hot) or drain multiplier. No config editing needed.

### `/shs weight <subcommand>`
Manages items and settings in weight.yml without editing the file.

Subcommands:

- `/shs weight set <material> <weight>` — Set the weight for an item type
- `/shs weight remove <material>` — Remove an item's custom weight (falls back to default)
- `/shs weight info [material]` — Show the current weight of an item (available to all players)
- `/shs weight armor set <material> <weight>` — Set an armor material's weight multiplier
- `/shs weight armor remove <material>` — Remove an armor material's custom multiplier
- `/shs weight encumbrance <key> <value>` — Change an encumbrance setting
- `/shs weight scaling-weight <key> <value>` — Change a scaling-weight setting
- `/shs weight scaling-drain <key> <value>` — Change a scaling-drain setting

Available encumbrance keys: `max-weight`, `severe-weight`, `encumbered-drain-multiplier`, `severe-drain-multiplier`, `encumbered-slowness`, `severe-slowness`, `block-sprint-severe`, `default-weight`

Available scaling-weight keys: `per-point`, `cap`, `placeholder`

Available scaling-drain keys: `per-point`, `cap`, `placeholder`

Examples:
- `/shs weight set DIAMOND_SWORD 3.5` — diamond swords weigh 3.5
- `/shs weight armor set NETHERITE_CHESTPLATE 0.15` — netherite chestplate weight 0.15
- `/shs weight encumbrance max-weight 150` — encumbered above 150 total weight
- `/shs weight info IRON_PICKAXE` — shows the current weight of an iron pickaxe
- `/shs weight scaling-weight per-point 3.0` — 3.0 extra max weight per placeholder point

### `/shs toggle <setting>`
Flips a setting on or off.

Available settings:

| Setting | What it toggles |
|---|---|
| `sprint` | Sprint stamina drain |
| `jump` | Jump stamina cost |
| `swim` | Swim stamina drain |
| `water-contact` | Water contact drain |
| `lava-contact` | Lava contact drain |
| `block-place` | Block place cost |
| `block-break` | Block break cost |
| `sneak` | Sneak regen |
| `attack` | Attack cost |
| `shield-block` | Shield block drain |
| `winded` | Winded (damage intake stamina) |
| `idle-regen` | Idle regen |
| `elytra` | Elytra gliding drain |
| `climbing` | Climbing drain |
| `eating-regen` | Eating stamina restore |
| `mace` | Mace smash extra cost |
| `potion-modifiers` | Potion effect drain modifiers |
| `damage-intake` | Damage intake drain |
| `boat` | Boat paddling drain |
| `crawling` | Crawling drain |
| `riptide` | Riptide launch cost |
| `tool-use` | Tool use (hoe/shears/brush) cost |
| `powder-snow` | Powder snow drain |
| `slime-bounce` | Slime bounce cost |
| `soul-sand` | Soul sand drain multiplier |
| `honey-block` | Honey block drain multiplier |
| `hunger` | Hunger overflow mode |
| `hunger-bar` | Hunger bar mode |
| `drain-saturation` | Drain saturation first |
| `overexertion` | Overexertion system |
| `overexertion-scaling` | Overexertion damage scaling |
| `projectiles` | All projectile costs |
| `bow` | Bow cost |
| `bow-scale-with-charge` | Bow charge scaling |
| `crossbow` | Crossbow cost |
| `trident` | Trident cost |
| `throwables` | All throwable costs |
| `effects` | All exhaustion effects |
| `slowness` | Exhaustion slowness |
| `sweat-particles` | Exhaustion sweat particles |
| `heavy-breathing` | Exhaustion heavy breathing |
| `stumble` | Exhaustion stumble |
| `biomes` | Biome system |
| `biome-freeze` | Biome freeze ticks |
| `biome-sweat` | Biome sweat particles |
| `biome-freeze-particles` | Biome freeze particles |
| `altitude` | Altitude system |
| `encumbered-drowning` | Encumbrance drowning |
| `encumbered-fall-damage` | Encumbrance fall damage |
| `scaling-weight` | Scaling max weight (PAPI) |
| `scaling-drain` | Scaling drain reduction (PAPI) |
| `mmoitems-weight` | MMOItems custom weights |
| `debug` | Console debug logging |
| `stop-sprint-on-empty` | Stop sprint at 0 stamina |
| `low-stamina-warning` | Low stamina UI warning |
| `stamina-bar` | Text stamina bar |

Example: `/shs toggle effects` turns exhaustion effects on or off.

### `/shs config set <group> <key> <value>`
Changes a specific config value.

Example: `/shs config set sprint drain-per-second 3.0`

Available groups and their keys:

| Group | Keys |
|---|---|
| `sprint` | `drain-per-second` |
| `jump` | `cost`, `cooldown` |
| `swim` | `drain-per-second` |
| `water-contact` | `drain-per-second` |
| `lava-contact` | `drain-per-second` |
| `block-place` | `cost` |
| `block-break` | `cost` |
| `sneak` | `regen-per-second` |
| `attack` | `cost` |
| `shield-block` | `initial-cost`, `drain-per-second` |
| `winded` | `normal-instant-cost`, `normal-drain-per-second`, `normal-duration`, `critical-instant-cost`, `critical-drain-per-second`, `critical-duration`, `critical-regen-lock-duration`, `refresh-on-hit` |
| `idle` | `regen-per-second`, `regen-action-cooldown` |
| `elytra` | `drain-per-second` |
| `climbing` | `drain-per-second` |
| `eating-regen` | `regen-amount` |
| `mace` | `cost` |
| `potion-modifiers` | `speed-multiplier`, `haste-multiplier` |
| `damage-intake` | `cost-per-heart` |
| `boat` | `drain-per-second` |
| `crawling` | `drain-per-second` |
| `riptide` | `cost` |
| `tool-use` | `hoe-cost`, `shears-cost`, `brush-cost` |
| `powder-snow` | `drain-per-second` |
| `slime-bounce` | `cost` |
| `soul-sand` | `drain-multiplier` |
| `honey-block` | `drain-multiplier` |
| `hunger` | `drain-per-second`, `min-hunger`, `drain-saturation` |
| `overexertion` | `threshold`, `base-damage`, `scaling-divisor`, `max-damage`, `recovery-rate`, `warning-threshold` |
| `bow` | `cost` |
| `crossbow` | `cost` |
| `trident` | `cost` |
| `throwables` | `snowball`, `egg`, `ender-pearl`, `eye-of-ender`, `splash-potion`, `lingering-potion`, `experience-bottle`, `firework-rocket`, `fishing-rod`, `wind-charge` |
| `engine` | `tick-interval`, `movement-threshold` |
| `effects` | `recovery-threshold` |
| `slowness` | `amplifier` |
| `sweat-particles` | `count` |
| `stumble` | `chance`, `strength` |
| `ui` | `type`, `update-threshold`, `message-cooldown`, `low-stamina-threshold` |
| `stamina-bar` | `length`, `filled-char`, `empty-char` |
| `general` | `bypass-permission` |
| `biomes` | `cold-drain-multiplier`, `hot-drain-multiplier`, `encumbrance-biome-bonus`, `freeze-ticks`, `sweat-count`, `freeze-particles-count` |
| `altitude` | `high-threshold`, `high-multiplier`, `high-passive-drain`, `low-threshold`, `low-multiplier`, `low-passive-drain` |
| `encumbrance` | `drowning-air-loss`, `fall-damage-max-multiplier` |

Tab completion shows you the available keys and value hints for each group.

### `/shs stamina give <player> <amount>`
Gives stamina to a player (won't go above their max).

Example: `/shs stamina give Steve 50`

### `/shs stamina reset <player>`
Sets a player's stamina back to full.

### `/shs help`
Lists all available commands.

---

## Permissions

### Core Permissions

| Permission | What it does | Default |
|---|---|---|
| `soapsstamina.use` | Check own stamina with `/stamina` and weight with `/weight` | Everyone |
| `soapsstamina.admin` | All admin commands (reload, gui, toggle, config, give, reset, weight management) | OP |
| `soapsstamina.bypass` | Skip all stamina and hunger drain | Nobody |

---

### Per-Feature Bypass Permissions

These let you exempt specific players from specific features. Give a player one of these and that feature won't affect them, even if it's enabled for everyone else.

All default to nobody (false).

| Permission | What it bypasses |
|---|---|
| `soapsstamina.bypass.sprint` | Sprint stamina drain |
| `soapsstamina.bypass.jump` | Jump stamina cost |
| `soapsstamina.bypass.swim` | Swim stamina drain |
| `soapsstamina.bypass.block-place` | Block place stamina cost |
| `soapsstamina.bypass.block-break` | Block break stamina cost |
| `soapsstamina.bypass.sneak` | Sneak stamina regen bonus |
| `soapsstamina.bypass.attack` | Attack stamina cost |
| `soapsstamina.bypass.shield-block` | Shield block stamina drain |
| `soapsstamina.bypass.hunger` | Hunger overflow drain |
| `soapsstamina.bypass.effects` | All exhaustion effects |
| `soapsstamina.bypass.effects.slowness` | Just the slowness effect |
| `soapsstamina.bypass.effects.sweat` | Just sweat particles |
| `soapsstamina.bypass.effects.breathing` | Just heavy breathing (darkness) |
| `soapsstamina.bypass.effects.stumble` | Just the stumble knockback |
| `soapsstamina.bypass.biomes` | Biome drain multipliers and effects |
| `soapsstamina.bypass.altitude` | Altitude drain multipliers and passive drain |
| `soapsstamina.bypass.projectiles` | All projectile and throwable stamina drain |
| `soapsstamina.bypass.encumbrance` | Encumbrance drain multipliers and effects |
| `soapsstamina.bypass.elytra` | Elytra gliding stamina drain |
| `soapsstamina.bypass.climbing` | Climbing stamina drain |
| `soapsstamina.bypass.eating` | Eating stamina regen |
| `soapsstamina.bypass.mace` | Mace smash extra stamina cost |
| `soapsstamina.bypass.damage-intake` | Damage intake stamina drain |
| `soapsstamina.bypass.boat` | Boat paddling stamina drain |
| `soapsstamina.bypass.crawling` | Crawling stamina drain |
| `soapsstamina.bypass.riptide` | Riptide trident stamina cost |
| `soapsstamina.bypass.tool-use` | Tool use (hoe, shears, brush) stamina cost |
| `soapsstamina.bypass.powder-snow` | Powder snow stamina drain |
| `soapsstamina.bypass.slime-bounce` | Slime bounce stamina cost |
| `soapsstamina.bypass.soul-sand` | Soul sand drain multiplier |
| `soapsstamina.bypass.honey-block` | Honey block drain multiplier |
| `soapsstamina.maxweight.*` | Set custom max weight per player (e.g. `soapsstamina.maxweight.500`) |

The global `soapsstamina.bypass` skips everything. The per-feature ones are more targeted — if you only want someone to skip sprint drain but still pay for everything else, give them `soapsstamina.bypass.sprint` instead.

---

## Tab Completion

All admin commands have tab completion. It shows:
- Subcommands at each level
- Toggle setting names
- Config group and key names
- Weight subcommands, material names, encumbrance keys, and value hints
- Value hints (current value, true/false, etc.)
- Online player names for give/reset

---

## PlaceholderAPI

If PlaceholderAPI is installed, placeholders are registered automatically. See [Placeholders](Placeholders.md) for the full list and usage examples.
