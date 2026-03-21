# Introduction

## The Problem

Vanilla survival hunger doesn't interact with MMOCore stamina. Players manage two separate resources that don't feel connected.

## The Solution

SoapsHungerStamina makes stamina the primary resource for movement. When stamina is gone, hunger becomes the cost.

## How It Works

**Stamina is your movement currency:**
- Sprinting drains stamina (5 per second by default)
- Jumping costs stamina (8 per jump by default)
- Swimming drains stamina (3 per second by default)

**Hunger kicks in when stamina is empty:**
- Keep sprinting after stamina hits zero? Hunger drains (1 per second by default)
- Hunger can't go below a minimum floor
- Saturation drains first, then hunger

**Real-time feedback:**
- Action bar shows your stamina level
- Low stamina warning changes color when you're running dry
- Clear visual indication of when you're switching from stamina cost to hunger cost

## Why It Matters

Your server now has a real resource system:
- Travel costs stamina
- Combat costs stamina
- Running out means hunger becomes the problem
- Food becomes valuable again
- Resting and recovery feel necessary

No weird double-drain. No confusion. Stamina → Hunger overflow.
