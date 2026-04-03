# Configuration

All settings live in `plugins/SoapsHungerStamina/config.yml`.

You can either edit the file and run `/shs reload`, or use the in-game GUI with `/shs gui`.

---

## General

```yaml
general:
  bypass-permission: "soapsstamina.bypass"
  ignore-flying: true
  stop-sprint-on-empty: true
  debug: false
```

`bypass-permission` - players with this permission skip all stamina and hunger drain. Give it to staff or event ranks. Per-action bypass permissions are also available (see [Commands & Permissions](Commands-and-Permissions.md)).

`ignore-flying` - skips players in creative flight. Elytra flight is not affected by this.

`stop-sprint-on-empty` - forces players to stop sprinting when stamina hits 0. Without this, they'd keep sprinting while hunger drains.

`debug` - prints drain info to the console. Only turn this on when you're testing.

---

## GUI

```yaml
gui:
  enabled: true
```

`enabled` - turns the in-game settings panel on or off. When off, `/shs gui` tells the player it's disabled. All commands (`/shs toggle`, `/shs config set`, etc.) still work regardless.

---

## Actions

There are 12 action types. Each one can be turned on/off separately.

```yaml
actions:
  regen-action-cooldown: 2000

  sprint:
    enabled: true
    drain-per-second: 1.2

  jump:
    enabled: true
    cost: 2.0
    cooldown: 300

  swim:
    enabled: true
    drain-per-second: 1.0

  water-contact:
    enabled: true
    drain-per-second: 0.5

  lava-contact:
    enabled: true
    drain-per-second: 2.0

  block-place:
    enabled: true
    cost: 0.15

  block-break:
    enabled: true
    cost: 0.4

  sneak:
    enabled: true
    regen-per-second: 0.8

  idle:
    enabled: true
    regen-per-second: 0.4

  attack:
    enabled: true
    cost: 1.2

  shield-block:
    enabled: true
    initial-cost: 0.8
    drain-per-second: 0.3
```

`regen-action-cooldown` - milliseconds after any draining action before sneak and idle regen kick in. Prevents players from instantly recovering by sprint-crouch cycling. 2000 = 2 seconds.

`sprint.drain-per-second` - stamina lost every second while sprinting and actually moving. Standing still while holding sprint doesn't count.

`jump.cost` - flat cost per jump. The cooldown stops rapid jumps from all counting.

`jump.cooldown` - milliseconds between jumps that cost stamina. 300ms means about 3 jumps per second max.

`swim.drain-per-second` - stamina lost per second while actively swimming.

`water-contact.drain-per-second` - stamina lost per second while in water but not swimming (wading, floating, standing in shallow water).

`lava-contact.drain-per-second` - stamina lost per second while touching lava. High by default because lava is already dangerous.

`block-place.cost` / `block-break.cost` - stamina cost each time you place or break a block.

`sneak.regen-per-second` - bonus stamina recovery per second while sneaking. Adds on top of MMOCore's natural regen. Subject to the regen action cooldown.

`idle.regen-per-second` - bonus stamina recovery per second while standing still. Smaller than sneak but still helpful. Also subject to the regen action cooldown.

`attack.cost` - stamina cost per melee hit. If MMOItems is installed and the weapon already applied a stamina cost through MythicLib, this drain is skipped to avoid double-charging.

`shield-block.initial-cost` - one-time cost when you raise your shield.

`shield-block.drain-per-second` - ongoing cost while your shield stays up.

---

## Winded

Taking damage drains stamina. Critical hits are harsher and lock out all regen.

```yaml
  winded:
    enabled: true
    refresh-on-hit: true
    normal:
      instant-cost: 2.0
      drain-per-second: 1.0
      duration: 5.0
    critical:
      instant-cost: 4.0
      drain-per-second: 2.0
      duration: 8.0
      regen-lock-duration: 5.0
```

`refresh-on-hit` - getting hit again restarts the winded timer. When disabled, a new hit doesn't extend the effect.

`normal.instant-cost` - stamina drained immediately when hit.

`normal.drain-per-second` - ongoing stamina drain per second after the hit.

`normal.duration` - how long the drain-over-time lasts in seconds.

`critical.instant-cost` - stamina drained immediately on a critical hit (higher than normal).

`critical.drain-per-second` - ongoing drain per second after a critical hit.

`critical.duration` - how long the critical drain lasts. Longer than normal.

`critical.regen-lock-duration` - seconds during which ALL stamina regen is completely blocked. No MMOCore regen, no sneak regen, no idle regen. This is the most punishing mechanic in the plugin.

---

## Overexertion

When stamina is at zero and the player keeps performing draining actions, overexertion accumulates. Pass the threshold and they start taking real damage.

```yaml
overexertion:
  enabled: true
  threshold: 12.0
  base-damage: 1.0
  scaling-enabled: true
  scaling-divisor: 8.0
  max-damage: 8.0
  recovery-rate: 2.5
  warning-threshold: 0.75
```

`threshold` - how much total drain at zero stamina before damage starts. Acts as a grace period. Small actions won't immediately hurt.

`base-damage` - hearts of damage per engine tick once past the threshold. 1.0 = half a heart, 2.0 = one heart.

`scaling-enabled` - damage increases the deeper into overexertion you go. Formula: `damage = base-damage + (overflow / scaling-divisor)`.

`scaling-divisor` - lower values make damage ramp up faster.

`max-damage` - cap on damage per engine tick. 8.0 = 4 hearts per tick, lethal if sustained.

`recovery-rate` - how fast overexertion resets per second when the player stops draining. Higher = faster recovery.

`warning-threshold` - percentage of the threshold at which the warning message is sent. 0.75 means warn at 75% before damage begins.

---

## Hunger Overflow

When stamina hits zero and the player keeps doing stuff, their food bar starts draining.

```yaml
hunger:
  enabled: true
  drain-per-second: 0.5
  min-hunger: 0
  drain-saturation: true
```

`drain-per-second` - how fast the food bar drops. 1 point = half a food shank.

`min-hunger` - the food bar won't go below this number (0-20). Set it to 3 or 4 if you don't want players to fully starve from stamina drain.

`drain-saturation` - if true, the golden saturation drains first before the actual food bar. Matches how vanilla hunger works.

---

## Hunger Bar Mode

```yaml
hunger-bar:
  enabled: false
```

Turns the vanilla food bar into a stamina display. Your stamina percentage (0-100%) maps to the food bar (0-20 shanks). Vanilla hunger mechanics are paused while this is on.

Only use this if you want a completely different visual approach.

---

## Engine

```yaml
engine:
  tick-interval: 4
  movement-threshold: 0.05
```

`tick-interval` - how often the plugin runs its checks, in server ticks. 20 ticks = 1 second. Lower numbers = smoother drain but more CPU. 4 is a good balance.

`movement-threshold` - how far (in blocks) a player needs to move to count as "moving." Prevents stamina draining while standing still. 0.05 is fine for normal play.

---

## Exhaustion Effects

Bad stuff that happens when stamina hits 0. Disabled by default.

```yaml
effects:
  enabled: false
  recovery-threshold: 10.0

  slowness:
    enabled: true
    amplifier: 0

  sweat-particles:
    enabled: true
    count: 3

  heavy-breathing:
    enabled: true

  stumble:
    enabled: true
    chance: 0.03
    strength: 0.1
```

`recovery-threshold` - the player has to regen past this stamina percentage before effects go away. At 10%, effects stick around until they get above 10% stamina.

`slowness.amplifier` - 0 = Slowness I, 1 = Slowness II, etc.

`sweat-particles.count` - water drip particles spawned per engine tick. More = more visible.

`heavy-breathing` - brief darkness pulses on the screen edges. On or off, no extra settings.

`stumble.chance` - chance per engine tick (0.0 to 1.0). 0.03 = 3% chance each tick.

`stumble.strength` - how hard the knockback pushes. 0.1 is subtle.

---

## Biomes

Cold biomes freeze you and drain stamina faster. Hot biomes make you sweat and drain faster. Disabled by default.

```yaml
biomes:
  enabled: false
  cold-drain-multiplier: 1.10
  hot-drain-multiplier: 1.08

  cold-passive-drain: 0.6
  hot-passive-drain: 0.5

  freeze:
    enabled: true
    ticks-per-tick: 1

  sweat:
    enabled: true
    count: 4

  encumbrance-biome-bonus: 0.10
```

`cold-drain-multiplier` - how much faster stamina drains in cold biomes. 1.10 = 10% faster.

`hot-drain-multiplier` - same thing for hot biomes. 1.08 = 8% faster.

`cold-passive-drain` - extra stamina drained per second just for standing in a cold biome, even if you're not doing anything.

`hot-passive-drain` - same for hot biomes.

`freeze.ticks-per-tick` - how many freeze ticks get added per engine tick in cold biomes. Higher = freezes faster.

`sweat.count` - water drip particles per engine tick in hot biomes.

`encumbrance-biome-bonus` - if the player is also carrying too much weight, the biome drain gets even worse. This multiplier stacks on top.

### Biome List

Below the settings, there's a `list:` section where you define which biomes are hot or cold. You can also manage this through the in-game GUI's Biome Settings page.

```yaml
  list:
    SNOWY_PLAINS:
      type: cold
    DESERT:
      type: hot
    NETHER_WASTES:
      type: hot
      multiplier: 1.50
```

`type` - set to `hot` or `cold`. Controls whether the biome causes sweat or freeze, and uses the default drain multiplier.

`multiplier` - optional. Overrides the default drain multiplier for that specific biome. Useful for places like the Nether where you want higher drain.

You can also set just a multiplier with no type, which changes the drain without adding freeze or sweat effects.

---

## Encumbrance

Extra penalties for carrying too much weight. The weight thresholds and item weights are in `weight.yml`.

The encumbrance config in weight.yml controls:

```yaml
encumbrance:
  enabled: true
  max-weight: 300.0
  severe-weight: 500.0
  encumbered-drain-multiplier: 1.4
  severe-drain-multiplier: 2.0
  encumbered-slowness: 0
  severe-slowness: 1
  block-sprint-severe: true
  swim-slowness-bonus: 2
  default-weight: 0.25
  container-weight: true
```

`max-weight` - total inventory weight threshold for normal encumbrance.

`severe-weight` - threshold for severe encumbrance.

`encumbered-drain-multiplier` / `severe-drain-multiplier` - stamina drain multiplier at each tier. 1.4 = 40% more drain.

`encumbered-slowness` / `severe-slowness` - slowness amplifier at each tier (0 = Slowness I).

`block-sprint-severe` - prevents sprinting when severely encumbered.

`swim-slowness-bonus` - extra slowness amplifier when encumbered and in water.

`default-weight` - weight for items not listed in the items section.

`container-weight` - when true, shulker boxes and bundles weigh their contents plus the container itself.

### Drowning & Fall Damage

```yaml
drowning:
  enabled: true
  air-loss-per-tick: 8

fall-damage:
  enabled: true
  max-multiplier: 1.75
```

`drowning.air-loss-per-tick` - severely encumbered players lose this many air ticks per engine tick when underwater. Vanilla provides 300 air ticks total (15 seconds), so 8 per tick drains it noticeably faster.

`fall-damage.max-multiplier` - fall damage is multiplied by up to this amount at max weight. 1.75 = 75% more fall damage when fully loaded.

### Scaling (PlaceholderAPI)

Both scaling features require PlaceholderAPI.

```yaml
scaling-weight:
  enabled: false
  placeholder: "%mmocore_level%"
  per-point: 5.0
  cap: 200.0

scaling-drain:
  enabled: false
  placeholder: "%mmocore_attribute_strength%"
  per-point: 0.02
  cap: 0.50
```

`scaling-weight` - increases max carry weight based on a placeholder value. Bonus = placeholder value x per-point, capped at cap. At level 20 with default settings: 20 x 5.0 = 100 extra carry capacity.

`scaling-drain` - reduces all stamina drain based on a placeholder value. At 10 strength with defaults: 10 x 0.02 = 20% less drain. Capped at 50%.

---

## UI Display

```yaml
ui:
  type: BOSS_BAR
  update-threshold: 0.5
  message-cooldown: 0
  low-stamina-warning: true
  low-stamina-threshold: 25.0
  bar:
    enabled: false
    length: 10
    filled-char: "█"
    empty-char: "░"
```

`type` - where stamina is shown. `ACTION_BAR` (above the hotbar), `BOSS_BAR` (top of screen), or `CHAT` (chat messages).

`update-threshold` - how much stamina has to change before the display refreshes. Prevents flickering on tiny changes.

`message-cooldown` - milliseconds between display updates. For CHAT mode, set this to 2000-5000 so it doesn't spam.

`low-stamina-warning` - shows a different colored format when stamina drops below the threshold.

`low-stamina-threshold` - what percentage counts as "low." 25 means the warning kicks in below 25% stamina.

`bar` - a text-based stamina bar using characters. When enabled, you can use `%stamina_bar%` in your messages.yml format strings.

---

## Messages

All player-facing text is in `plugins/SoapsHungerStamina/messages.yml`.

Everything supports [MiniMessage formatting](https://docs.advntr.dev/minimessage/) for colors, gradients, bold, etc.

Key sections:
- `prefix` - the colored tag added to every message
- `command.*` - all command responses
- `exhaustion.*` - messages when effects activate/clear
- `encumbrance.*` - messages for weight thresholds
- `winded.*` - messages when getting hit (normal and critical)
- `overexertion.*` - warning, damage, and recovery messages
- `biome.*` - messages when entering hot/cold/neutral biomes
- `ui.format` - the stamina display format
- `ui.low-stamina-format` - warning display when low
- `gui.*` - all text shown in the admin settings GUI

---

## Weight

Item weights are in `plugins/SoapsHungerStamina/weight.yml`.

This file controls:
- Armor weight multipliers and how much each armor piece affects stamina drain
- Encumbrance thresholds for "encumbered" and "severely encumbered"
- Drowning and fall damage penalties
- Scaling rules for PlaceholderAPI-based bonuses
- Per-item weights so every item type can have a custom weight

See [Default Config Files](Default-Config-Files.md) for details on the weight system.
