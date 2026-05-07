# Engine Notes

Use this file only when the user wants implementation, regression, or compatibility details.

## Condition Lifecycle

- Timed conditions use ticks and end times.
- A duration of `-1` means indefinite.
- Same-type conditions usually refresh instead of stacking additively.
- A shorter incoming duration does not replace a longer remaining duration.
- A finite condition does not replace an infinite one.

## Damage Conditions

- Burning, poison, energy, drown, freezing, dazzled, cursed, bleeding, and similar damage conditions can be delayed or periodic.
- Stronger damage conditions can replace weaker ones.
- Initial damage can happen as soon as the condition starts.
- Immunity or suppression can cancel damage.
- Field-based damage conditions are tied to the matching field when the creature stays inside it.

## Speed And Movement

- Positive speed changes behave like haste.
- Negative speed changes behave like paralyze or slow.
- Refreshing a speed condition adjusts the delta instead of stacking it.
- Paralyze removal can be delayed until the creature can walk again.

## Other Condition Types

- Invisibility hides the creature until the effect ends.
- Outfit and light conditions update the visible appearance immediately.
- Attribute conditions change skills or stats and push client updates.
- Regeneration conditions heal over time; protection zones can suppress healing while duration still ticks.
- Soul conditions grant soul on their own timer.
- Drunk conditions can refresh with stronger drunkenness.

## Player Handling

- Players show condition icons to the client, plus protection-zone and logout-related markers.
- Login restores stored conditions.
- Death clears persistent non-constant conditions.
- Combat-related conditions can be blocked, delayed, or cleaned up by player state.
- Mute and pacify style effects are tracked separately from simple timers.

## Practical Compatibility Notes

- If you are writing a feature for an older server, check whether the server treats certain markers as full conditions or only as client icons.
- Do not assume every official wiki label maps one-to-one to the same code path.
