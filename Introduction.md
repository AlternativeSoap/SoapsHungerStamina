# Introduction

SoapsHungerStamina extends MMOCore stamina with survival and combat pressure. Stamina is the primary resource; vanilla hunger can mirror it or absorb overflow depending on your hunger mode.

## Core systems

**Stamina engine** runs on a tick interval (default every 4 server ticks). It detects movement, applies per-second drains, handles regen cooldowns after draining actions, and updates the stamina UI.

**Action drains** cover sprint, jump, swim, combat, projectiles, block interaction, environment contact, and more. Values live in `actions.yml`.

**Weight and encumbrance** sum inventory weight against per-player carry limits. Over-limit players get faster stamina drain (unless scaling-drain replaces tier multipliers), slowness, blocked sprint at severe tier, faster drowning, and higher fall damage.

**Hunger integration** has three modes: overflow (stamina loss can reduce food), bar (food bar shows stamina percent), or disabled.

**Winded** applies when players take entity hits: instant stamina loss, lingering drain, and on critical hits a short regen lock.

**Overexertion** punishes players who keep draining at 0 stamina. Accumulation past a threshold deals scaling damage until they recover.

**Biomes and altitude** (off by default) add exposure timers, passive drain, freeze or sweat effects, and multiplier stacks.

**Abilities** (mostly off by default): dodge (sneak while sprinting), sprint burst (double-tap sprint), bed rest recovery, and stamina-restoring food.

## How it fits MMOCore

- Max stamina and base regen come from MMOCore.
- SoapsHungerStamina drains and restores stamina on top of MMOCore's own systems.
- Attack drain is skipped when MMOItems already drained stamina for the same hit (if MMOItems is installed).
- `scaling-weight` can raise carry cap from an MMOCore placeholder (e.g. level).
- `scaling-drain` (v1.0.7) lets a stat like strength offset how much inventory weight hurts action stamina drain.

## World control

`config.yml` → `general.disabled-worlds`:

- `stamina`: disables engine, actions, and UI in listed worlds.
- `weight`: disables encumbrance, armor-weight drain, and scaling-drain in listed worlds.

Per-world multipliers are available under `worlds:` and `action-world-overrides:`.

## Bypass model

`soapsstamina.bypass` skips all stamina drain globally. Granular `soapsstamina.bypass.*` permissions exist per action and effect. OP bypass is on by default (`general.op-bypass: true`); set it false while testing.
