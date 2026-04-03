# Commands & Permissions

## Player Commands

| Command | Description |
|---|---|
| `/stamina` | Shows your current stamina, max stamina, percentage, and hunger level |
| `/weight` | Shows your current total weight and max carry weight |
| `/weight info [material]` | Shows the weight of a specific item, or the item you're holding |

Permission: `soapsstamina.use` (default: everyone)

---

## Main Command

| Command | Description |
|---|---|
| `/shs` | Shows the plugin version and usage |
| `/shs help` | Lists all available commands |
| `/shs stamina` | Same as `/stamina` |

---

## Admin Commands

All admin commands need `soapsstamina.admin` (default: op).

### Reload & GUI

| Command | Description |
|---|---|
| `/shs reload` | Reloads config, messages, and weight files. No restart needed |
| `/shs gui` | Opens the in-game settings panel. Click items to toggle features and change values. Includes a biome settings page |

### Toggle

`/shs toggle <setting>` - Flips a setting on or off.

Available settings: `sprint`, `jump`, `swim`, `water-contact`, `lava-contact`, `block-place`, `block-break`, `sneak`, `attack`, `shield-block`, `winded`, `hunger`, `hunger-bar`, `drain-saturation`, `effects`, `slowness`, `sweat-particles`, `heavy-breathing`, `stumble`, `debug`, `stop-sprint-on-empty`, `low-stamina-warning`, `biomes`, `biome-freeze`, `biome-sweat`, `encumbered-drowning`, `encumbered-fall-damage`, `stamina-bar`, `scaling-weight`, `scaling-drain`, `idle-regen`, `overexertion`, `overexertion-scaling`

### Config

`/shs config set <group> <key> <value>` - Changes a specific config value.

Example: `/shs config set sprint drain-per-second 3.0`

### Weight

| Command | Description |
|---|---|
| `/shs weight set <material> <weight>` | Set the weight for an item type |
| `/shs weight remove <material>` | Remove a custom weight (falls back to default) |
| `/shs weight info <material>` | Show an item's current weight |
| `/shs weight armor set <material> <weight>` | Set an armor material's weight multiplier |
| `/shs weight armor remove <material>` | Remove an armor material's custom multiplier |
| `/shs weight encumbrance <key> <value>` | Change an encumbrance setting (max-weight, severe-weight, etc.) |
| `/shs weight scaling-weight <key> <value>` | Change a scaling-weight setting (per-point, cap, placeholder) |
| `/shs weight scaling-drain <key> <value>` | Change a scaling-drain setting (per-point, cap, placeholder) |

### Stamina

| Command | Description |
|---|---|
| `/shs stamina give <player> <amount>` | Gives stamina to a player (won't go above their max) |
| `/shs stamina reset <player>` | Resets a player back to full stamina |

---

## Permissions

### Core Permissions

| Permission | What it does | Default |
|---|---|---|
| `soapsstamina.use` | Check own stamina with `/stamina` and weight with `/weight` | Everyone |
| `soapsstamina.admin` | All admin commands (reload, gui, toggle, config, give, reset, weight) | OP |
| `soapsstamina.bypass` | Skip all stamina and hunger drain | Nobody |

---

### Per-Feature Bypass Permissions

These let you exempt specific players from specific features. Give a player one of these and that feature won't affect them, even if it's enabled for everyone else.

All default to nobody (false).

| Permission | What it bypasses |
|---|---|
| `soapsstamina.bypass.sprint` | Sprint stamina drain |
| `soapsstamina.bypass.jump` | Jump stamina cost |
| `soapsstamina.bypass.swim` | Swim, water contact, and lava contact stamina drain |
| `soapsstamina.bypass.block-place` | Block place stamina cost |
| `soapsstamina.bypass.block-break` | Block break stamina cost |
| `soapsstamina.bypass.sneak` | Sneak stamina regen bonus |
| `soapsstamina.bypass.idle` | Idle stamina regen bonus |
| `soapsstamina.bypass.attack` | Attack stamina cost |
| `soapsstamina.bypass.shield-block` | Shield block stamina drain |
| `soapsstamina.bypass.winded` | Winded drain from taking damage |
| `soapsstamina.bypass.hunger` | Hunger overflow drain |
| `soapsstamina.bypass.overexertion` | Overexertion damage |
| `soapsstamina.bypass.effects` | All exhaustion effects |
| `soapsstamina.bypass.effects.slowness` | Just the slowness effect |
| `soapsstamina.bypass.effects.sweat` | Just sweat particles |
| `soapsstamina.bypass.effects.breathing` | Just heavy breathing (darkness) |
| `soapsstamina.bypass.effects.stumble` | Just the stumble knockback |
| `soapsstamina.bypass.biomes` | Biome drain multipliers and effects |
| `soapsstamina.bypass.encumbrance` | Encumbrance drain multipliers and effects |

The global `soapsstamina.bypass` skips everything. The per-feature ones are more targeted - if you only want someone to skip sprint drain but still pay for everything else, give them `soapsstamina.bypass.sprint` instead.

### Special Permissions

| Permission | What it does | Default |
|---|---|---|
| `soapsstamina.maxweight.<number>` | Sets a custom max carry weight for that player (e.g. `soapsstamina.maxweight.500` gives 500 max weight) | Nobody |

This is useful for rank-based carry capacity without needing PlaceholderAPI scaling.

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
