# Configuration

Main file: `plugins/SoapsHungerStamina/config.yml`

Action costs live in `actions.yml`. Weight in `weight.yml`. Messages in `messages.yml`.

## general

| Key | Default | Description |
|-----|---------|-------------|
| `bypass-permission` | `soapsstamina.bypass` | Permission that skips all drain |
| `op-bypass` | `true` | OPs bypass stamina systems |
| `ignore-flying` | `true` | Skip drain for creative/spectator flying (elytra still drains) |
| `debug` | `false` | Console debug logging |
| `disabled-worlds.stamina` | `[]` | Worlds with no stamina engine/UI |
| `disabled-worlds.weight` | `[]` | Worlds with no weight/encumbrance |

## worlds

Per-world drain multiplier stack. Example:

```yaml
worlds:
  world_nether: 1.25
```

## action-world-overrides

Per-world per-action enable and multiplier:

```yaml
action-world-overrides:
  world:
    sprint:
      enabled: true
      multiplier: 1.0
    attack:
      multiplier: 1.2
```

## context

| Section | Purpose |
|---------|---------|
| `pvp-pve` | Separate multipliers for PvP vs PvE on attack, projectiles, winded, damage-intake |
| `in-combat` | Combat window duration, regen multiplier (default 0.5), allow dodge in combat |
| `rate-limits` | Anti-spam caps for jump, dodge, throwables |
| `new-players` | Temporary reduced drain for first `duration-minutes` |

## hunger

See [Hunger Modes](Hunger-Modes.md). Keys: `mode`, `drain-per-second`, `min-hunger`, `drain-saturation`.

## ui

| Key | Default | Description |
|-----|---------|-------------|
| `enabled` | `true` | Master switch for stamina UI |
| `type` | `BOSS_BAR` | `ACTION_BAR`, `BOSS_BAR`, or `CHAT` |
| `update-threshold` | `0.5` | Min stamina change before UI refresh |
| `message-cooldown` | `0` | Ms between repeated messages (overexertion tick) |
| `low-stamina-warning` | `true` | Switch format below threshold |
| `low-stamina-threshold` | `25.0` | Percent for low-stamina format |
| `bar.length` | `10` | Characters in `%stamina_bar%` / `%shs_stamina_bar%` |
| `bar.filled-char` | `█` | Filled segment character |
| `bar.empty-char` | `░` | Empty segment character |

Format strings are in `messages.yml` → `ui.format` and `ui.low-stamina-format`. Placeholders: `%stamina%`, `%max_stamina%`, `%stamina_percent%`, `%hunger%`, `%stamina_bar%`.

## sounds

Optional feedback for exhaustion, low stamina, overexertion, second wind. Master switch: `sounds.enabled` (default false).

## gui

| Key | Default |
|-----|---------|
| `enabled` | `true` |

Requires `soapsstamina.admin` and a player sender for `/shs gui`.

## player-display-choice

| Key | Default | Description |
|-----|---------|-------------|
| `enabled` | `false` | Allow `/stamina display` per-player override |

## engine

| Key | Default | Description |
|-----|---------|-------------|
| `tick-interval` | `4` | Server ticks between engine passes |
| `movement-threshold` | `0.05` | Blocks moved to count as moving |
| `damage-movement-suppress-ms` | `500` | Brief movement drain pause after damage |

## overexertion

| Key | Default | Description |
|-----|---------|-------------|
| `enabled` | `true` | Overexertion damage system |
| `threshold` | `25.0` | Accumulation before damage starts |
| `base-damage` | `0.5` | Damage per tick at threshold |
| `scaling-enabled` | `true` | Scale damage with excess accumulation |
| `scaling-divisor` | `8.0` | Higher = gentler scaling |
| `max-damage` | `4.0` | Damage cap per tick |
| `recovery-rate` | `5.0` | Accumulation decay per second when not draining at 0 |
| `warning-threshold` | `0.75` | Fraction of threshold for warning message |

Bypass: `soapsstamina.bypass.overexertion`

## effects

Exhaustion visuals when stamina hits 0 (off by default). Sub-keys: `slowness`, `sweat-particles`, `heavy-breathing`, `stumble`, `recovery-animation`. Recovery when stamina rises above `recovery-threshold`.

Bypass: `soapsstamina.bypass.effects` and per-effect children.

## biomes

Off by default. Cold/hot biome lists, exposure timers, passive drain, freeze and sweat effects, encumbrance bonus in harsh biomes. Full biome list is in default `config.yml`.

Bypass: `soapsstamina.bypass.biomes`

## altitude

Off by default. High altitude (default Y 192+) and low depth (default Y 32-) add multipliers and passive drain.

Bypass: `soapsstamina.bypass.altitude`

## Live edits

- `/shs toggle <setting>` for booleans
- `/shs config set <group> <key> <value>` for numeric values (see [Commands and Permissions](Commands-and-Permissions.md))
- `/shs gui` for visual editing

All live edits trigger a reload internally.
