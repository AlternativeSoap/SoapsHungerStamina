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
  cooldown: 400
swim:
  enabled: true
  drain-per-second: 5.0
attack:
  enabled: true
  cost: 5.0
shield-block:
  enabled: true
  initial-cost: 4.0
  drain-per-second: 2.0
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
```

Every swing counts. Blocking drains hard. Getting hit (winded + damage-intake) punishes overcommitting. Sneaking between fights is the only way to recover. Building is free because it's a PvP arena. Potion effects add a drain boost so speed potions come at a cost.

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
  cooldown: 200
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
elytra:
  enabled: true
  drain-per-second: 0.4
boat:
  enabled: true
  drain-per-second: 0.15
climbing:
  enabled: true
  drain-per-second: 0.3
eating-regen:
  enabled: true
  regen-amount: 5.0
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

altitude:
  enabled: true
  high-threshold: 192
  high-multiplier: 1.10
  high-passive-drain: 0.2

effects:
  enabled: false
```

Travel is fun, stamina is a soft constraint, food is backup. Biomes and altitude add atmosphere without being brutal. Eating food restores 5.0 stamina as a nice bonus.

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
  cooldown: 350
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
shield-block:
  enabled: true
  initial-cost: 3.0
  drain-per-second: 1.5
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
  drain-per-second: 1.5
tool-use:
  enabled: true
  hoe-cost: 0.5
  shears-cost: 0.4
  brush-cost: 0.3
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

Stamina is critical. Hunger is deadly. Biomes and altitude punish you. Overexertion hits faster and harder. Carrying too much gear near water can kill you. Every action matters.

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
  cooldown: 250
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
eating-regen:
  enabled: true
  regen-amount: 4.0
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

Max carry weight increases by 5 per level (up to +200). Every point of strength reduces drain by 2% (up to 50% less). MMOItems get custom weights so your rare gear feels appropriately heavy. Eating food recovers stamina so food items have RPG value.
