# Examples

## Light survival (vanilla-plus style)

Lower pressure, combat regen less punishing:

```yaml
# config.yml
hunger:
  mode: overflow
context:
  in-combat:
    regen-multiplier: 0.8

# actions.yml
sprint:
  drain-per-second: 0.7
jump:
  cost: 0.8
attack:
  cost: 0.6
block-interact:
  enabled: false
```

## RPG with strength-based carry

High stat lets warriors haul more without extra drain:

```yaml
# weight.yml
scaling-weight:
  enabled: true
  placeholder: "%mmocore_level%"
  per-point: 5.0
  cap: 200.0

scaling-drain:
  enabled: true
  placeholder: "%mmocore_attribute_strength%"
  stat-format: points
  stat-per-point: 6.0
  stress-per-ratio: 0.20
```

Requires PlaceholderAPI. Monitor `%shs_carry_burden%` on a test scoreboard while loading inventory.

## Hunger bar only (no boss bar)

```yaml
# config.yml
hunger:
  mode: bar
ui:
  enabled: false
```

Players read stamina from the vanilla food bar.

## Hardcore encumbrance

```yaml
# weight.yml
encumbrance:
  max-weight: 200.0
  severe-weight: 350.0
  encumbered-drain-multiplier: 1.6
  severe-drain-multiplier: 2.5
  block-sprint-severe: true
drowning:
  enabled: true
  air-loss-per-tick: 12
```

## PvP combat pacing

```yaml
# config.yml
context:
  pvp-pve:
    attack:
      pvp-multiplier: 1.3
    winded:
      pvp-multiplier: 1.5
  in-combat:
    regen-multiplier: 0.3
    allow-dodge: false

# actions.yml
winded:
  critical:
    regen-lock-duration: 3.5
regen-action-cooldown: 2000
```

## Enable dodge and sprint burst

```yaml
# actions.yml
dodge:
  enabled: true
  cost: 4.0
  cooldown-ms: 1500

sprint-burst:
  enabled: true
  min-stamina-percent: 75.0
  cost: 5.0
  cooldown-ms: 25000
```

Dodge: sneak while sprinting. Sprint burst: double-tap sprint within 400ms.

## Disable stamina in hub world

```yaml
# config.yml
general:
  disabled-worlds:
    stamina:
      - hub
    weight:
      - hub
```

## Custom item weight (MMOItems)

```yaml
# weight.yml
mmoitems-weight:
  enabled: true
  items:
    SWORD:RUBY_SWORD: 3.0
  type-defaults:
    SWORD: 2.0
```

## Scoreboard line

```
&aSTM &f%shs_stamina%&7/&f%shs_stamina_max% &8| &eWT &f%shs_weight% &7(%shs_encumbered%)
```

## Live tuning session

```
/shs toggle biomes
/shs config set sprint drain-per-second 1.0
/shs config set overexertion threshold 30
/shs weight encumbrance max-weight 280
/shs weight scaling-drain stat-per-point 7
```

Each command reloads config automatically.
