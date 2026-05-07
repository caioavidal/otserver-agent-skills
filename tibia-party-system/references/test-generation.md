# Party Test Generation

Use this file when writing unit tests, integration tests, scenario tests, or acceptance criteria for party behavior.

## Test Style

- Use player-facing language.
- Test one visible rule per case.
- Include the invited state, the accepted state, and the active member state separately.
- Include side effects: party channel, icon refresh, shared experience, leadership transfer, or disband messages.
- Include timing when a rule depends on leader logout, leave actions, or temporary shared-experience checks.

## Core Coverage Areas

- Invite flow: invite, accept, revoke, reject.
- Membership: one party only, join success, join refusal.
- Leadership: transfer, leader leave, leader logout.
- Shared experience: toggle, disable, re-enable, level-range failure, distance failure, activity failure.
- Loot access: corpse opening by leader or member.
- Party spells: visible buff, range, duration, and any permission checks.

## Common Edge Cases

- An invited player is already in another party.
- The leader leaves while members remain.
- Shared experience is on, but one member is too far away.
- Shared experience is on, but the level gap is too large.
- A party is empty after invite revocation or leaving.
- A party spell is cast, but the target is not a valid party member.

## Output Template

### Allowed Behavior

Given [party state]
When [action]
Then [visible outcome]
And [important side effect]

### Refused Behavior

Given [party state]
When [invalid action]
Then [action is refused]
And [party state stays unchanged]
