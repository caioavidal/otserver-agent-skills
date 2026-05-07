# House Behavior Test Generation

Use this file when writing unit tests, integration tests, scenario tests, acceptance criteria, or validation plans for house behavior.

Keep test names and steps focused on what the player sees. Avoid engine-specific terms unless the user asks for implementation details.

## Test Style

- Use Given/When/Then phrasing.
- Test one visible rule per case.
- Include one allowed case and at least one refused case for every permission rule.
- Include after-effects: list changes, door state, kicked position, item movement, rent deadline, warning, or eviction.
- Include timing when behavior occurs at server save or after a warning period.
- Prefer roles over internals: owner, sub-owner, guest, uninvited player, guild member.

## Core Coverage Areas

- Ownership: Premium requirement, account house limit, guildhall leader requirement, one active transaction.
- Auctions: bid limit, reserved money, no withdrawal, seven-day duration, first rent payment.
- Transfers: receiver acceptance, transfer date, bank funds, cancellation, server-save completion.
- Rent: automatic bank debit, warning period, eviction after seven days, 30-day account block.
- Premium expiry: loss at next server save, transfer before loss when both happen together.
- Guest access: invited entry, uninvited refusal, removed guest loses access.
- Door access: closed-door refusal, door-authorized opening, open-door passage for invited characters.
- Sub-owners: guest-list editing, kicking, owner-only sub-owner editing.
- List syntax: exact names, wildcards, single-character wildcard, exclusions, comments, guilds, rank rules, list limits.
- House spells: caster location, permission, target selection, successful outcome, failure outcome.
- Beds: Premium sleeping, offline soul recovery, food-dependent hit point and mana recovery, skill training.
- Items: storage safety, move-out item return, eviction item return, large furniture exception if relevant.
- Protection: house tile is safe, but standing there does not itself regenerate hit points or mana.

## Permission Matrix To Check

| Actor | Enter House | Open Closed Door | Edit Guest List | Edit Sub-Owners | Edit Door List | Kick Others |
| --- | --- | --- | --- | --- | --- | --- |
| Owner | Yes | Yes | Yes | Yes | Yes | Yes |
| Sub-owner | Yes | Server-era dependent | Yes | No | Confirm server-era rule | Yes |
| Guest with door rights | Yes | That door only | No | No | No | No |
| Guest without door rights | Yes if reachable | No | No | No | No | No |
| Uninvited player | No | No | No | No | No | No |

When testing a specific server, replace "server-era dependent" with the chosen rule and add one compatibility test.

## High-Value Edge Cases

- A guest is invited but the front door is closed and they are not on the front-door list.
- A guest is not on a door list but the interior door is already open.
- A wildcard invite also matches an unwanted character.
- An exclusion appears after a wildcard allow.
- A sub-owner tries to edit the sub-owner list.
- A guest tries to use `alana sio` on another guest.
- A player removes an invited character while that character is standing inside.
- Rent is due with insufficient bank funds.
- Rent remains unpaid after the warning period.
- A house transfer and Premium expiry are scheduled for the same server save.
- A move-out leaves ordinary items and large furniture behind.

## Review Checklist

- Does every rule name the actor and target?
- Does every refusal leave the house state unchanged unless a source says otherwise?
- Does every server-save rule avoid happening immediately?
- Are bank funds checked where the official rules require them?
- Are access lists separate from door lists?
- Are compatibility choices labeled instead of mixed into official behavior?
