# Introduction

## The Problem

Vanilla survival hunger doesn't interact with MMOCore stamina. Players manage two separate resources that don't feel connected.

## The Solution

SoapsHungerStamina makes stamina the primary resource for movement. When stamina is gone, hunger becomes the cost.

## How It Works

**Stamina is your movement currency:**
- Sprinting drains stamina (2 per second by default)
- Jumping costs stamina (3 per jump by default)
- Swimming drains stamina (1.5 per second by default)

**Hunger kicks in when stamina is empty:**
- Keep sprinting after stamina hits zero? Hunger drains (1 per second by default)
- Hunger can't go below a minimum floor
- Saturation drains first, then hunger

**Exhaustion effects hit when you're empty:**
- Slowness makes you sluggish
- Sweat particles drip from your character
- Heavy breathing darkens vision briefly
- Stumble nudges knock you off course
- All effects clear once stamina recovers past a threshold

**Real-time feedback:**
- Action bar, boss bar, or chat messages show your stamina level
- Low stamina warning changes color when you're running dry
- Exhaustion enter/recover messages tell you when effects kick in

## Why It Matters

Your server now has a real resource system:
- Travel costs stamina
- Combat costs stamina
- Running out means hunger becomes the problem and exhaustion effects hit
- Food becomes valuable again
- Resting and recovery feel necessary

No weird double-drain. No confusion. Stamina → Hunger overflow → Exhaustion effects.
