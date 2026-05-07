# Condition Test Generation

Use this file when writing unit, integration, scenario, or acceptance tests for conditions.

## Test Style

- Use player-facing language.
- Test one rule per scenario.
- Always include the visible effect and the visible end state.
- Include timing when the condition ends by time or server save.
- Include cleanup when the condition ends through death, login, zone change, or cure.

## Core Coverage Areas

- Damage over time: apply, tick, cure, and expiry.
- Movement loss: rooted, feared, slowed, drunk.
- Defense and buffs: haste, magic shield, strengthened, hungry.
- Area markers: protection zone, protection zone block, logout block, resting area.
- Stacks: taints and other multi-stage conditions.
- Visibility: icons, icon limits, and `...` overflow.
- Cleanup: login restore, death removal, refresh, replacement, immunity.

## Scenario Checklist

- Who caused the condition?
- What condition did the player get?
- How long should it last?
- What can the player still do?
- What visible icon or message appears?
- What ends it?
- What should remain unchanged?

## Common Edge Cases

- A stronger same-type condition replaces a weaker one.
- A finite condition should not replace an indefinite one.
- A condition should not continue after death if it is not meant to persist.
- Protection-zone state should not be confused with healing.
- Ambiguous names should be resolved before building the test.

## Output Template

### Allowed Behavior

Given [state]
When [condition is applied]
Then [visible effect happens]
And [end state]

### Refused Behavior

Given [state]
When [condition should not apply]
Then [no effect happens]
And [state stays unchanged]
