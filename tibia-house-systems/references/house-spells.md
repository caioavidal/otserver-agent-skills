# House Spells

Use this file for gameplay behavior of Tibia house spells. Keep spell outcomes player-facing.

## Spell Summary

- `aleta sio`: edit the guest list.
- `aleta som`: edit the sub-owner list.
- `aleta grav`: edit one door's access list.
- `alana sio "character"`: kick a character out of a house.

## `aleta sio` - Guest List

- Opens the guest list for the house.
- The caster must be standing inside the house.
- The owner can use it.
- A sub-owner can use it when they have active sub-owner rights.
- The result is a list of characters, wildcard rules, guild rules, and exclusions that determine who may enter.
- Removing a character from the guest list should remove their invitation.
- Compatibility note: the supplied downgrade reference immediately kicks characters inside the house if they are no longer invited after the guest list changes.

## `aleta som` - Sub-Owner List

- Opens the sub-owner list for the house.
- The caster must be standing inside the house.
- Only the owner should be able to edit this list.
- Sub-owners are invited and gain the right to edit guests and kick characters.
- Tibia Wiki MCP behavior lists 10 sub-owners as the maximum.
- Only Premium players can actively use sub-owner powers in official/wiki behavior.
- Compatibility note: the supplied downgrade reference immediately kicks characters inside the house if they are no longer invited after the sub-owner list changes.

## `aleta grav` - Door Rights

- Opens the access list for one house door.
- The caster must target the relevant house door by facing it, standing in the doorway, or otherwise meeting the server's door targeting rule.
- Official behavior describes this as an owner action.
- Each door has a separate list, including the front door.
- The list controls who may open and close that specific door.
- Invited characters may pass through an already open door even without door rights.
- The spell should fail if the caster is not targeting a door that belongs to the current house.
- Compatibility note: the supplied downgrade reference opens a door-list window only if the caster is in the house and the targeted position resolves to one of that house's doors.

## `alana sio "character"` - Kick Character

- Kicks the named character out of the house.
- The target must be inside a house where the caster has kick rights.
- Owners and sub-owners can kick other characters from their house.
- Any character can kick themselves out of a house.
- Tibia Wiki MCP behavior allows this spell to be used from outside the house and at unlimited range, as long as the target is in a house where the caster has rights.
- A successful kick places the target outside, at the house entry area.
- The spell should fail if the target is not in that house or the caster lacks sufficient rights.
- Compatibility note: the supplied downgrade reference falls back to targeting the caster if the named player is not found.

## Failure Outcomes

Use a simple player-facing refusal unless the user asks for exact messages.

- The spell should fail outside a valid house when the spell requires being inside.
- The spell should fail when the caster lacks the required house right.
- `aleta grav` should fail when no valid house door is targeted.
- `alana sio` should fail when the target cannot be kicked from that house.

## Spell Test Checklist

- Correct actor: owner, sub-owner, guest, uninvited player, or self-kicking character.
- Correct location: inside house, outside house, facing door, or target inside house.
- Correct target: guest list, sub-owner list, specific door, or named character.
- Correct result: edit window opens, target is kicked, or action is refused.
- Correct side effect: invitation changes, immediate removal if applicable, or door permissions remain separate.
