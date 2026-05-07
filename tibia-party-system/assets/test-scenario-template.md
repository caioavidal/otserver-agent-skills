# Party Behavior Test Set: [Feature Name]

## Source Rule

[Primary rule or compatibility rule being tested.]

## Scenarios

### [Allowed Behavior]

Given [party state]
When [the actor performs the action]
Then [the visible outcome happens]
And [important side effect or unchanged state]

### [Refused Behavior]

Given [party state]
When [the actor performs an action they should not be allowed to perform]
Then [the action is refused]
And [the party state remains unchanged]

### [Edge Case]

Given [edge-case party state]
When [the action happens]
Then [the canonical or compatibility outcome happens]

## Coverage Notes

- Actors covered: [leader, member, invited player, outsider]
- Timing covered: [immediate, logout, leave, disband, shared-exp toggle]
- Systems covered: [invites, leadership, shared experience, loot access, party spells]
