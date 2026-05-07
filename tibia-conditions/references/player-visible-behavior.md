# Player-Visible Behavior

Use this file for rules the player can observe directly.

## General Rules

- Special conditions are temporary.
- They are shown as icons below the inventory or next to the character.
- A maximum of six icons can be shown at once.
- If more are active, the client shows `...`.

## Damage Over Time

- Agony: damage over time; cannot be cured, blocked, or resisted.
- Bleeding: damage over time; can be cured by time, Cure Bleeding, or certain NPCs.
- Burning: fire damage over time; can be cured by time, swimming, Cure Burning, or certain NPCs.
- Cursed: death damage over time; can be cured by Cure Curse or time.
- Dazzled: holy damage over time; usually wears off on its own.
- Drowning: drown damage over time; stops when not underwater, and the Helmet of the Deep helps underwater.
- Electrified: energy damage over time; can be cured by time, swimming, Cure Electrification, or certain NPCs.
- Freezing: ice damage over time; usually wears off on its own.
- Poisoned: earth damage over time; can be cured by time, Cure Poison, or certain NPCs.

## Movement And Control

- Drunk: movement becomes unreliable and the character may step in the wrong direction.
- Feared: the character loses control, runs away, and cannot use items or spells.
- Rooted: the character cannot move for a short time.
- Slowed: the character moves much slower; healing magic or waiting removes it.

## Buffs And Resource Effects

- Haste: movement becomes faster.
- Magic Shield: damage is taken from mana first.
- Strengthened: one or more skills are temporarily boosted.
- Hungry: the character can still eat, and regeneration is slower until they do.

## Markers And Area States

- Within Protection Zone: the character is in a safe area and cannot attack or be attacked.
- Protection Zone Block: the character recently attacked a player and cannot enter a protection zone or log out.
- Logout Block: the character cannot log out for a while.
- Within Resting Area / Within Active Resting Area: resting-area state shown by the client.

## Boss Or Progression Stacks

- Bakragore's Taints: stacked penalties and bonuses tied to Rotten Blood areas.
- Goshnar's Taints: stacked penalties and bonuses tied to Soul War areas.

## Broader Social Markers

- Skull, party, war, and guild icons are visible status markers in the same UI area, but they are not classic timed ailments.

## High-Value Edge Cases

- Some effects can be removed only by waiting.
- Some effects can be cured only by a specific spell or NPC.
- Some markers are informational and do not directly damage the character.
- Protection-zone behavior may suppress regeneration while the timer still counts down.
