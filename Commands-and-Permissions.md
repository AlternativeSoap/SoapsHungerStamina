# Commands and Permissions

## Commands

| Command | Permission | Who | Description |
|---------|------------|-----|-------------|
| `/shs` | None | Anyone | Shows version and usage |
| `/shs help` | None | Anyone | Help menu |
| `/shs reload` | `soapsstamina.admin` | Admin | Reload all config files |
| `/shs stamina` | None | Player | Show own stamina status |
| `/shs stamina display <off\|actionbar\|bossbar>` | `soapsstamina.display.choose` | Player | Set personal UI preference |
| `/shs stamina give <player> <amount>` | `soapsstamina.admin` | Admin | Add stamina to a player |
| `/shs stamina reset <player>` | `soapsstamina.admin` | Admin | Set stamina to max |
| `/shs stats` | None | Player | Session stamina statistics |
| `/shs toggle <setting>` | `soapsstamina.admin` | Admin | Toggle a feature on/off |
| `/shs config set <group> <key> <value>` | `soapsstamina.admin` | Admin | Set a numeric/boolean/string value |
| `/shs gui` | `soapsstamina.admin` | Admin (player) | Open settings GUI |
| `/shs weight` | None | Player | Show own weight status |
| `/shs weight info [material]` | None | Player | Weight of held item or material |
| `/shs weight set <material> <weight>` | `soapsstamina.admin` | Admin | Set item weight in `weight.yml` |
| `/shs weight remove <material>` | `soapsstamina.admin` | Admin | Remove item from weight map |
| `/shs weight armor set <material> <weight>` | `soapsstamina.admin` | Admin | Set armor drain contribution |
| `/shs weight armor remove <material>` | `soapsstamina.admin` | Admin | Remove armor entry |
| `/shs weight encumbrance <key> <value>` | `soapsstamina.admin` | Admin | Tune encumbrance settings |
| `/shs weight scaling-weight <key> <value>` | `soapsstamina.admin` | Admin | Keys: `placeholder`, `per-point`, `cap` |
| `/shs weight scaling-drain <key> <value>` | `soapsstamina.admin` | Admin | Keys: `placeholder`, `stat-format`, `percent-reference`, `stat-per-point`, `stress-per-ratio` |
| `/stamina` | `soapsstamina.use` (default true) | Player | Shortcut for own stamina |
| `/stamina display <off\|actionbar\|bossbar>` | `soapsstamina.display.choose` | Player | Same as `/shs stamina display` |
| `/weight` | None | Player | Shortcut for own weight |
| `/weight info [material]` | None | Player | Same as `/shs weight info` |

Alias: `/soapshungerstamina` → `/shs`

Display commands require `player-display-choice.enabled: true` in `config.yml` and global `ui.enabled: true`.

## Toggle settings (`/shs toggle <name>`)

`sprint`, `jump`, `swim`, `water-contact`, `lava-contact`, `block-place`, `block-break`, `sneak`, `attack`, `shield-block`, `winded`, `hunger`, `hunger-bar`, `drain-saturation`, `effects`, `slowness`, `sweat-particles`, `heavy-breathing`, `stumble`, `debug`, `sprint-lock-enabled`, `sprint-lock-unlock-above-zero`, `sprint-lock-unlock-threshold`, `low-stamina-warning`, `biomes`, `biome-freeze`, `biome-sweat`, `biome-freeze-particles`, `altitude`, `encumbered-drowning`, `encumbered-fall-damage`, `scaling-weight`, `scaling-drain`, `idle-regen`, `overexertion`, `overexertion-scaling`, `projectiles`, `bow`, `bow-scale-with-charge`, `crossbow`, `trident`, `throwables`, `elytra`, `climbing`, `mace`, `potion-modifiers`, `damage-intake`, `boat`, `crawling`, `riptide`, `tool-use`, `block-interact`, `powder-snow`, `slime-bounce`, `soul-sand`, `honey-block`, `mmoitems-weight`, `executableitems-weight`, `ecoitems-weight`, `crucible-weight`, `sounds`, `second-wind`, `weapon-costs`, `recovery-animation`, `player-display-choice`, `stamina-food`, `dodge`, `sprint-burst`, `bed-rest`, `bed-rest-buff`

`hunger` and `hunger-bar` are mutually exclusive modes. Toggling one on warns if the other was active.

## Config set groups (`/shs config set <group> <key> <value>`)

`sprint`, `jump`, `swim`, `water-contact`, `lava-contact`, `block-place`, `block-break`, `sneak`, `attack`, `shield-block`, `winded`, `hunger`, `engine`, `effects`, `slowness`, `sweat-particles`, `stumble`, `ui`, `general`, `sprint-lock`, `biomes`, `altitude`, `encumbrance`, `stamina-bar`, `overexertion`, `idle`, `bow`, `crossbow`, `trident`, `throwables`, `elytra`, `climbing`, `mace`, `potion-modifiers`, `damage-intake`, `boat`, `crawling`, `riptide`, `tool-use`, `block-interact`, `powder-snow`, `slime-bounce`, `soul-sand`, `honey-block`, `second-wind`, `weapon-costs`, `dodge`, `sprint-burst`, `bed-rest`, `context`

Run `/shs config set` with no args to see usage. Unknown group/key returns an error message.

## Permissions

| Permission | Default | Description |
|------------|---------|-------------|
| `soapsstamina.admin` | op | Reload, give/reset stamina, gui, toggle, config, weight admin |
| `soapsstamina.use` | true | Use `/stamina` |
| `soapsstamina.bypass` | false | Bypass all stamina drain |
| `soapsstamina.bypass.sprint` | false | Bypass sprint drain |
| `soapsstamina.bypass.jump` | false | Bypass jump drain |
| `soapsstamina.bypass.swim` | false | Bypass swim drain |
| `soapsstamina.bypass.block-place` | false | Bypass block place drain |
| `soapsstamina.bypass.block-break` | false | Bypass block break drain |
| `soapsstamina.bypass.sneak` | false | Bypass sneak regen |
| `soapsstamina.bypass.attack` | false | Bypass attack drain |
| `soapsstamina.bypass.shield-block` | false | Bypass shield block drain |
| `soapsstamina.bypass.hunger` | false | Bypass hunger overflow drain |
| `soapsstamina.bypass.effects` | false | Bypass all exhaustion effects |
| `soapsstamina.bypass.effects.slowness` | false | Bypass exhaustion slowness |
| `soapsstamina.bypass.effects.sweat` | false | Bypass sweat particles |
| `soapsstamina.bypass.effects.breathing` | false | Bypass heavy breathing (darkness) |
| `soapsstamina.bypass.effects.stumble` | false | Bypass stumble knockback |
| `soapsstamina.bypass.biomes` | false | Bypass biome drain and effects |
| `soapsstamina.bypass.altitude` | false | Bypass altitude drain |
| `soapsstamina.bypass.projectiles` | false | Bypass projectile/throwable drain |
| `soapsstamina.bypass.encumbrance` | false | Bypass encumbrance multipliers and effects |
| `soapsstamina.maxweight.*` | false | Per-player max weight (e.g. `soapsstamina.maxweight.500`) |
| `soapsstamina.bypass.elytra` | false | Bypass elytra drain |
| `soapsstamina.bypass.climbing` | false | Bypass climbing drain |
| `soapsstamina.bypass.mace` | false | Bypass mace smash extra cost |
| `soapsstamina.bypass.damage-intake` | false | Bypass environmental damage stamina drain |
| `soapsstamina.bypass.boat` | false | Bypass boat paddling drain |
| `soapsstamina.bypass.crawling` | false | Bypass crawling drain |
| `soapsstamina.bypass.riptide` | false | Bypass riptide cost |
| `soapsstamina.bypass.tool-use` | false | Bypass hoe/shears/brush/flint costs |
| `soapsstamina.bypass.powder-snow` | false | Bypass powder snow exposure boost |
| `soapsstamina.bypass.slime-bounce` | false | Bypass slime bounce cost |
| `soapsstamina.bypass.second-wind` | false | Bypass second wind mechanic |
| `soapsstamina.display.choose` | true | Choose stamina display type |
| `soapsstamina.bypass.soul-sand` | false | Bypass soul sand drain multiplier |
| `soapsstamina.bypass.honey-block` | false | Bypass honey block drain multiplier |
| `soapsstamina.bypass.water-contact` | false | Bypass water contact drain |
| `soapsstamina.bypass.lava-contact` | false | Bypass lava contact drain |
| `soapsstamina.bypass.overexertion` | false | Bypass overexertion damage |
| `soapsstamina.bypass.winded` | false | Bypass winded on damage |
| `soapsstamina.bypass.idle` | false | Bypass idle regen |
| `soapsstamina.bypass.stamina-food` | false | Bypass stamina food effects |
| `soapsstamina.bypass.dodge` | false | Bypass dodge ability |
| `soapsstamina.bypass.sprint-burst` | false | Bypass sprint burst |
| `soapsstamina.bypass.bed-rest` | false | Bypass bed rest recovery |

Master bypass permission is configurable: `general.bypass-permission` (default `soapsstamina.bypass`).
