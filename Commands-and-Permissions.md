# Commands & Permissions

## Player Commands

### `/stamina`
Shows your current stamina, max stamina, percentage, and hunger level.

**Permission:** `soapsstamina.use` (default: everyone)

**Alias:** `/shs stamina`

---

## Admin Commands

All admin commands need `soapsstamina.admin` (default: op).

### `/shs reload`
Reloads config, messages, and weight files from disk. No restart needed.

### `/shs gui`
Opens the in-game settings panel. Click items to toggle features and adjust values. Only works if `gui.enabled` is true in config.

### `/shs toggle <setting>`
Flips a setting on or off.

**Available settings:** `sprint`, `jump`, `swim`, `block-place`, `block-break`, `sneak`, `attack`, `shield-block`, `hunger`, `hunger-bar`, `drain-saturation`, `effects`, `slowness`, `sweat-particles`, `heavy-breathing`, `stumble`, `debug`, `stop-sprint-on-empty`, `low-stamina-warning`, `biomes`, `biome-freeze`, `biome-sweat`, `encumbered-drowning`, `encumbered-fall-damage`, `stamina-bar`

**Example:** `/shs toggle effects` — turns exhaustion effects on or off.

### `/shs config set <group> <key> <value>`
Changes a specific config value.

**Example:** `/shs config set sprint drain-per-second 3.0`

Groups include: `sprint`, `jump`, `swim`, `block-place`, `block-break`, `sneak`, `attack`, `shield-block`, `hunger`, `engine`, `effects`, `slowness`, `sweat-particles`, `stumble`, `ui`, `general`, `biomes`, `encumbrance`, `stamina-bar`

Tab completion shows you the available keys and value hints for each group.

### `/shs stamina give <player> <amount>`
Gives stamina to a player (won't go above their max).

**Example:** `/shs stamina give Steve 50`

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
| `soapsstamina.bypass` | Skip **all** stamina and hunger drain | Nobody |

---

### Per-Feature Bypass Permissions

These let you exempt specific players from specific features. Give a player one of these permissions and that feature won't affect them — even if the feature is enabled for everyone else.

All default to **nobody** (false).

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

**How it works with `soapsstamina.bypass`:**  
The global bypass skips everything. The per-feature permissions are more surgical — if you only want someone to skip sprint drain but still pay for everything else, give them `soapsstamina.bypass.sprint` instead of the full bypass.

---

## Tab Completion

All admin commands have tab completion. It shows:
- Subcommands at each level
- Toggle setting names
- Config group and key names
- Value hints (current value, true/false, etc.)
- Online player names for give/reset

---

## PlaceholderAPI

If PlaceholderAPI is installed, placeholders are registered automatically. See [Placeholders](Placeholders.md) for the full list and usage examples.
