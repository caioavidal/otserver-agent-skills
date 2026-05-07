# Engine Notes

Use this file only when the user wants implementation or compatibility details.

## Party Lifecycle In Code

- Party creation assigns a leader.
- Invites must be accepted before membership starts.
- Revoking an invite removes invite state and can end an empty party.
- Leaving broadcasts a party-leave message and updates icons.
- Disbanding clears members, invitees, party chat, and shared-experience state.

## Shared Experience In Code

- The leader toggles shared experience.
- Eligibility is rechecked against level, range, and activity rules.
- Party members receive the shared experience payout when the system is active.
- The code can keep shared experience flagged on while temporarily disabled by failed checks.

## Loot And Corpse Access

- A corpse can be opened by the party leader or by a player in the same party as the corpse owner.
- If the user is asking about loot, distinguish corpse access from automatic loot splitting.

## PvP And Harm

- The wiki sources disagree on whether party members can be harmed in PvP contexts.
- Treat this as server-era dependent and state the chosen rule explicitly in specs and tests.

## Visible Side Effects

- Invite, join, leave, revoke, leadership transfer, shared-experience toggle, and disband actions all send player-facing messages.
- Party channel open and close behavior is part of the user-visible lifecycle.
- Party and shield icons are refreshed when state changes.

## Compatibility Notes

- The reference implementation is stricter than some wiki summaries about active participation.
- Use this file to describe server-specific behavior, not to override the player-facing source rules.
