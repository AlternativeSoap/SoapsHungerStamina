# FAQ

## Does this replace MMOCore stamina?

No. MMOCore owns max stamina and base regen. SoapsHungerStamina adds drains, bonuses, UI, weight, and hunger tie-ins on top.

## Why is nothing draining?

Check in order:

1. Player has `soapsstamina.bypass` or OP with `general.op-bypass: true`
2. World is in `general.disabled-worlds.stamina`
3. Action is disabled in `actions.yml` or via `/shs toggle`
4. MMOCore stamina is already 0 and sprint lock is blocking movement
5. `general.debug: true` to log drains in console

## Stamina drains twice on attack with MMOItems weapons

MMOItems integration should prevent double drain. Confirm MMOItems is installed and loaded before SHS. Check console for integration warnings on startup.

## Hunger drops but stamina looks fine

You are likely in `overflow` mode. Overflow converts sub-zero stamina hits into food loss. Switch to `bar` or `disabled` if you do not want that.

## Encumbrance messages but weight looks low

Container weight counts shulker and bundle contents. Check nested storage depth (`container-max-depth`). Custom items may use `custom-items.default-weight`.

## scaling-drain enabled but no effect

Requires PlaceholderAPI. Confirm placeholder resolves to a number for test players (`/papi parse <player> %mmocore_attribute_strength%`). Enable `general.debug` to see resolution warnings.

## Does scaling-drain stack with encumbrance multipliers?

No. When scaling-drain is on, tier drain multipliers are not applied to action drain. Slowness, sprint block at severe, drowning, and fall damage still work.

## How do players pick action bar vs boss bar?

Set `player-display-choice.enabled: true`. Players use `/stamina display <off|actionbar|bossbar>` with `soapsstamina.display.choose`. Global default remains `ui.type`.

## Dodge does nothing

`dodge.enabled` must be true. Player must sneak **while already sprinting**. In combat, dodge is blocked unless `context.in-combat.allow-dodge: true`. Check stamina and cooldown.

## Sprint burst does nothing

`sprint-burst.enabled` must be true. Player must double-tap sprint within `activation-window-ms` (default 400ms). Needs stamina above `min-stamina-percent`.

## Bed rest did not refill stamina

Confirm `bed-rest.enabled`, player slept long enough (`minimum-sleep-ms`), and cooldown since last rest has passed. Creative/spectator and bypass permission skip it.

## Placeholders show empty

PlaceholderAPI must be installed. Player must be online for player placeholders. Reload PAPI after installing SHS: `/papi reload`.

## Config changes from GUI did not stick

GUI writes YAML and reloads. If an external tool overwrites files, changes can be lost. Edit files when the server is stopped or coordinate reload order.

## Can I run stamina without weight?

Yes. Disable encumbrance in weight.yml (`encumbrance.enabled: false`) or add all worlds to `disabled-worlds.weight`.

## What Minecraft version?

API version 1.21 per `plugin.yml`. Built for Paper 1.21+ with Java 21.

## Where do I report bugs?

Website: [soapsuniverse.com](https://www.soapsuniverse.com). Include version 1.0.7, server software, and relevant config snippets.
