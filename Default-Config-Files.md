# Default Config Files

What each default setting does and what files the plugin creates.

---

## What Gets Created

On first run, the plugin creates four files:

```
plugins/SoapsHungerStamina/
  ├── config.yml     (general, engine, projectiles, overexertion, hunger, effects, biomes, altitude, UI, GUI)
  ├── actions.yml    (all action drain/regen values)
  ├── messages.yml   (all player-facing text)
  └── weight.yml     (armor weights, encumbrance, scaling, drowning, fall damage, MMOItems weights, item weights)
```

All are fully editable. Run `/shs reload` to apply changes, or use `/shs gui` to change settings in-game.

---

## config.yml Defaults

### General

```yaml
general:
  bypass-permission: "soapsstamina.bypass"
  ignore-flying: true
  stop-sprint-on-empty: true
  debug: false
```

- `bypass-permission`: players with this permission skip all stamina/hunger drain
- `ignore-flying`: skips players in creative flight (elytra unaffected)
- `stop-sprint-on-empty`: forces sprinting to stop at 0 stamina
- `debug`: prints drain info to console (off by default)

### GUI

```yaml
gui:
  enabled: true
```

The `/shs gui` settings panel is available. Turn off to disable it (commands still work).

### Engine

```yaml
engine:
  tick-interval: 4
  movement-threshold: 0.05
```

Checks every 4 ticks (5 times per second), smooth and efficient. You need to move at least 0.05 blocks to count as "moving."

### Projectiles & Throwables

```yaml
projectiles:
  enabled: true
  bow:
    enabled: true
    cost: 1.5
    scale-with-charge: true
  crossbow:
    enabled: true
    cost: 1.8
  trident:
    enabled: true
    cost: 2.0
  throwables:
    enabled: true
    snowball: 0.3
    egg: 0.3
    ender-pearl: 1.0
    eye-of-ender: 0.5
    splash-potion: 0.5
    lingering-potion: 0.5
    experience-bottle: 0.3
    firework-rocket: 0.4
    fishing-rod: 0.2
    wind-charge: 0.5
```

All projectile costs are enabled by default. Bow shots can scale with draw charge (half-drawn = half cost). 10 throwable items are individually configurable.

### Overexertion

```yaml
overexertion:
  enabled: true
  threshold: 15.0
  base-damage: 1.0
  scaling-enabled: true
  scaling-divisor: 8.0
  max-damage: 6.0
  recovery-rate: 3.0
  warning-threshold: 0.75
```

When stamina is at 0 and the player keeps draining, overexertion accumulates. After 15 points of drain, damage starts at 1.0 (half a heart) per tick and scales up. Maximum 6.0 (3 hearts) per tick. Player is warned at 75% of the threshold. Recovers at 3.0 per second when resting.

### Hunger

```yaml
hunger:
  mode: overflow
  drain-per-second: 0.5
  min-hunger: 0
  drain-saturation: true
```

Three modes available: `overflow` (food drains when stamina is empty), `bar` (food bar shows stamina instead), `disabled` (no hunger interaction). Default is overflow at 0.5 food points per second. Can drain all the way to 0. Saturation goes first, then the food bar.

### Exhaustion Effects

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

Off by default. When you turn them on:
- Slowness I while exhausted (amplifier 0)
- 3 water drip particles per tick around the head
- Brief darkness flashes on screen edges
- 3% chance per tick of a small knockback stumble
- Everything clears once stamina gets above 10%

### Biomes

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
  freeze-particles:
    enabled: true
    count: 4
  encumbrance-biome-bonus: 0.10
```

Off by default. When enabled:
- Cold biomes drain 10% faster, plus 0.6/sec passive drain, freeze ticks, and freeze particles
- Hot biomes drain 8% faster, plus 0.5/sec passive drain and sweat particles
- Being encumbered in an extreme biome adds another 10% on top
- 36 biomes are pre-configured (20 cold, 11 hot, 5 nether with custom multipliers)

### Altitude

```yaml
altitude:
  enabled: false
  high-threshold: 192
  high-multiplier: 1.15
  high-passive-drain: 0.4
  low-threshold: 32
  low-multiplier: 1.12
  low-passive-drain: 0.3
```

Off by default. When enabled:
- Above Y 192: drain increases linearly up to 15% more at Y 320, plus 0.4/sec passive drain
- Below Y 32: drain increases linearly up to 12% more at Y -64, plus 0.3/sec passive drain
- Between the two thresholds: no altitude penalty

### UI

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

- Boss bar display by default (top of screen)
- Updates when stamina changes by 0.5 or more
- Warning format below 25% stamina
- Text bar disabled by default (enable and use `%stamina_bar%` in messages.yml)

---

## actions.yml Defaults

All action drain and regen values live in this file, separate from config.yml.

### Core Actions

```yaml
regen-action-cooldown: 2000

sprint:
  enabled: true
  drain-per-second: 1.0
jump:
  enabled: true
  cost: 1.5
  cooldown: 300
swim:
  enabled: true
  drain-per-second: 1.0
water-contact:
  enabled: true
  drain-per-second: 0.5
lava-contact:
  enabled: true
  drain-per-second: 1.5
block-place:
  enabled: true
  cost: 0.15
block-break:
  enabled: true
  cost: 0.3
sneak:
  enabled: true
  regen-per-second: 0.8
idle:
  enabled: true
  regen-per-second: 0.4
attack:
  enabled: true
  cost: 1.0
shield-block:
  enabled: true
  initial-cost: 0.6
  drain-per-second: 0.3
```

Quick math on the defaults:
- 100 stamina lasts ~100 seconds of sprinting
- 100 stamina = ~66 jumps
- 100 stamina = 100 seconds of swimming
- 100 stamina = 100 melee hits
- 100 stamina = ~666 blocks placed
- Sneaking regens 0.8/sec on top of MMOCore's natural regen (after a 2s cooldown)
- Standing still regens 0.4/sec extra (after the same cooldown)

### Winded

```yaml
winded:
  enabled: true
  refresh-on-hit: true
  normal:
    instant-cost: 0.5
    drain-per-second: 0.6
    duration: 3.5
  critical:
    instant-cost: 1.5
    drain-per-second: 1.2
    duration: 5.0
    regen-lock-duration: 3.0
```

Taking damage costs stamina. A normal hit drains 0.5 instantly + 0.6/sec for 3.5 seconds (2.6 total). A critical hit drains 1.5 instantly + 1.2/sec for 5 seconds (7.5 total) and blocks all regen for 3 seconds.

### Extended Actions

```yaml
elytra:
  enabled: true
  drain-per-second: 0.8
climbing:
  enabled: true
  drain-per-second: 0.6
eating-regen:
  enabled: true
  regen-amount: 3.0
mace:
  enabled: true
  cost: 2.5
potion-modifiers:
  enabled: false
  speed-multiplier: 1.15
  haste-multiplier: 1.10
damage-intake:
  enabled: true
  cost-per-heart: 0.5
boat:
  enabled: true
  drain-per-second: 0.3
crawling:
  enabled: true
  drain-per-second: 0.5
riptide:
  enabled: true
  cost: 2.5
tool-use:
  enabled: true
  hoe-cost: 0.2
  shears-cost: 0.15
  brush-cost: 0.1
powder-snow:
  enabled: true
  drain-per-second: 0.7
slime-bounce:
  enabled: true
  cost: 0.5
soul-sand:
  enabled: true
  drain-multiplier: 1.20
honey-block:
  enabled: true
  drain-multiplier: 1.15
```

Most extended actions are enabled by default except `potion-modifiers` (disabled). Each has its own bypass permission.

---

## messages.yml Defaults

Controls all player-facing text. Everything uses [MiniMessage formatting](https://docs.advntr.dev/minimessage/).

Key sections:
- `prefix` — gradient-colored plugin name added to all messages
- `command.*` — responses for every command (stamina, weight, toggle, config set, help)
- `exhaustion.*` — "You are exhausted" / "strength returning" messages
- `encumbrance.*` — weight warning/recovery messages and drowning warning
- `winded.*` — normal hit, critical hit, and recovery messages
- `overexertion.*` — warning, damage start, damage tick, and recovery messages
- `biome.*` — climate change messages (entering cold/hot/neutral biomes)
- `ui.format` — normal stamina display
- `ui.low-stamina-format` — warning display when low
- `gui.*` — all text in the admin settings GUI (titles, labels, setting names, value names)

---

## weight.yml Defaults

Controls the weight/encumbrance system.

### Armor Weight

Armor uses a per-piece weight system. The total drain multiplier is `1.0 + sum(equipped piece weights)`. Each piece adds a small amount:

| Material | Helmet | Chestplate | Leggings | Boots | Full Set |
|---|---|---|---|---|---|
| Leather | 0.01 | 0.02 | 0.015 | 0.01 | 1.055 (5.5% more drain) |
| Chainmail | 0.02 | 0.04 | 0.03 | 0.02 | 1.11 (11% more drain) |
| Gold | 0.025 | 0.05 | 0.04 | 0.025 | 1.14 (14% more drain) |
| Iron | 0.04 | 0.08 | 0.06 | 0.04 | 1.22 (22% more drain) |
| Diamond | 0.05 | 0.10 | 0.08 | 0.05 | 1.28 (28% more drain) |
| Netherite | 0.07 | 0.13 | 0.10 | 0.07 | 1.37 (37% more drain) |
| Turtle | 0.035 | — | — | — | (helmet only) |

### Encumbrance Thresholds

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

- `max-weight`: 300 — above this, you're "encumbered" (message + faster drain + Slowness I)
- `severe-weight`: 500 — above this, you're "severely encumbered" (Slowness II + sprint blocked + drowning + fall damage)
- `encumbered-drain-multiplier`: 1.4 (40% faster drain when encumbered)
- `severe-drain-multiplier`: 2.0 (double drain when severely encumbered)
- `swim-slowness-bonus`: 2 extra slowness levels when encumbered and in water
- `default-weight`: 0.25 (weight for any item not explicitly listed)
- `container-weight`: true — shulker boxes and bundles include their contents' weight

### Drowning & Fall Damage

```yaml
drowning:
  enabled: true
  air-loss-per-tick: 8

fall-damage:
  enabled: true
  max-multiplier: 1.75
```

- Severely encumbered players lose 8 air ticks per engine tick underwater
- Fall damage scales up to 75% more at max weight

### Scaling

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

Both disabled by default. Requires PlaceholderAPI. Lets max carry weight grow with level, and stamina drain decrease with attributes (or any placeholder value). Scaling-weight also supports multiple sources via a `sources:` list.

### MMOItems Custom Weights

```yaml
mmoitems-weight:
  enabled: false
  items:
    SWORD:CUTLASS: 2.5
    SWORD:RUBY_SWORD: 3.0
    BOW:MARKSMAN_BOW: 1.8
    ARMOR:MITHRIL_ARMOR: 10.0
  type-defaults:
    SWORD: 2.0
    BOW: 1.5
    ARMOR: 6.0
```

Disabled by default. Requires MMOItems. Override weight for specific items by `TYPE:ITEM_ID`, or set default weights for entire item types. Priority: specific item → type default → vanilla material weight.

### Item Weights

The plugin ships with over 1000 item weight entries covering all survival-obtainable items. Some examples:
- Stone/ore blocks: 1.0–1.5
- Dirt/sand: 0.6–0.9
- Wood logs/planks: 0.5–0.8
- Tools (pickaxe, sword): 2.0–4.0
- Heavy blocks (anvil, enchanting table): 10.0–15.0
- Light items (sticks, seeds): 0.1–0.3

Unlisted items use the `default-weight` (0.25). The full list is in weight.yml and can be customized per item or managed with `/shs weight` commands.
