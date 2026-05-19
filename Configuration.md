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
  sprint-lock:
    enabled: true
    unlock-mode: above-zero
    unlock-threshold-percent: 0.0
  debug: false
  disabled-worlds: []
```

`bypass-permission` — players with this permission skip all stamina and hunger drain. Give it to staff or event ranks. Per-action bypass permissions are also available (see [Commands & Permissions](Commands-and-Permissions.md)).

`ignore-flying` — skips players in creative flight. Elytra flight is not affected by this.

`sprint-lock` — controls hard sprint lock behavior when stamina is exhausted. Use `unlock-mode: above-zero` for immediate unlock or `threshold-percent` for stricter recovery gating.

`debug` — prints drain info to the console. Only turn this on when you're testing.

`disabled-worlds` — list of world folder names (e.g. `world_nether`, `creative`) where the stamina system is completely turned off. Players in these worlds skip all stamina drain, effects, and UI. Useful for creative worlds, lobbies, or minigame worlds.

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
regen-action-cooldown: 1500

sprint:
  enabled: true
  drain-per-second: 0.8

jump:
  enabled: true
  cost: 1.0

swim:
  enabled: true
  drain-per-second: 0.7

water-contact:
  enabled: true
  drain-per-second: 0.3

lava-contact:
  enabled: true
  drain-per-second: 1.0

block-place:
  enabled: true
  cost: 0.15
  exclude:
    - TORCH
    - SOUL_TORCH
    - WALL_TORCH
    - SOUL_WALL_TORCH
    - REDSTONE_TORCH
    - REDSTONE_WALL_TORCH

block-break:
  enabled: true
  cost: 0.2
  exclude: []

sneak:
  enabled: true
  regen-per-second: 1.2

idle:
  enabled: true
  regen-per-second: 0.6

attack:
  enabled: true
  cost: 0.8
  exclude: []
  weapon-costs:
    enabled: false
    sword: 0.6
    axe: 1.0
    trident: 0.9
    fist: 0.3

shield-block:
  enabled: true
  initial-cost: 0.2
  drain-per-second: 0.10
  min-stamina: 1.0
  damage-cost: 0.5
```

`regen-action-cooldown` — milliseconds after any draining action before sneak and idle regen kick in. Prevents players from instantly recovering by sprint-crouch cycling. 1500 = 1.5 seconds.

`sprint.drain-per-second` — stamina lost every second while sprinting and actually moving. Standing still while holding sprint doesn't count.

`jump.cost` — flat cost per jump. Every jump is tracked through the server's built-in statistic, so no jumps are missed.

`swim.drain-per-second` — stamina lost per second while actively swimming.

`water-contact.drain-per-second` — stamina lost per second while in water but not swimming (wading, floating, standing in shallow water).

`lava-contact.drain-per-second` — stamina lost per second while touching lava.

`block-place.cost` / `block-break.cost` — stamina cost each time you place or break a block.

`block-place.exclude` / `block-break.exclude` — list of Minecraft material names that won't cost stamina. By default, torches are excluded from placement cost since they're decorative. Add any blocks you want players to place or break for free.

`sneak.regen-per-second` — bonus stamina recovery per second while sneaking. Adds on top of MMOCore's natural regen. Subject to the regen action cooldown.

`idle.regen-per-second` — bonus stamina recovery per second while standing still. Smaller than sneak but still helpful. Also subject to the regen action cooldown.

`attack.cost` — stamina cost per melee hit. If MMOItems is installed and the weapon already applied a stamina cost through MythicLib, this drain is skipped to avoid double-charging.

`attack.exclude` — list of Minecraft material names (e.g. `WOODEN_SWORD`, `DIAMOND_AXE`) that won't cost stamina when attacking. Useful for quest items or event weapons.

`attack.weapon-costs` — when enabled, different weapon types use their own stamina cost instead of the generic `cost` above. Swords are cheapest, axes are heaviest. Any weapon that doesn't match a category falls back to the default cost. Fist means punching with an empty hand.

`shield-block.initial-cost` — one-time cost when you raise your shield.

`shield-block.drain-per-second` — ongoing cost while your shield stays up.

`shield-block.min-stamina` — when the player's stamina drops to or below this value, the shield is forced down and can't be raised again until they recover above it. Prevents players from turtling indefinitely.

`shield-block.damage-cost` — extra stamina drained each time the shield absorbs a hit. So blocking punches is free-ish, but blocking heavy attacks eats through stamina fast.

---

## Winded

*File: actions.yml*

Taking damage drains stamina. Critical hits are harsher and lock out all regen.

Bypass: `soapsstamina.bypass.winded`

```yaml
winded:
  enabled: true
  refresh-on-hit: true
  normal:
    instant-cost: 0.3
    drain-per-second: 0.4
    duration: 3.0
  critical:
    instant-cost: 1.0
    drain-per-second: 0.8
    duration: 4.0
    regen-lock-duration: 2.5
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

## Elytra, Climbing, Mace

*File: actions.yml*

```yaml
elytra:
  enabled: true
  drain-per-second: 0.5

climbing:
  enabled: true
  drain-per-second: 0.4

mace:
  enabled: true
  cost: 2.0
```

`elytra.drain-per-second` — stamina lost per second while gliding with an elytra. Firework boosts don't add extra cost. Bypass: `soapsstamina.bypass.elytra`

`climbing.drain-per-second` — stamina lost per second while climbing ladders, vines, or scaffolding. Bypass: `soapsstamina.bypass.climbing`

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
  cost-per-heart: 0.3
```

Drains stamina when taking any damage (fire, fall, drowning, etc.). This is separate from "winded" which only triggers on entity attacks. Bypass: `soapsstamina.bypass.damage-intake`

---

## Boat, Crawling, Riptide

*File: actions.yml*

```yaml
boat:
  enabled: true
  drain-per-second: 0.1

crawling:
  enabled: true
  drain-per-second: 0.35

riptide:
  enabled: true
  cost: 2.0
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
  flint-and-steel-cost: 0.15
```

Small stamina costs for hoe tilling, shearing, brush archaeology, and lighting fires with flint and steel. Bypass: `soapsstamina.bypass.tool-use`

---

## Powder Snow, Slime Bounce

*File: actions.yml*

```yaml
powder-snow:
  enabled: true
  exposure-multiplier: 2.0

slime-bounce:
  enabled: true
  cost: 0.5
```

`powder-snow.exposure-multiplier` — multiplier applied to cold biome exposure rate while standing in powder snow. Bypass: `soapsstamina.bypass.powder-snow`

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

Bypass: `soapsstamina.bypass.overexertion`

```yaml
overexertion:
  enabled: true
  threshold: 25.0
  base-damage: 0.5
  scaling-enabled: true
  scaling-divisor: 8.0
  max-damage: 4.0
  recovery-rate: 5.0
  warning-threshold: 0.75
```

`threshold` — how much total drain at zero stamina before damage starts. Acts as a grace period. Small actions won't immediately hurt.

`base-damage` — hearts of damage per engine tick once past the threshold. 0.5 = a quarter heart, 2.0 = one heart.

`scaling-enabled` — damage increases the deeper into overexertion you go. Formula: `damage = base-damage + (overflow / scaling-divisor)`.

`scaling-divisor` — lower values make damage ramp up faster.

`max-damage` — cap on damage per engine tick. 4.0 = 2 hearts per tick, lethal if sustained.

`recovery-rate` — how fast overexertion resets per second when the player stops draining. Higher = faster recovery.

`warning-threshold` — percentage of the threshold at which the warning message is sent. 0.75 means warn at 75% before damage begins.

---

## Second Wind

*File: config.yml*

A last-resort recovery for players who hit rock bottom. When their stamina is at zero and they stand completely still for a few seconds, they catch a "second wind" — a burst of stamina that gets them back in the fight. Has a long cooldown so players can't abuse it.

Bypass: `soapsstamina.bypass.second-wind`

```yaml
second-wind:
  enabled: false
  idle-seconds: 5.0
  recovery-percent: 0.30
  cooldown-seconds: 90.0
```

`idle-seconds` — how long the player must stand still at zero stamina before it triggers. 5 seconds feels like an eternity in combat, which is the point.

`recovery-percent` — fraction of max stamina restored (0.0 to 1.0). 0.30 = 30%.

`cooldown-seconds` — how long before second wind can trigger again. 90 seconds by default.

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
  recovery-animation:
    enabled: true
    particle: HAPPY_VILLAGER
    count: 15
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

`recovery-animation` — spawns particles when the player finally recovers from exhaustion, giving visible feedback that they've caught their breath. The default green sparkles (HAPPY_VILLAGER) are subtle but noticeable. Set `enabled: false` to turn it off, or change `particle` to any valid Bukkit Particle name.

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

In v1.0.5, biomes use an **exposure system**. Players get a grace period when they enter an extreme biome. The exposure timer counts up while they're unprotected, and once it fills up, biome effects kick in. When they leave or protect themselves, the timer decays back down.

**Protection:**
- **Cold biomes:** wearing at least 50% armor (2 of 4 pieces) pauses and decays the timer.
- **Hot biomes:** wearing NO armor, or standing in water, protects the player.
- **Over-encumbered in cold:** extra slowness applied immediately (no grace period).
- **Over-encumbered in hot:** instant exposure (skips the grace period entirely).

```yaml
biomes:
  enabled: false
  cold-drain-multiplier: 1.10
  hot-drain-multiplier: 1.08
  exposure:
    cold-duration: 60
    hot-duration: 45
    decay-rate: 2.0
  cold:
    exposed-drain: 0.6
    armor-protection: 0.5
    encumbered-slowness: 2
    freeze:
      enabled: true
      ticks-per-tick: 1
      tick-cap: 0.95
    freeze-particles:
      enabled: true
      count: 4
  hot:
    exposed-drain: 0.5
    water-cooldown: true
    no-armor-protection: true
    encumbered-instant: true
    sweat:
      enabled: true
      count: 4
  encumbrance-biome-bonus: 0.10
```

`cold-drain-multiplier` — how much faster stamina drains in cold biomes once exposed. 1.10 = 10% faster.

`hot-drain-multiplier` — same thing for hot biomes. 1.08 = 8% faster.

### Exposure Timer

`exposure.cold-duration` — seconds an unprotected player must spend in a cold biome before freeze effects begin. 60 seconds gives them a full minute to gear up or get out.

`exposure.hot-duration` — same for hot biomes. 45 seconds by default (heat hits sooner).

`exposure.decay-rate` — how fast the exposure timer counts back down per second when the player is protected or in a neutral biome. Higher = forgives faster.

### Cold Biome Settings

`cold.exposed-drain` — passive stamina drain per second once the player is exposed (frozen), even if they're standing still.

`cold.armor-protection` — fraction of armor slots needed to be "protected" from cold (0.0–1.0). 0.5 means at least 2 out of 4 armor pieces. Protected players don't accumulate exposure.

`cold.encumbered-slowness` — slowness amplifier applied when over-encumbered in a cold biome. This kicks in immediately, no exposure needed. 2 = Slowness III.

`cold.freeze` — gradually increases the player's freeze ticks to show the icy-screen overlay. The `tick-cap` at 0.95 gives a strong frost visual without actually dealing freeze damage (that happens at 1.0).

`cold.freeze-particles` — snowflake particles near the player's head when exposed.

### Hot Biome Settings

`hot.exposed-drain` — passive stamina drain per second once exposed (sweating).

`hot.water-cooldown` — when true, standing in water cools the player and decays their exposure timer.

`hot.no-armor-protection` — when true, wearing no armor protects from heat (exposure doesn't accumulate). Makes sense — less clothing = less overheating.

`hot.encumbered-instant` — when true, over-encumbered players are instantly exposed in hot biomes (skip the grace period). Carrying heavy gear in the desert is brutal.

`hot.sweat` — water drip particles per engine tick in hot biomes.

`encumbrance-biome-bonus` — if the player is both encumbered AND exposed, the biome drain gets even worse. This multiplier stacks on top.

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

The default config includes 38 preconfigured biomes: 22 cold (snowy plains, frozen ocean, deep dark, pale garden, taiga variants, windswept hills, stony shore, etc.), 12 hot (desert, jungle, badlands, savanna, swamp, mangrove swamp, etc.), and 5 nether biomes with custom multipliers (nether wastes 1.50, soul sand valley 1.40, basalt deltas 1.40, crimson/warped forest 1.25).

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

## Sounds

*File: config.yml*

Play sound effects at key stamina events. Disabled by default. When enabled, players hear audio feedback when they enter/exit exhaustion, get low stamina warnings, approach overexertion, or trigger second wind.

```yaml
sounds:
  enabled: false
  exhaustion-enter:
    sound: ENTITY_PLAYER_BREATH
    volume: 0.6
    pitch: 0.8
  exhaustion-recover:
    sound: ENTITY_PLAYER_LEVELUP
    volume: 0.5
    pitch: 1.2
  low-stamina-warning:
    sound: BLOCK_NOTE_BLOCK_BASS
    volume: 0.5
    pitch: 0.5
  overexertion-warning:
    sound: ENTITY_VILLAGER_NO
    volume: 0.7
    pitch: 0.7
  second-wind:
    sound: ENTITY_PLAYER_LEVELUP
    volume: 0.8
    pitch: 1.5
```

Each event has a `sound`, `volume`, and `pitch`. Sound names must be valid Bukkit Sound enum values — you can find the full list on [SpigotMC's Javadocs](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Sound.html). Volume ranges from 0.0 to 1.0, pitch from 0.5 to 2.0.

---

## Per-World Multipliers

*File: config.yml*

Override the stamina drain multiplier for specific worlds. This stacks with all other multipliers (biome, altitude, encumbrance, etc.).

```yaml
worlds:
  # world_nether: 1.25
  # world_the_end: 0.80
```

Use the exact world folder name as the key. 1.0 = no change, 1.25 = 25% more drain, 0.80 = 20% less drain. Uncomment and add entries for any world you want to adjust.

To completely **disable** stamina in a world (not just reduce it), add the world name to `general.disabled-worlds` instead.

---

## Player Display Preference

*File: config.yml*

Lets players choose their own stamina display type with `/stamina display`. When disabled, everyone uses the global `ui.type` setting.

```yaml
player-display-choice:
  enabled: false
```

Requires the `soapsstamina.display.choose` permission. Players can pick between `actionbar`, `bossbar`, or `off`. Their choice is remembered until the server restarts or they change it again.

---

## Stamina Food

*File: config.yml*

Certain foods restore stamina when eaten and can give a temporary "Well Fed" regen buff. This works on top of whatever hunger mode you're using — it's purely a stamina bonus, not a hunger replacement.

Bypass: `soapsstamina.bypass.stamina-food`

```yaml
stamina-food:
  enabled: true
  items:
    GOLDEN_APPLE:
      instant-stamina: 10.0
      buff-duration: 30
      buff-regen-bonus: 0.5
    ENCHANTED_GOLDEN_APPLE:
      instant-stamina: 20.0
      buff-duration: 60
      buff-regen-bonus: 1.0
    GOLDEN_CARROT:
      instant-stamina: 5.0
      buff-duration: 15
      buff-regen-bonus: 0.3
    COOKED_BEEF:
      instant-stamina: 3.0
    COOKED_PORKCHOP:
      instant-stamina: 3.0
    COOKED_MUTTON:
      instant-stamina: 2.5
    COOKED_CHICKEN:
      instant-stamina: 2.5
    COOKED_SALMON:
      instant-stamina: 2.5
    COOKED_COD:
      instant-stamina: 2.0
    BAKED_POTATO:
      instant-stamina: 2.0
    BREAD:
      instant-stamina: 1.5
    RABBIT_STEW:
      instant-stamina: 4.0
      buff-duration: 10
      buff-regen-bonus: 0.2
    MUSHROOM_STEW:
      instant-stamina: 3.0
```

Each food can have:
- `instant-stamina` — stamina restored immediately when eaten.
- `buff-duration` — seconds of the "Well Fed" regen buff (omit for no buff).
- `buff-regen-bonus` — extra stamina regen per second during the buff.

Golden foods are the strongest since they're harder to get. Regular cooked meats give a small instant boost with no buff. You can add any Minecraft food item to this list using its material name.

> **Note:** The old `eating-regen` action from v1.0.4 has been replaced by this system. Stamina food gives you much more control over which foods matter and by how much.

---

## Dodge

*File: config.yml*

An active ability: press sneak while sprinting to perform a dodge roll. The player gets launched forward with a burst of speed and brief invulnerability. Costs stamina and has a cooldown. Great for PvP servers or action-RPG gameplay. Disabled by default.

Bypass: `soapsstamina.bypass.dodge`

```yaml
dodge:
  enabled: false
  cost: 4.0
  cooldown-ms: 1500
  velocity: 1.2
  invulnerable-ticks: 12
  sound: ENTITY_PLAYER_ATTACK_SWEEP
  sound-volume: 0.8
  sound-pitch: 1.3
```

`cost` — flat stamina cost per dodge.

`cooldown-ms` — milliseconds between dodges. 1500 = 1.5 seconds.

`velocity` — how fast the player is launched forward. 1.2 is a snappy dodge. Higher values send them flying further.

`invulnerable-ticks` — ticks of invulnerability after dodging (20 ticks = 1 second). 12 gives about 0.6 seconds of i-frames.

The sound settings play a sound when dodging. Set the `sound` to any valid Bukkit Sound name.

---

## Sprint Burst

*File: config.yml*

When a player starts sprinting with high stamina, they get an automatic burst of speed. Costs a flat chunk of stamina and applies a temporary Speed potion effect. Won't trigger again until the cooldown expires. Disabled by default.

Bypass: `soapsstamina.bypass.sprint-burst`

```yaml
sprint-burst:
  enabled: false
  min-stamina-percent: 80.0
  cost: 6.0
  speed-amplifier: 1
  duration-ticks: 60
  cooldown-ms: 30000
  sound: ENTITY_PLAYER_LEVELUP
  sound-volume: 0.6
  sound-pitch: 1.8
```

`min-stamina-percent` — stamina must be at least this percentage (0–100) to trigger. 80% means you need to be well-rested to get a burst.

`cost` — flat stamina cost when the burst activates.

`speed-amplifier` — Speed effect level. 0 = Speed I, 1 = Speed II.

`duration-ticks` — how long the speed boost lasts in ticks (20 = 1 second). 60 = 3 seconds.

`cooldown-ms` — milliseconds before sprint burst can trigger again. 30000 = 30 seconds.

---

## Bed Rest

*File: config.yml*

Sleeping through the night restores stamina and can give a "Well Rested" buff that reduces all stamina drain for a while. The player has to actually sleep (stay in bed for at least 1 second — no bed-right-click skipping).

Bypass: `soapsstamina.bypass.bed-rest`

```yaml
bed-rest:
  enabled: true
  restore-percent: 1.0
  buff-enabled: true
  buff-duration-seconds: 120
  buff-drain-reduction: 0.65
  sound: ENTITY_PLAYER_LEVELUP
  sound-volume: 0.7
  sound-pitch: 1.4
```

`restore-percent` — fraction of max stamina restored after sleeping (0.0 to 1.0). 1.0 = full stamina.

`buff-enabled` — whether the "Well Rested" buff is applied after sleeping.

`buff-duration-seconds` — how long the Well Rested buff lasts. 120 = 2 minutes.

`buff-drain-reduction` — drain multiplier during the buff (0.0 to 1.0). 0.65 means all stamina drain is reduced to 65% of normal (35% reduction). Lower values = stronger buff.

---

## UI Display

*File: config.yml*

```yaml
ui:
  enabled: true
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

`enabled` — global master switch for stamina UI. Set to `false` to hide stamina UI for everyone.

`type` — where stamina is shown when `enabled` is true. `ACTION_BAR` (above the hotbar), `BOSS_BAR` (top of screen), or `CHAT` (chat messages).

`update-threshold` — how much stamina has to change before the display refreshes. Prevents flickering on tiny changes.

`message-cooldown` — milliseconds between display updates. For CHAT mode, set this to 2000–5000 so it doesn't spam.

`low-stamina-warning` — shows a different colored format when stamina drops below the threshold.

`low-stamina-threshold` — what percentage counts as "low." 25 means the warning kicks in below 25% stamina.

`bar` — a text-based stamina bar using characters. When enabled, you can use `%stamina_bar%` in your messages.yml format strings, or `%shs_stamina_bar%` with PlaceholderAPI.

If `ui.enabled` is false, `/stamina display` choices are ignored until UI is enabled again.

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
- `second-wind.*` — messages for second wind activation and cooldown
- `biome.*` — messages when entering hot/cold/neutral biomes
- `stamina-food.*` — messages for Well Fed buff
- `dodge.*` — dodge activation and cooldown messages
- `sprint-burst.*` — sprint burst activation messages
- `bed-rest.*` — Well Rested buff messages
- `stats.*` — session statistics display
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
