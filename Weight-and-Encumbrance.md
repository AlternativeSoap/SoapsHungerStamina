# Weight and Encumbrance

File: `plugins/SoapsHungerStamina/weight.yml`

Inventory weight drives encumbrance tiers, armor drain multipliers, and optional RPG scaling.

## Encumbrance tiers

| Tier | Threshold (default) | Effects |
|------|---------------------|---------|
| Normal | under 300 | None |
| Encumbered | 300+ (`max-weight`) | 1.4x drain, slowness I |
| Severe | 500+ (`severe-weight`) | 2.0x drain, slowness II, sprint blocked |

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
  container-max-depth: 3
```

Bypass: `soapsstamina.bypass.encumbrance`

Per-player cap override: permission `soapsstamina.maxweight.<number>` (e.g. `soapsstamina.maxweight.500`).

## Item weights

- `items:` map lists per-material weights. Stack weight = unit weight x stack size.
- Unlisted materials use `encumbrance.default-weight`.
- `container-weight: true` counts shulker, bundle, and nested contents up to `container-max-depth`.
- Ender chest contents are not weighed (server-side storage).

Weight resolution order for custom items:

MMOItems → ExecutableItems → EcoItems → MythicCrucible → `items:` → `custom-items` → default-weight

## Armor weight

Separate from inventory weight. Equipped armor adds a global drain multiplier:

```yaml
armor-weight:
  enabled: true
  pieces:
    IRON_CHESTPLATE: 0.04
```

Example: full iron adds ~11% more drain on all actions.

## Encumbrance penalties

| Penalty | Default | Key |
|---------|---------|-----|
| Faster drowning | on, 8 air/tick | `drowning.air-loss-per-tick` |
| Higher fall damage | on, up to 1.75x | `fall-damage.max-multiplier` |

## scaling-weight (PlaceholderAPI)

Raises max carry cap from a placeholder:

```yaml
scaling-weight:
  enabled: false
  placeholder: "%mmocore_level%"
  per-point: 5.0
  cap: 200.0
```

Added capacity = min(placeholder value x per-point, cap).

Optional multi-source mode via `sources:` list (see default `weight.yml`).

## scaling-drain (v1.0.7, PlaceholderAPI)

Stat offsets how much inventory weight increases **action** stamina drain:

```yaml
scaling-drain:
  enabled: false
  placeholder: "%mmocore_attribute_strength%"
  stat-format: points       # or percent
  percent-reference: 100.0  # when stat-format is percent
  stat-per-point: 6.0       # weight cancelled per stat point
  stress-per-ratio: 0.20    # extra drain per 100% overload burden
```

When enabled:

- Encumbrance **drain multipliers do not stack** on top. One load-based model handles action drain.
- Slowness, severe sprint block, drowning, and fall damage **still apply** at encumbrance tiers.

Placeholders: `%shs_carry_burden%` (0 = stat covers load, 1+ = at/over cap after relief), `%shs_scaling_drain_mult%` (current multiplier on action drain).

Live tune: `/shs weight scaling-drain <key> <value>`

## Custom items

```yaml
custom-items:
  enabled: false
  default-weight: 1.0
```

Detection: PersistentDataContainer keys, CustomModelData, or custom display name.

## Admin commands

| Command | Purpose |
|---------|---------|
| `/weight` | Show current / max weight |
| `/shs weight set <MATERIAL> <weight>` | Edit item entry |
| `/shs weight encumbrance max-weight 350` | Tune thresholds |
| `/shs weight scaling-weight per-point 6` | Tune level scaling |
| `/shs weight scaling-drain stat-per-point 8` | Tune stat relief |

Disabled worlds: `config.yml` → `general.disabled-worlds.weight`.
