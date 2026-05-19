# Examples

Preset configs for different server styles. Action values go in `actions.yml`, everything else in `config.yml`. Run `/shs reload` after editing.

---

## PvP Arena (Short, Intense Fights)

High costs so stamina management matters in combat. Attacking, shielding, and getting hit are all expensive.

**actions.yml:**
```yaml
sprint:
  enabled: true
  drain-per-second: 8.0
jump:
  enabled: true
  cost: 10.0
swim:
  enabled: true
  drain-per-second: 5.0
attack:
  enabled: true
  cost: 5.0
  weapon-costs:
    enabled: true
    sword: 4.0
    axe: 7.0
    trident: 6.0
    fist: 2.0
shield-block:
  enabled: true
  initial-cost: 4.0
  drain-per-second: 2.0
  min-stamina: 5.0
  damage-cost: 3.0
block-place:
  enabled: false
block-break:
  enabled: false
sneak:
  enabled: true
  regen-per-second: 3.0
winded:
  enabled: true
  refresh-on-hit: true
  normal:
    instant-cost: 2.0
    drain-per-second: 1.5
    duration: 4.0
  critical:
    instant-cost: 5.0
    drain-per-second: 3.0
    duration: 6.0
    regen-lock-duration: 4.0
damage-intake:
  enabled: true
  cost-per-heart: 1.5
mace:
  enabled: true
  cost: 5.0
potion-modifiers:
  enabled: true
  speed-multiplier: 1.25
  haste-multiplier: 1.15
```

**config.yml:**
```yaml
hunger:
  mode: overflow
  drain-per-second: 2.0
  min-hunger: 4

overexertion:
  enabled: true
  threshold: 10.0
  max-damage: 8.0

effects:
  enabled: true
  recovery-threshold: 15.0
  stumble:
    enabled: true
    chance: 0.08
    strength: 0.15

dodge:
  enabled: true
  cost: 6.0
  cooldown-ms: 2000
  velocity: 1.5
  invulnerable-ticks: 10

sprint-burst:
  enabled: true
  min-stamina-percent: 90.0
  cost: 8.0
  speed-amplifier: 1
  duration-ticks: 40
  cooldown-ms: 20000

sounds:
  enabled: true
```

Every swing counts. Weapon-type costs mean axes hit harder but drain more. Shield drops at 5 stamina and eats 3.0 per blocked hit — turtling is expensive. Dodge lets skilled players escape combos. Sprint burst rewards patient play. Building is free because it's a PvP arena.

---

## Survival Exploration (Chill Travel)

Low costs so travel doesn't feel punishing. Biomes and altitude add flavor. Elytra and boats have a small cost.

**actions.yml:**
```yaml
sprint:
  enabled: true
  drain-per-second: 1.0
jump:
  enabled: true
  cost: 1.5
swim:
  enabled: true
  drain-per-second: 0.5
block-place:
  enabled: true
  cost: 0.1
block-break:
  enabled: true
  cost: 0.3
sneak:
  enabled: true
  regen-per-second: 2.0
attack:
  enabled: true
  cost: 1.0
shield-block:
  enabled: true
  initial-cost: 0.5
  drain-per-second: 0.2
  min-stamina: 1.0
  damage-cost: 0.3
elytra:
  enabled: true
  drain-per-second: 0.4
boat:
  enabled: true
  drain-per-second: 0.15
climbing:
  enabled: true
  drain-per-second: 0.3
soul-sand:
  enabled: true
  drain-multiplier: 1.10
honey-block:
  enabled: true
  drain-multiplier: 1.05
```

**config.yml:**
```yaml
hunger:
  mode: overflow
  drain-per-second: 0.5
  min-hunger: 3

biomes:
  enabled: true
  cold-drain-multiplier: 1.10
  hot-drain-multiplier: 1.05
  exposure:
    cold-duration: 90
    hot-duration: 75

altitude:
  enabled: true
  high-threshold: 192
  high-multiplier: 1.10
  high-passive-drain: 0.2

effects:
  enabled: false

stamina-food:
  enabled: true

bed-rest:
  enabled: true
  restore-percent: 1.0
  buff-duration-seconds: 180
  buff-drain-reduction: 0.50
```

Travel is fun, stamina is a soft constraint, food gives stamina back. Biomes and altitude add atmosphere with longer grace periods so they don't ambush you. Sleeping gives full stamina plus a generous 3-minute Well Rested buff (50% drain reduction) for morning exploration.

---

## Hardcore (Everything Hurts)

Stamina is a real survival resource. Weight matters. Biomes are dangerous. Every action drains hard.

**actions.yml:**
```yaml
sprint:
  enabled: true
  drain-per-second: 6.0
jump:
  enabled: true
  cost: 8.0
swim:
  enabled: true
  drain-per-second: 4.0
block-place:
  enabled: true
  cost: 1.0
block-break:
  enabled: true
  cost: 2.0
sneak:
  enabled: true
  regen-per-second: 1.0
attack:
  enabled: true
  cost: 4.0
  weapon-costs:
    enabled: true
    sword: 3.0
    axe: 5.0
    trident: 4.5
    fist: 1.5
shield-block:
  enabled: true
  initial-cost: 3.0
  drain-per-second: 1.5
  min-stamina: 3.0
  damage-cost: 2.0
elytra:
  enabled: true
  drain-per-second: 2.0
climbing:
  enabled: true
  drain-per-second: 1.5
damage-intake:
  enabled: true
  cost-per-heart: 1.0
winded:
  enabled: true
  refresh-on-hit: true
  normal:
    instant-cost: 1.5
    drain-per-second: 1.0
    duration: 5.0
  critical:
    instant-cost: 4.0
    drain-per-second: 2.5
    duration: 7.0
    regen-lock-duration: 5.0
crawling:
  enabled: true
  drain-per-second: 1.0
riptide:
  enabled: true
  cost: 5.0
powder-snow:
  enabled: true
  exposure-multiplier: 3.0
tool-use:
  enabled: true
  hoe-cost: 0.5
  shears-cost: 0.4
  brush-cost: 0.3
  flint-and-steel-cost: 0.4
```

**config.yml:**
```yaml
hunger:
  mode: overflow
  drain-per-second: 1.5
  min-hunger: 0
  drain-saturation: true

overexertion:
  enabled: true
  threshold: 8.0
  max-damage: 10.0
  recovery-rate: 1.5

second-wind:
  enabled: false

effects:
  enabled: true
  recovery-threshold: 20.0
  stumble:
    enabled: true
    chance: 0.10
    strength: 0.15

biomes:
  enabled: true
  cold-drain-multiplier: 1.30
  hot-drain-multiplier: 1.25
  exposure:
    cold-duration: 30
    hot-duration: 20
    decay-rate: 1.0
  encumbrance-biome-bonus: 0.25

altitude:
  enabled: true
  high-threshold: 160
  high-multiplier: 1.25
  high-passive-drain: 0.8
  low-threshold: 48
  low-multiplier: 1.20
  low-passive-drain: 0.6

projectiles:
  enabled: true
  bow:
    cost: 3.0
  crossbow:
    cost: 4.0
  trident:
    cost: 5.0

stamina-food:
  enabled: true

bed-rest:
  enabled: true
  restore-percent: 0.50
  buff-enabled: false

sounds:
  enabled: true
```

**weight.yml:**
```yaml
encumbrance:
  max-weight: 200.0
  severe-weight: 350.0
  encumbered-drain-multiplier: 1.6
  severe-drain-multiplier: 2.5

drowning:
  enabled: true
  air-loss-per-tick: 12

fall-damage:
  enabled: true
  max-multiplier: 2.5
```

Stamina is critical. Hunger is deadly. Biomes and altitude punish you with short grace periods (30s cold, 20s hot). Overexertion hits faster and harder. Carrying too much gear near water can kill you. Second wind is disabled — no free recovery. Bed rest only gives back 50% stamina and no buff. Weapon costs make every swing a strategic choice. Sounds are on so players hear when they're in danger.

---

## Parkour (Jump Only)

Only jumping costs stamina. Everything else is free. No hunger, no weight.

**actions.yml:**
```yaml
sprint:
  enabled: false
jump:
  enabled: true
  cost: 2.0
swim:
  enabled: false
block-place:
  enabled: false
block-break:
  enabled: false
sneak:
  enabled: false
attack:
  enabled: false
shield-block:
  enabled: false
elytra:
  enabled: false
climbing:
  enabled: false
winded:
  enabled: false
```

**config.yml:**
```yaml
hunger:
  mode: disabled

overexertion:
  enabled: false
```

---

## RPG Server (Scaling with Levels)

Stamina improves as players level up. Combine with MMOCore attributes for a full RPG feel.

**actions.yml:**
```yaml
sprint:
  enabled: true
  drain-per-second: 1.5
jump:
  enabled: true
  cost: 2.0
attack:
  enabled: true
  cost: 1.5
  weapon-costs:
    enabled: true
    sword: 1.0
    axe: 2.0
    trident: 1.8
    fist: 0.5
mace:
  enabled: true
  cost: 3.0
elytra:
  enabled: true
  drain-per-second: 1.0
potion-modifiers:
  enabled: true
  speed-multiplier: 1.15
  haste-multiplier: 1.10
```

**config.yml:**
```yaml
hunger:
  mode: overflow
  drain-per-second: 0.3

overexertion:
  enabled: true
  threshold: 20.0
  max-damage: 4.0

second-wind:
  enabled: true
  idle-seconds: 4.0
  recovery-percent: 0.25
  cooldown-seconds: 60.0

stamina-food:
  enabled: true

dodge:
  enabled: true
  cost: 3.0
  cooldown-ms: 2000
  velocity: 1.0
  invulnerable-ticks: 15

sprint-burst:
  enabled: true
  min-stamina-percent: 75.0
  cost: 5.0

bed-rest:
  enabled: true
  buff-duration-seconds: 180
  buff-drain-reduction: 0.50

player-display-choice:
  enabled: true

sounds:
  enabled: true
```

**weight.yml:**
```yaml
scaling-weight:
  enabled: true
  placeholder: "%mmocore_level%"
  per-point: 5.0
  cap: 200.0

scaling-drain:
  enabled: true
  placeholder: "%mmocore_attribute_strength%"
  per-point: 0.02
  cap: 0.50

mmoitems-weight:
  enabled: true
  type-defaults:
    SWORD: 2.0
    BOW: 1.5
    ARMOR: 6.0
  items:
    SWORD:CUTLASS: 2.5
    ARMOR:MITHRIL_ARMOR: 10.0
```

Max carry weight increases by 5 per level (up to +200). Every point of strength reduces drain by 2% (up to 50% less). MMOItems get custom weights so your rare gear feels appropriately heavy. Stamina food gives your golden apples and cooked meats RPG value. Weapon costs differentiate playstyles — sword fighters are more efficient than axe users. Dodge and sprint burst add action-RPG flair. Second wind prevents complete wipe-outs. Players can pick their own UI display style. Sleeping gives a generous Well Rested buff for morning adventures.
