# Getting Started

## Install

1. Install **Paper 1.21+**, **SoapsCommon**, and **MMOCore**.
2. Drop `SoapsHungerStamina-1.0.7.jar` into `plugins/`.
3. Restart the server (not just reload) on first install.
4. Install **PlaceholderAPI** if you plan to use `%shs_*%` placeholders or scaling-weight / scaling-drain.

## First-run checklist

1. Confirm MMOCore stamina is working for players before tuning SHS.
2. Open `plugins/SoapsHungerStamina/config.yml` and set `general.disabled-worlds` if some worlds should ignore stamina or weight.
3. Skim `actions.yml` for sprint, jump, and attack costs. Defaults are moderate survival values.
4. Pick a hunger mode (`hunger.mode`: `overflow`, `bar`, or `disabled`). See [Hunger Modes](Hunger-Modes.md).
5. Set `ui.type` to `ACTION_BAR`, `BOSS_BAR`, or `CHAT`. Boss bar is the default.
6. Review `weight.yml` → `encumbrance.max-weight` and `severe-weight` for your server's economy.
7. Run `/shs reload` after file edits, or use `/shs gui` for live toggles (admin).

## Test as a player

| Command | Purpose |
|---------|---------|
| `/stamina` | Current stamina and hunger (overflow mode) |
| `/weight` | Current carry weight vs max |
| `/shs stats` | Session drain/regen stats |

Sprint, jump, and fight briefly. Watch the boss bar or action bar. Cross the encumbrance threshold by holding heavy blocks.

## Test as admin

| Command | Purpose |
|---------|---------|
| `/shs help` | Command list |
| `/shs gui` | Settings GUI |
| `/shs toggle sprint` | Flip a feature without editing YAML |
| `/shs config set sprint drain-per-second 1.0` | Live numeric tweak |

Set `general.debug: true` to log drain events to console. Turn it off on production.

## Optional integrations

| Integration | Enable in |
|-------------|-----------|
| MMOItems weights | `weight.yml` → `mmoitems-weight.enabled` |
| Scaling carry cap by level | `weight.yml` → `scaling-weight.enabled` + PlaceholderAPI |
| Stat-based load drain | `weight.yml` → `scaling-drain.enabled` + PlaceholderAPI |
| Player UI choice | `config.yml` → `player-display-choice.enabled` |

## Presets

The plugin ships YAML snippets under `presets/` in the source repo (`vanilla-plus`, `pvp-balanced`, `rpg-combat`, `hardcore-survival`). Copy sections into your live config rather than replacing whole files. See [Examples](Examples.md).
