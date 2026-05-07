---
name: tibia-party-system
description: Use this skill when a task involves Tibia party behavior, invites, leadership, shared experience, loot access, party channel, party spells, leaving, disbanding, or validating and generating gameplay tests for party rules. It turns party features into player-facing rules, expected outcomes, edge cases, and acceptance criteria while staying language-agnostic and independent of engine architecture.
metadata:
  domain: tibia-party-gameplay
  version: "1.0"
---

# Tibia Party System

Use this skill to reason about Tibia party behavior from the player's point of view. Keep answers non-technical unless the user asks for implementation details.

## Ground Rules

- Speak in gameplay terms: leader, member, invite, join, leave, disband, shared experience, loot access, party channel, party buff.
- Do not assume any engine layout, data model, or scripting language.
- Prefer player-facing sources first. Use TibiaWiki as the primary behavior reference, Fandom as a cross-check, and the supplied reference implementation only for compatibility notes.
- If sources disagree, state the difference instead of merging them silently.
- Treat party spells as party support behavior, not generic combat spells.

## Source Priority

Use sources in this order:

1. TibiaWiki Party page.
2. Tibia Fandom Party page.
3. Reference implementation in `party.cpp` and `data/spells/scripts/party`.

If the sources disagree, explain which rule you are using and why. If the user does not specify a server era, prefer the most current player-facing behavior and note older compatibility differences.

## Workflow

1. Identify the party area: invite and join, leadership, leaving and disbanding, shared experience, loot access, icons, party channel, or party spells.
2. Read only the needed reference file:
   - `references/party-rules.md`
   - `references/shared-experience.md`
   - `references/party-spells.md`
   - `references/engine-notes.md`
   - `references/test-generation.md`
3. Convert the request into player-facing rules: who can act, who is affected, what must already be true, what changes, and what the visible result is.
4. Check edge cases: one-party-only limit, invite acceptance, leadership transfer, range and level checks, shared experience activation, and party marker visibility.
5. Present the result as a short spec, validation report, or Given/When/Then scenarios.

## Output Defaults

- For a feature spec, use `assets/behavior-spec-template.md`.
- For tests, use `assets/test-scenario-template.md`.
- For a review, lead with rule mismatches, then missing edge cases, then practical acceptance checks.

## Validation Questions

Before finalizing a party answer, make sure it covers:

- Who is the leader.
- Whether the target has been invited and accepted.
- Whether the player is already in another party.
- Whether shared experience is enabled and all members still qualify.
- Whether members are close enough and active enough for the chosen ruleset.
- Whether the request is about current behavior or compatibility behavior.
- Whether the party spell has a visible effect and who is allowed to cast it.

## Common Pitfalls

- Do not assume a player can join two parties.
- Do not assume invitation and membership are the same thing.
- Do not assume shared experience stays on automatically.
- Do not mix party icons with guild or war markers.
- Do not treat party buffs as universal spells; they are party-targeted support effects.
- Do not hide source conflicts when wiki pages disagree.
