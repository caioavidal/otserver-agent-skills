---
name: tibia-house-systems
description: Use this skill when a task involves Tibia houses, guildhalls, house ownership, rent, auctions, transfers, guest lists, sub-owners, door rights, house spells, beds, house item safety, eviction, or validating and generating gameplay tests for house behavior. It turns house features into player-facing rules, expected outcomes, edge cases, and acceptance criteria while staying language-agnostic and independent of engine architecture.
metadata:
  domain: tibia-house-gameplay
  version: "1.0"
---

# Tibia House Systems

Use this skill to reason about Tibia house features from the player's point of view. Keep the answer non-technical unless the user explicitly asks for implementation details.

## Ground Rules

- Speak in gameplay terms: owner, guest, sub-owner, door, rent, bank balance, server save, invitation, eviction.
- Do not assume any engine layout, database shape, item model, or scripting language.
- Prefer official gameplay behavior when sources disagree.
- Use the reference implementation only to clarify expected outcomes or old-server compatibility, not to override official rules.
- When a rule depends on server-era behavior, state the official rule first, then call out the compatibility choice.
- For implementation requests, define the behavior and acceptance checks before discussing code changes.

## Source Priority

Use sources in this order:

1. Official Tibia manual house behavior.
2. Tibia Wiki MCP `getHouseFeatureInfo` and the Tibia Wiki house article.
3. Reference implementation behavior from the supplied OTServer files.

If the sources disagree, follow the official rule and mention the lower-priority behavior as a compatibility note only when it affects the user's task.

## Workflow

1. Identify the house area involved: ownership, auction, transfer, rent, eviction, access lists, doors, spells, beds, items, protection zone, or tests.
2. Read only the needed reference file:
   - `references/canonical-house-rules.md` for broad house ownership, rent, transfer, beds, items, and protection behavior.
   - `references/access-lists.md` for guests, sub-owners, door rights, wildcards, guild patterns, and exclusions.
   - `references/house-spells.md` for `aleta sio`, `aleta som`, `aleta grav`, and `alana sio` behavior.
   - `references/test-generation.md` when producing test cases or acceptance checks.
3. Convert the request into player-facing rules: who can act, where they must be, what must already be true, what changes, and what must be refused.
4. Check the result against source priority and the relevant edge cases.
5. Present the outcome as a short feature spec, validation report, or Given/When/Then scenarios.

## Output Defaults

For a feature specification, use `assets/behavior-spec-template.md` if the user wants a spec or the request is ambiguous.

For tests, use `assets/test-scenario-template.md` and keep each case focused on one visible outcome.

For a review or validation, lead with mismatches from canonical behavior, then missing edge cases, then suggested acceptance checks.

## Validation Questions

Before finalizing house behavior, make sure the answer covers:

- Who is acting: owner, sub-owner, guest, door-authorized guest, uninvited player, guild member, or account-limited character.
- Where the character is: inside the house, outside the house, facing a door, standing in a doorway, sleeping in a bed, or away from the target.
- Whether the action is allowed, refused, delayed until server save, or dependent on bank funds.
- What happens afterward: list changes, door access, entry, kicking, item movement, bed wake-up, rent extension, eviction, or auction availability.
- What is intentionally not covered because it belongs to a different system.

## Common Pitfalls

- Do not treat a guest invitation as permission to open closed doors.
- Do not forget that open doors can let invited characters pass even without door rights.
- Do not let broad wildcard invites hide exclusion rules; exclusions need to be evaluated before broad allows.
- Do not model rent as a manual payment action; official behavior debits the bank automatically.
- Do not forget the seven-day warning period before rent eviction.
- Do not say house interiors regenerate hit points or mana by themselves; beds provide offline recovery under their own rules.
- Do not assume sub-owners have every owner power. They can invite and kick; owner-only powers need explicit confirmation.
