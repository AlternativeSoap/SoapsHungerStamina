# Configuration

All settings live in `plugins/SoapsHungerStamina/config.yml`.

You can either edit the file and run `/shs reload`, or use the in-game GUI with `/shs gui`.

---

## General

```yaml
general:
  bypass-permission: "soapsstamina.bypass"
  stop-sprint-on-empty: true
  debug: false
```

`bypass-permission` - players with this permission skip all stamina and hunger drain. Give it to staff or event ranks.

`stop-sprint-on-empty` - forces players to stop sprinting when stamina hits 0. Without this, they'd keep sprinting while hunger drains, which feels weird.

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

There are 8 actions. Each one can be turned on/off separately.

```yaml
actions:
  sprint:
    enabled: true
    drain-per-second: 2.5

  jump:
    enabled: true
    cost: 4.0
    cooldown: 300

  swim:
    enabled: true
    drain-per-second: 2.0

  block-place:
    enabled: true
    cost: 0.3

  block-break:
    enabled: true
    cost: 0.8

  sneak:
    enabled: true
    regen-per-second: 1.5

  attack:
    enabled: true
    cost: 2.5

  shield-block:
    enabled: true
    initial-cost: 1.5
    drain-per-second: 0.5
```

`sprint.drain-per-second` - stamina lost every second while sprinting and actually moving. Standing still while holding sprint doesn't count.

`jump.cost` - flat cost per jump. The cooldown stops rapid double-jumps from all counting.

`jump.cooldown` - milliseconds between jumps that cost stamina. 300ms means about 3 jumps per second max.

`swim.drain-per-second` - stamina lost per second while in water.

`block-place.cost` / `block-break.cost` - stamina cost each time you place or break a block.

`sneak.regen-per-second` - bonus stamina recovery per second while sneaking. This adds on top of MMOCore's natural regen.

`attack.cost` - stamina cost per melee hit.

`shield-block.initial-cost` - one-time cost when you raise your shield.

`shield-block.drain-per-second` - ongoing cost while your shield stays up.

---

## Hunger Overflow

When stamina hits zero and the player keeps doing stuff, their food bar starts draining.

```yaml
hunger:
  enabled: true
  drain-per-second: 1.0
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
  recovery-threshold: 15.0

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

`recovery-threshold` - the player has to regen past this stamina percentage before effects go away. At 15%, effects stick around until they get above 15% stamina.

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
  cold-drain-multiplier: 1.15
  hot-drain-multiplier: 1.10

  freeze:
    enabled: true
    ticks-per-tick: 1

  sweat:
    enabled: true
    count: 4

  encumbrance-biome-bonus: 0.15
```

`cold-drain-multiplier` - how much faster stamina drains in cold biomes. 1.15 = 15% faster.

`hot-drain-multiplier` - same thing for hot biomes. 1.10 = 10% faster.

`freeze.ticks-per-tick` - how many freeze ticks get added per engine tick in cold biomes. Higher = freezes faster.

`sweat.count` - water drip particles per engine tick in hot biomes.

`encumbrance-biome-bonus` - if the player is also carrying too much weight, the biome drain gets even worse. This multiplier stacks on top.

### Biome List

Below the settings, there's a `list:` section where you define which biomes are hot or cold.

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

```yaml
encumbrance:
  drowning:
    enabled: true
    air-loss-per-tick: 8

  fall-damage:
    enabled: true
    max-multiplier: 1.75
```

`drowning.air-loss-per-tick` - severely encumbered players lose this many air ticks per engine tick when underwater. Vanilla gives you 300 air ticks total (15 seconds), so 8 per tick drains it fast.

`fall-damage.max-multiplier` - fall damage is multiplied by up to this amount at max weight. 1.75 = 75% more fall damage when fully loaded.

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
- `biome.*` - messages when entering hot/cold/neutral biomes
- `ui.format` - the stamina display format
- `ui.low-stamina-format` - warning display when low
- `gui.*` - all text shown in the admin settings GUI

---

## Weight

Item weights are in `plugins/SoapsHungerStamina/weight.yml`.

This file controls:
- Armor weight multipliers and how much each armor piece slows stamina drain
- Encumbrance thresholds for "encumbered" and "severely encumbered"
- Per-item weights so every item type can have a custom weight

See [Default Config Files](Default-Config-Files.md) for details on the weight system.
