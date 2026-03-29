# Introduction

## The Problem

Vanilla survival hunger doesn't interact with MMOCore stamina. Players manage two separate resources that don't feel connected.

## The Solution

SoapsHungerStamina makes stamina the primary resource for everything physical. When stamina is gone, hunger becomes the cost. Your inventory weight matters. The biome you're in matters.

## How It Works

**Stamina is your movement currency:**
- Sprinting drains stamina per second
- Jumping costs a flat amount per jump
- Swimming drains stamina per second
- Attacking costs stamina per hit
- Placing and breaking blocks cost stamina
- Raising a shield costs stamina upfront and keeps draining while held
- Sneaking gives you bonus stamina regen on top of MMOCore's natural regen

**Hunger kicks in when stamina is empty:**
- Keep doing stuff after stamina hits zero? Your food bar starts draining instead
- Saturation drains first, then actual hunger
- There's a configurable minimum — hunger can stop draining at a floor you set

**Exhaustion effects hit when you're empty:**
- Slowness makes you sluggish
- Sweat particles drip from your character
- Heavy breathing darkens your vision briefly
- Stumble nudges knock you off course
- All effects clear once stamina recovers past a configurable threshold

**Biomes change everything:**
- Cold biomes (snowy plains, frozen ocean, etc.) freeze you and drain stamina faster
- Hot biomes (desert, jungle, nether) make you sweat and drain stamina faster
- Each biome can have a custom drain multiplier
- Being encumbered in an extreme biome makes it even worse

**Weight slows you down:**
- Armor has weight — heavier armor means faster stamina drain
- Items in your inventory have weight too
- Cross a threshold and you're "encumbered" — stamina drains faster
- Cross the severe threshold and things get really bad: you can drown faster and take more fall damage

**Real-time feedback:**
- Action bar, boss bar, or chat messages show your stamina level
- Optional text-character stamina bar (`████░░░░░░`)
- Low stamina warning changes color when you're running dry
- Exhaustion enter/recover messages tell you when effects kick in
- Biome transition messages tell you when the climate changes

**Admin GUI:**
- Open `/shs gui` to toggle features and change every value in-game
- No config file editing needed — every setting has a clickable item
- Left/right click to adjust values, shift-click for bigger jumps

## Why It Matters

Your server now has a real resource system:
- Travel costs stamina
- Combat costs stamina
- Carrying heavy gear has a downside
- Biomes feel different to be in
- Running out means hunger becomes the problem and exhaustion effects hit
- Food becomes valuable again
- Resting and recovery feel necessary

Stamina → Hunger overflow → Exhaustion effects. That's the loop.
