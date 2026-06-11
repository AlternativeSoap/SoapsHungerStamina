# SoapsHungerStamina Wiki

Server-owner documentation for **SoapsHungerStamina** v1.0.7.

SoapsHungerStamina is an MMOCore stamina addon. It adds action-based stamina drain and regen, inventory weight and encumbrance, hunger integration, biome and altitude pressure, combat winded effects, overexertion damage, and optional dodge, sprint burst, and bed rest recovery.

## Requirements

| Plugin | Required |
|--------|----------|
| Paper 1.21+ | Yes |
| SoapsCommon | Yes (hard dependency) |
| MMOCore | Yes (hard dependency) |
| PlaceholderAPI | Optional (scaling-weight, scaling-drain, `%shs_*%`) |
| MMOItems | Optional (duplicate attack drain prevention, custom item weights) |
| ExecutableItems, EcoItems, MythicCrucible | Optional (custom item weights) |

## Quick links

| Page | What it covers |
|------|----------------|
| [Introduction](Introduction.md) | Feature overview and how systems connect |
| [Getting Started](Getting-Started.md) | Install, first config steps, go-live checklist |
| [Configuration](Configuration.md) | `config.yml` reference |
| [Actions](Actions.md) | `actions.yml` stamina costs and recovery |
| [Weight and Encumbrance](Weight-and-Encumbrance.md) | `weight.yml`, scaling, penalties |
| [Hunger Modes](Hunger-Modes.md) | overflow, bar, disabled |
| [Abilities](Abilities.md) | Dodge, sprint burst, bed rest, stamina food |
| [Admin GUI](Admin-GUI.md) | In-game settings panel |
| [Commands and Permissions](Commands-and-Permissions.md) | Full command and permission tables |
| [Placeholders](Placeholders.md) | All 22 `%shs_*%` PlaceholderAPI placeholders |
| [Default Config Files](Default-Config-Files.md) | Shipped defaults and file layout |
| [Examples](Examples.md) | Presets and tuning recipes |
| [FAQ](FAQ.md) | Common owner questions |
| [Changelog](Changelog.md) | Version history |

## Config files (after first run)

```
plugins/SoapsHungerStamina/
  config.yml      # Global rules, UI, biomes, overexertion, hunger mode
  actions.yml     # Stamina costs per action and recovery
  weight.yml      # Item weights, encumbrance, scaling
  messages.yml    # Player and admin messages (MiniMessage)
```

Reload with `/shs reload` (requires `soapsstamina.admin`).
