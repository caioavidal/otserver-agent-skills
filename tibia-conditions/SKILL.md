---
name: tibia-conditions
description: Use this skill when a task involves Tibia conditions, special conditions, status effects, condition icons, taints, or PvP/party/war/guild markers, or when you need gameplay rules, feature specs, validation, or tests for poison, burning, bleeding, electrocution, freeze, curse, haste, paralyze, magic shield, drunk, rooted, feared, hungry, logout block, protection zone block, resting area, and related effects.
metadata:
  domain: tibia-conditions-gameplay
  version: "1.0"
---

# Tibia Conditions

Use this skill to reason about Tibia condition behavior from the player point of view. Keep the answer non-technical unless the user asks for implementation details.

## Ground Rules

- Speak in gameplay terms: effect, icon, duration, cure, immunity, movement, regeneration, damage, removal, and visible outcome.
- Do not assume any engine layout, data model, or scripting language.
- Prefer official gameplay behavior first. Use the wiki and MCP catalog to fill in newer or more specific condition names, then use the reference implementation only for compatibility notes.
- Treat "conditions" as player-visible status effects and markers, not generic logic conditions.
- Some labels in the catalog are exact pages for spells, charms, or marker systems. Verify the page meaning before using it as a status effect.

## Source Priority

Use sources in this order:

1. Official Tibia manual special conditions section.
2. Tibia Wiki special conditions page.
3. Tibia Wiki MCP `getConditions` and `getConditionByName`.
4. Reference implementation in `condition.cpp`, `creature.cpp`, and `player.cpp`.

If sources disagree, follow official gameplay behavior and mark code behavior as compatibility only.

## Lookup Rules

- Use `getConditions` when you need the catalog, a search result, or the player-facing name of a condition.
- Use `getConditionByName` only after you know the exact condition name you want.
- If a name is ambiguous, verify it before treating it as a status effect. For example, `poison` may point to the Poison charm page, not the Poisoned status.
- When the user asks about a specific icon or label, match the visible effect first and the engine name second.

## Workflow

1. Identify the condition family: damage over time, movement/control, defense/buff, resource, area/status marker, or boss stack.
2. Read the needed reference file:
   - `references/condition-catalog.md` for names, categories, and what each condition is meant to represent.
   - `references/player-visible-behavior.md` for observable effects, cures, limits, and special cases.
   - `references/engine-notes.md` for implementation and compatibility details from the reference server.
   - `references/test-generation.md` for unit, integration, and acceptance test structure.
3. Convert the request into player-facing rules: who is affected, what changes, how long it lasts, how it ends, and what the player can see.
4. Check edge cases: stacking, refresh, immunity, login/death cleanup, protection zones, and icon display limits.
5. Present the result as a short spec, a validation report, or Given/When/Then scenarios.

## Output Defaults

- For a feature spec, use `assets/behavior-spec-template.md`.
- For tests, use `assets/test-scenario-template.md`.
- For a review, lead with mismatches from canonical behavior, then missing edge cases, then practical acceptance checks.

## Validation Questions

Before finalizing a condition answer, make sure it covers:

- What the condition does to the player or creature.
- Whether it is harmful, helpful, neutral, or only a marker.
- How it appears on screen.
- How it ends: time, cure, waiting, equipment, zone change, or a special rule.
- Whether it stacks, refreshes, or replaces another effect.
- Whether it survives login, death, or zone changes.

## Common Pitfalls

- Do not treat every icon as a damage condition.
- Do not merge skull, party, war, guild, logout block, or resting-area icons into combat ailments without saying they are broader status markers.
- Do not assume all conditions can be cured.
- Do not assume haste changes attack speed or regeneration speed.
- Do not assume buff and debuff stacking is additive; many same-type conditions refresh instead.
- Do not forget that protection zone rules can suppress some regeneration behavior.
