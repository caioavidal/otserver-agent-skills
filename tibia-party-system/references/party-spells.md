# Party Spells

Use this file for the party support spells found in the supplied downgrade reference.

## Canonical Behavior

- The scripts create party-targeted support effects in a small area.
- They are non-aggressive.
- The scripts themselves do not define role logic; the server decides who may cast them.

## Script Summary

- `train_party`: temporary combat-skill boost for nearby party members.
- `protect_party`: temporary shielding boost for nearby party members.
- `heal_party`: temporary regeneration effect for nearby party members.
- `enchant_party`: temporary magic-oriented party boost for nearby party members.

## Compatibility Notes

- In the supplied downgrade reference, these scripts apply short-lived party conditions through `addPartyCondition`.
- The visible effect lasts about 2 minutes in the reference scripts.
- `heal_party` applies a healing-over-time style effect in the reference scripts.
- If you need exact numbers, verify them against the target server before writing acceptance criteria.
- Fandom also describes class-specific party support skills for Premium players at level 32+.
- If the task concerns those skills instead of the supplied scripts, verify the target ruleset before writing acceptance criteria.

## Validation Checklist

- Is the spell party-targeted, not single-target?
- Does it affect nearby members only?
- Does it show a visible buff or heal effect?
- Does the server enforce any casting restriction outside the script?
