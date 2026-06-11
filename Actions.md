# Actions

File: `plugins/SoapsHungerStamina/actions.yml`

All stamina costs and recovery values for player actions. Bypass permissions are listed per section (pattern: `soapsstamina.bypass.<action>`).

## Global regen rule

`regen-action-cooldown: 1500` (ms). After any draining action, sneak and idle regen wait this long. Stops crouch-spam healing mid-fight.

## Movement

| Action | Type | Default | Bypass permission |
|--------|------|---------|-------------------|
| Sprint | drain/sec | 0.8 | `soapsstamina.bypass.sprint` |
| Jump | flat cost | 1.0 | `soapsstamina.bypass.jump` |
| Swim | drain/sec | 0.7 | `soapsstamina.bypass.swim` |
| Crawling | drain/sec | 0.35 | `soapsstamina.bypass.crawling` |
| Climbing | drain/sec | 0.4 | `soapsstamina.bypass.climbing` |
| Elytra | drain/sec | 0.5 | `soapsstamina.bypass.elytra` |
| Boat | drain/sec | 0.1 (off) | `soapsstamina.bypass.boat` |
| Riptide | flat cost | 2.0 | `soapsstamina.bypass.riptide` |

### Sprint lock

```yaml
sprint:
  lock:
    enabled: true
    unlock-mode: above-zero    # or threshold-percent
    unlock-threshold-percent: 0.0
```

## Combat

| Action | Default | Notes |
|--------|---------|-------|
| Attack | 0.8 flat | Skipped if MMOItems drained same hit |
| Mace smash | +2.0 flat | When falling with mace; stacks on attack |
| Shield block | 0.2 up + 0.10/sec + 0.5/hit absorbed | Shield forced down at `min-stamina` |
| Winded (normal hit) | 0.3 instant + 0.4/sec for 3s | Entity hits |
| Winded (critical) | 1.0 instant + 0.8/sec for 4s + 2.5s regen lock | Attacker falling or sprinting |
| Damage intake | 0.3 per heart | Fire, fall, etc. Entity hits use winded if enabled |
| Bow | 1.5 (scales with charge) | |
| Crossbow | 1.8 | |
| Trident throw | 2.0 | |
| Throwables | per-item costs | snowball 0.3, pearl 1.0, etc. |

`attack.exclude`: materials that cost no stamina. `attack.weapon-costs`: per weapon type when enabled.

## Interactions

| Action | Default |
|--------|---------|
| Block place | 0.15 (torches excluded by default) |
| Block break | 0.2 |
| Tool use | hoe 0.2, shears 0.15, brush 0.1, flint 0.15 |
| Block interact | 0.05 (off by default) |

## Environment

| Action | Default | Effect |
|--------|---------|--------|
| Water contact | 0.3/sec | Wading without swim sprint |
| Lava contact | 1.0/sec | |
| Powder snow | exposure x2 | Needs biomes enabled |
| Soul sand | 1.20x multiplier | All drain while on soul sand |
| Honey block | 1.15x (off) | All drain on honey |
| Slime bounce | 0.5 flat | 500ms cooldown |

## Potion modifiers (off by default)

- Speed: multiplies all drain (default 1.15x)
- Haste: multiplies block-break and tool-use only (default 1.10x)

## Recovery

| Action | Default |
|--------|---------|
| Sneak regen | 1.2/sec |
| Idle regen | 0.6/sec |
| Stamina food | per-item in `stamina-food.items` |
| Dodge | 4.0 cost (off) |
| Sprint burst | 6.0 cost (off) |
| Bed rest | 100% restore + Well Rested buff |

## PvP/PvE multipliers

Set in `config.yml` → `context.pvp-pve` for attack, projectiles, winded, and damage-intake.

## Tuning tips

1. Start with sprint and jump; players feel these constantly.
2. Raise `regen-action-cooldown` for harder combat pacing.
3. Lower attack cost for fast weapons if fights feel sluggish.
4. Enable `weapon-costs` to differentiate axes vs swords.
5. Use `/shs config set sprint drain-per-second 1.0` for quick tests.

Full defaults are in the shipped `actions.yml`.
