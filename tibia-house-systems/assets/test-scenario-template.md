# House Behavior Test Set: [Feature Name]

## Source Rule

[Official rule or compatibility rule being tested.]

## Scenarios

### [Allowed Behavior]

Given [house state and actor role]
When [the actor performs the action]
Then [the visible outcome happens]
And [important side effect or unchanged state]

### [Refused Behavior]

Given [house state and actor role]
When [the actor performs an action they should not be allowed to perform]
Then [the action is refused]
And [the house state remains unchanged]

### [Edge Case]

Given [edge-case state]
When [the action happens]
Then [the canonical or compatibility outcome happens]

## Coverage Notes

- Actors covered: [owner, sub-owner, guest, uninvited, guild member]
- Timing covered: [immediate, server save, warning period]
- Lists covered: [guest, sub-owner, door, wildcard, guild, exclusion]
