# Configuration

Settings are split across two main files:
- `plugins/SoapsHungerStamina/config.yml` — general settings, engine, projectiles, overexertion, hunger, effects, biomes, altitude, UI, GUI
- `plugins/SoapsHungerStamina/actions.yml` — all action drain and regen values

You can edit files and run `/shs reload`, use the in-game GUI with `/shs gui`, or change values with `/shs toggle` and `/shs config set`.

---

## General

*File: config.yml*

```yaml
general:
  bypass-permission: "soapsstamina.bypass"
  ignore-flying: true
  stop-sprint-on-empty: true
  debug: false
```

`bypass-permission` — players with this permission skip all stamina and hunger drain. Give it to staff or event ranks. Per-action bypass permissions are also available (see [Commands & Permissions](Commands-and-Permissions.md)).

`ignore-flying` — skips players in creative flight. Elytra flight is not affected by this.

`stop-sprint-on-empty` — forces players to stop sprinting when stamina hits 0. Without this, they'd keep sprinting while hunger drains.

`debug` — prints drain info to the console. Only turn this on when you're testing.

---

## GUI

*File: config.yml*

```yaml
gui:
  enabled: true
```

`enabled` — turns the in-game settings panel on or off. When off, `/shs gui` tells the player it's disabled. All commands (`/shs toggle`, `/shs config set`, etc.) still work regardless.

---

## Actions

*File: actions.yml*

All stamina-draining and regenerating actions live in this file. Each one can be turned on/off separately.

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

`regen-action-cooldown` — milliseconds after any draining action before sneak and idle regen kick in. Prevents players from instantly recovering by sprint-crouch cycling. 2000 = 2 seconds.

`sprint.drain-per-second` — stamina lost every second while sprinting and actually moving. Standing still while holding sprint doesn't count.

`jump.cost` — flat cost per jump. The cooldown stops rapid jumps from all counting.

`jump.cooldown` — milliseconds between jumps that cost stamina. 300ms means about 3 jumps per second max.

`swim.drain-per-second` — stamina lost per second while actively swimming.

`water-contact.drain-per-second` — stamina lost per second while in water but not swimming (wading, floating, standing in shallow water).

`lava-contact.drain-per-second` — stamina lost per second while touching lava.

`block-place.cost` / `block-break.cost` — stamina cost each time you place or break a block.

`sneak.regen-per-second` — bonus stamina recovery per second while sneaking. Adds on top of MMOCore's natural regen. Subject to the regen action cooldown.

`idle.regen-per-second` — bonus stamina recovery per second while standing still. Smaller than sneak but still helpful. Also subject to the regen action cooldown.

`attack.cost` — stamina cost per melee hit. If MMOItems is installed and the weapon already applied a stamina cost through MythicLib, this drain is skipped to avoid double-charging.

`shield-block.initial-cost` — one-time cost when you raise your shield.

`shield-block.drain-per-second` — ongoing cost while your shield stays up.

---

## Winded

*File: actions.yml*

Taking damage drains stamina. Critical hits are harsher and lock out all regen.

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

`refresh-on-hit` — getting hit again restarts the winded timer. When disabled, a new hit doesn't extend the effect.

`normal.instant-cost` — stamina drained immediately when hit.

`normal.drain-per-second` — ongoing stamina drain per second after the hit.

`normal.duration` — how long the drain-over-time lasts in seconds.

`critical.instant-cost` — stamina drained immediately on a critical hit (higher than normal).

`critical.drain-per-second` — ongoing drain per second after a critical hit.

`critical.duration` — how long the critical drain lasts.

`critical.regen-lock-duration` — seconds during which ALL stamina regen is completely blocked. No MMOCore regen, no sneak regen, no idle regen. This is the most punishing mechanic in the plugin.

---

## Elytra, Climbing, Eating, Mace

*File: actions.yml*

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
```

`elytra.drain-per-second` — stamina lost per second while gliding with an elytra. Firework boosts don't add extra cost. Bypass: `soapsstamina.bypass.elytra`

`climbing.drain-per-second` — stamina lost per second while climbing ladders, vines, or scaffolding. Bypass: `soapsstamina.bypass.climbing`

`eating-regen.regen-amount` — flat stamina restored each time the player eats food. Bypass: `soapsstamina.bypass.eating`

`mace.cost` — extra stamina cost for attacking with a mace while falling (smash attack). Stacks with the normal attack cost. Bypass: `soapsstamina.bypass.mace`

---

## Potion Modifiers

*File: actions.yml*

```yaml
potion-modifiers:
  enabled: false
  speed-multiplier: 1.15
  haste-multiplier: 1.10
```

Multiplies stamina drain when the player has certain potion effects active. Speed makes you faster but costs more stamina. Disabled by default — enable for more realistic gameplay.

---

## Damage Intake

*File: actions.yml*

```yaml
damage-intake:
  enabled: true
  cost-per-heart: 0.5
```

Drains stamina when taking any damage (fire, fall, drowning, etc.). This is separate from "winded" which only triggers on entity attacks. Bypass: `soapsstamina.bypass.damage-intake`

---

## Boat, Crawling, Riptide

*File: actions.yml*

```yaml
boat:
  enabled: true
  drain-per-second: 0.3

crawling:
  enabled: true
  drain-per-second: 0.5

riptide:
  enabled: true
  cost: 2.5
```

`boat.drain-per-second` — stamina drain while paddling a boat (player must be moving). Bypass: `soapsstamina.bypass.boat`

`crawling.drain-per-second` — stamina drain while crawling through 1-block spaces (swimming pose on land). Bypass: `soapsstamina.bypass.crawling`

`riptide.cost` — flat stamina cost when launching with a riptide-enchanted trident. Bypass: `soapsstamina.bypass.riptide`

---

## Tool Use

*File: actions.yml*

```yaml
tool-use:
  enabled: true
  hoe-cost: 0.2
  shears-cost: 0.15
  brush-cost: 0.1
```

Small stamina costs for hoe tilling, shearing, and brush archaeology. Bypass: `soapsstamina.bypass.tool-use`

---

## Powder Snow, Slime Bounce

*File: actions.yml*

```yaml
powder-snow:
  enabled: true
  drain-per-second: 0.7

slime-bounce:
  enabled: true
  cost: 0.5
```

`powder-snow.drain-per-second` — stamina drain while standing in powder snow. Bypass: `soapsstamina.bypass.powder-snow`

`slime-bounce.cost` — stamina cost each time the player bounces on a slime block. Bypass: `soapsstamina.bypass.slime-bounce`

---

## Soul Sand, Honey Block

*File: actions.yml*

```yaml
soul-sand:
  enabled: true
  drain-multiplier: 1.20

honey-block:
  enabled: true
  drain-multiplier: 1.15
```

These multiply all stamina drain while standing on the respective block. Soul sand adds 20% more drain, honey blocks add 15%.

---

## Projectiles & Throwables

*File: config.yml*

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

Master toggle disables all projectile costs at once. Each weapon type has its own toggle.

`bow.scale-with-charge` — partial draws cost proportionally less stamina. A half-charge shot costs half the stamina. Crossbows always fire at full charge.

`throwables` — sub-toggle for all hand-thrown items. Each throwable has its own stamina cost per throw.

Bypass: `soapsstamina.bypass.projectiles`

---

## Overexertion

*File: config.yml*

When stamina is at zero and the player keeps performing draining actions, overexertion accumulates. Pass the threshold and they start taking real damage.

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

`threshold` — how much total drain at zero stamina before damage starts. Acts as a grace period. Small actions won't immediately hurt.

`base-damage` — hearts of damage per engine tick once past the threshold. 1.0 = half a heart, 2.0 = one heart.

`scaling-enabled` — damage increases the deeper into overexertion you go. Formula: `damage = base-damage + (overflow / scaling-divisor)`.

`scaling-divisor` — lower values make damage ramp up faster.

`max-damage` — cap on damage per engine tick. 6.0 = 3 hearts per tick, lethal if sustained.

`recovery-rate` — how fast overexertion resets per second when the player stops draining. Higher = faster recovery.

`warning-threshold` — percentage of the threshold at which the warning message is sent. 0.75 means warn at 75% before damage begins.

---

## Hunger

*File: config.yml*

Controls how stamina interacts with the vanilla food bar. Three modes are available:
- **overflow** — when stamina hits 0, extra drain overflows to the food bar. The food bar works normally otherwise.
- **bar** — replaces the vanilla food bar entirely with a stamina display. Eating food gives stamina instead of hunger.
- **disabled** — no food bar interaction at all.

```yaml
hunger:
  mode: overflow
  drain-per-second: 0.5
  min-hunger: 0
  drain-saturation: true
```

`mode` — set to `overflow`, `bar`, or `disabled`. Only one mode can be active.

`drain-per-second` — (overflow mode only) how fast the food bar drops. 1 point = half a food shank.

`min-hunger` — (overflow mode only) the food bar won't go below this number (0–20). Set it to 3 or 4 if you don't want players to fully starve from stamina drain.

`drain-saturation` — (overflow mode only) if true, the golden saturation drains first before the actual food bar. Matches how vanilla hunger works.

Bypass: `soapsstamina.bypass.hunger`

---

## Engine

*File: config.yml*

```yaml
engine:
  tick-interval: 4
  movement-threshold: 0.05
```

`tick-interval` — how often the plugin runs its checks, in server ticks. 20 ticks = 1 second. Lower numbers = smoother drain but more CPU. 4 is a good balance.

`movement-threshold` — how far (in blocks) a player needs to move to count as "moving." Prevents stamina draining while standing still. 0.05 is fine for normal play.

---

## Exhaustion Effects

*File: config.yml*

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

`recovery-threshold` — the player has to regen past this stamina percentage before effects go away. At 10%, effects stick around until they get above 10% stamina.

`slowness.amplifier` — 0 = Slowness I, 1 = Slowness II, etc.

`sweat-particles.count` — water drip particles spawned per engine tick. More = more visible.

`heavy-breathing` — brief darkness pulses on the screen edges. On or off, no extra settings.

`stumble.chance` — chance per engine tick (0.0 to 1.0). 0.03 = 3% chance each tick.

`stumble.strength` — how hard the knockback pushes. 0.1 is subtle.

Bypass all: `soapsstamina.bypass.effects`
Bypass individually: `soapsstamina.bypass.effects.slowness`, `.sweat`, `.breathing`, `.stumble`

---

## Biomes

*File: config.yml*

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
  freeze-particles:
    enabled: true
    count: 4
  encumbrance-biome-bonus: 0.10
```

`cold-drain-multiplier` — how much faster stamina drains in cold biomes. 1.10 = 10% faster.

`hot-drain-multiplier` — same thing for hot biomes. 1.08 = 8% faster.

`cold-passive-drain` — extra stamina drained per second just for standing in a cold biome, even if you're not doing anything.

`hot-passive-drain` — same for hot biomes.

`freeze.ticks-per-tick` — how many freeze ticks get added per engine tick in cold biomes. Higher = freezes faster.

`sweat.count` — water drip particles per engine tick in hot biomes.

`freeze-particles.count` — snowflake particles per engine tick in cold biomes (visible shivering/frost effect).

`encumbrance-biome-bonus` — if the player is also carrying too much weight, the biome drain gets even worse. This multiplier stacks on top.

Bypass: `soapsstamina.bypass.biomes`

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

`type` — set to `hot` or `cold`. Controls whether the biome causes sweat or freeze, and uses the default drain multiplier.

`multiplier` — optional. Overrides the default drain multiplier for that specific biome. Useful for places like the Nether where you want higher drain.

The default config includes 36 preconfigured biomes: 20 cold (snowy plains, frozen ocean, deep dark, pale garden, etc.), 11 hot (desert, jungle, savanna, swamp, etc.), and 5 nether biomes with custom multipliers (nether wastes 1.50, soul sand valley 1.40, basalt deltas 1.40, crimson/warped forest 1.25).

---

## Altitude

*File: config.yml*

Stamina drains faster at extreme heights (thin mountain air) and deep underground (stuffy caves). Disabled by default.

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

Between the two thresholds is a comfortable zone with no altitude penalty. The multiplier scales linearly — at the threshold edge it's 1.0 (no penalty), and at the world border (Y 320 / Y -64) it reaches the full configured value.

`high-threshold` — above this Y level, stamina drain starts increasing.

`high-multiplier` — maximum drain multiplier at the world height limit (Y 320). 1.15 = 15% more drain at the very top.

`high-passive-drain` — passive drain per second just for being at high altitude, even standing still.

`low-threshold` — below this Y level, stamina drain starts increasing.

`low-multiplier` — maximum drain multiplier at the world depth limit (Y -64). 1.12 = 12% more drain at bedrock level.

`low-passive-drain` — passive drain per second for being deep underground.

Bypass: `soapsstamina.bypass.altitude`

---

## Encumbrance

Extra penalties for carrying too much weight. The weight thresholds and item weights are in `weight.yml`.

*File: weight.yml*

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

`max-weight` — total inventory weight threshold for normal encumbrance.

`severe-weight` — threshold for severe encumbrance.

`encumbered-drain-multiplier` / `severe-drain-multiplier` — stamina drain multiplier at each tier. 1.4 = 40% more drain.

`encumbered-slowness` / `severe-slowness` — slowness amplifier at each tier (0 = Slowness I).

`block-sprint-severe` — prevents sprinting when severely encumbered.

`swim-slowness-bonus` — extra slowness amplifier when encumbered and in water.

`default-weight` — weight for items not listed in the items section.

`container-weight` — when true, shulker boxes and bundles weigh their contents plus the container itself.

### Drowning & Fall Damage

*File: weight.yml*

```yaml
drowning:
  enabled: true
  air-loss-per-tick: 8

fall-damage:
  enabled: true
  max-multiplier: 1.75
```

`drowning.air-loss-per-tick` — severely encumbered players lose this many air ticks per engine tick when underwater. Vanilla provides 300 air ticks total (15 seconds), so 8 per tick drains it noticeably faster.

`fall-damage.max-multiplier` — fall damage is multiplied by up to this amount at max weight. 1.75 = 75% more fall damage when fully loaded.

### Scaling (PlaceholderAPI)

*File: weight.yml*

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

`scaling-weight` — increases max carry weight based on a placeholder value. Bonus = placeholder value × per-point, capped at cap. At level 20 with default settings: 20 × 5.0 = 100 extra carry capacity. Supports multiple sources via a `sources:` list in place of the single placeholder.

`scaling-drain` — reduces all stamina drain based on a placeholder value. At 10 strength with defaults: 10 × 0.02 = 20% less drain. Capped at 50%.

### MMOItems Custom Weights

*File: weight.yml*

Override weight for specific MMOItems items by their type and ID. Requires the MMOItems plugin (soft-dependency). Disabled by default.

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

Format: `TYPE:ITEM_ID: <weight>`. The type and ID match what you see in MMOItems.

You can set a default weight for all items of a given type with `type-defaults`. Priority: specific item → type default → vanilla material weight.

---

## UI Display

*File: config.yml*

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

`type` — where stamina is shown. `ACTION_BAR` (above the hotbar), `BOSS_BAR` (top of screen), or `CHAT` (chat messages).

`update-threshold` — how much stamina has to change before the display refreshes. Prevents flickering on tiny changes.

`message-cooldown` — milliseconds between display updates. For CHAT mode, set this to 2000–5000 so it doesn't spam.

`low-stamina-warning` — shows a different colored format when stamina drops below the threshold.

`low-stamina-threshold` — what percentage counts as "low." 25 means the warning kicks in below 25% stamina.

`bar` — a text-based stamina bar using characters. When enabled, you can use `%stamina_bar%` in your messages.yml format strings, or `%shs_stamina_bar%` with PlaceholderAPI.

---

## Messages

All player-facing text is in `plugins/SoapsHungerStamina/messages.yml`.

Everything supports [MiniMessage formatting](https://docs.advntr.dev/minimessage/) for colors, gradients, bold, etc.

Key sections:
- `prefix` — the colored tag added to every message
- `command.*` — all command responses
- `exhaustion.*` — messages when effects activate/clear
- `encumbrance.*` — messages for weight thresholds
- `winded.*` — messages when getting hit (normal and critical)
- `overexertion.*` — warning, damage, and recovery messages
- `biome.*` — messages when entering hot/cold/neutral biomes
- `ui.format` — the stamina display format
- `ui.low-stamina-format` — warning display when low
- `gui.*` — all text shown in the admin settings GUI

---

## Weight

Item weights are in `plugins/SoapsHungerStamina/weight.yml`.

This file controls:
- Armor weight multipliers and how much each armor piece affects stamina drain
- Encumbrance thresholds for "encumbered" and "severely encumbered"
- Drowning and fall damage penalties
- Scaling rules for PlaceholderAPI-based bonuses
- MMOItems custom weights by type and ID
- Per-item weights so every item type can have a custom weight (1000+ preconfigured)

See [Default Config Files](Default-Config-Files.md) for details on the weight system.
