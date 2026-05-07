# Condition Test Set: [Condition Name]

## Source Rule

[Official rule or compatibility rule being tested.]

## Scenarios

### [Allowed Behavior]

Given [state]
When [condition is applied]
Then [visible effect happens]
And [end state]

### [Refused Behavior]

Given [state]
When [condition should not apply]
Then [the action is refused or ignored]
And [state stays unchanged]

### [Edge Case]

Given [edge case]
When [condition changes]
Then [canonical or compatibility outcome]

## Coverage Notes

- Actors: [player, creature, source, target]
- Timing: [instant, periodic, duration, server save, login]
- Cleanup: [cure, wait, death, zone change, removal]
