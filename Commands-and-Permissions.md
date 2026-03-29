# Commands & Permissions

## Player Commands

### `/stamina`
Shows your current stamina, max stamina, percentage, and hunger level.

Permission: `soapsstamina.use` (default: everyone)

Alias: `/shs stamina`

---

## Admin Commands

All admin commands need `soapsstamina.admin` (default: op).

### `/shs reload`
Reloads config, messages, and weight files from disk. No restart needed.

### `/shs gui`
Opens the in-game settings panel. Click items to toggle features and adjust values. Only works if `gui.enabled` is true in config.

The GUI includes a Biome Settings page where you can add, remove, and edit biomes directly. Click a biome to change its type (cold/hot) or drain multiplier. No config editing needed.

### `/shs weight <subcommand>`
Manages items and settings in weight.yml without editing the file.

Subcommands:

- `/shs weight set <material> <weight>` - Set the weight for an item type
- `/shs weight remove <material>` - Remove an item's custom weight (falls back to default)
- `/shs weight info <material>` - Show the current weight of an item
- `/shs weight armor set <material> <weight>` - Set an armor material's weight multiplier
- `/shs weight armor remove <material>` - Remove an armor material's custom multiplier
- `/shs weight encumbrance <key> <value>` - Change an encumbrance setting

Available encumbrance keys: `max-weight`, `severe-weight`, `encumbered-drain-multiplier`, `severe-drain-multiplier`, `encumbered-slowness`, `severe-slowness`, `block-sprint-severe`, `default-weight`

Examples:
- `/shs weight set DIAMOND_SWORD 3.5` - diamonds swords weigh 3.5
- `/shs weight armor set NETHERITE 1.5` - netherite armor multiplier 1.5x
- `/shs weight encumbrance max-weight 150` - encumbered above 150 total weight
- `/shs weight info IRON_PICKAXE` - shows the current weight of an iron pickaxe

### `/shs toggle <setting>`
Flips a setting on or off.

Available settings: `sprint`, `jump`, `swim`, `block-place`, `block-break`, `sneak`, `attack`, `shield-block`, `hunger`, `hunger-bar`, `drain-saturation`, `effects`, `slowness`, `sweat-particles`, `heavy-breathing`, `stumble`, `debug`, `stop-sprint-on-empty`, `low-stamina-warning`, `biomes`, `biome-freeze`, `biome-sweat`, `encumbered-drowning`, `encumbered-fall-damage`, `stamina-bar`

Example: `/shs toggle effects` turns exhaustion effects on or off.

### `/shs config set <group> <key> <value>`
Changes a specific config value.

Example: `/shs config set sprint drain-per-second 3.0`

Groups include: `sprint`, `jump`, `swim`, `block-place`, `block-break`, `sneak`, `attack`, `shield-block`, `hunger`, `engine`, `effects`, `slowness`, `sweat-particles`, `stumble`, `ui`, `general`, `biomes`, `encumbrance`, `stamina-bar`

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
| `soapsstamina.use` | Check own stamina with `/stamina` | Everyone |
| `soapsstamina.admin` | All admin commands (reload, gui, toggle, config, give, reset) | OP |
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
| `soapsstamina.bypass.encumbrance` | Encumbrance drain multipliers and effects |

The global `soapsstamina.bypass` skips everything. The per-feature ones are more targeted - if you only want someone to skip sprint drain but still pay for everything else, give them `soapsstamina.bypass.sprint` instead.

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
