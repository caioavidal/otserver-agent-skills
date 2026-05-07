# Access Lists And Door Rights

Use this file when the task involves who may enter, who may open doors, list syntax, wildcards, guild permissions, exclusions, or access validation.

## Access Roles

- Owner: has ultimate access to the house and controls house rights.
- Sub-owner: is invited to the house and can invite or uninvite guests and kick characters from the house.
- Guest: may enter reachable parts of the house but cannot open or close closed doors unless listed for that door.
- Door-authorized character: may open and close the specific door whose list includes them.
- Uninvited character: should not be able to enter the house.

## Owner Rights

- The owner always has access to the house.
- The owner can edit the guest list.
- The owner can edit the sub-owner list.
- The owner can edit door access lists.
- The owner can kick characters from the house, subject to any server-specific protection for staff or special accounts.

## Sub-Owner Rights

- Sub-owners can edit the guest list.
- Sub-owners can kick guests or unwanted visitors from the house.
- Only Premium players can actively use sub-owner powers in official/wiki behavior.
- A house can have up to 10 sub-owners according to Tibia Wiki MCP behavior.
- Do not assume sub-owners can edit the sub-owner list or door lists unless the target server explicitly chooses that compatibility rule.

## Guest Rights

- A guest can enter the house when the path is reachable.
- A guest can enter rooms through open doors.
- A guest cannot open or close a closed door unless that door's access list allows it.
- If the front door is closed and the guest lacks front-door rights, the guest cannot enter even though they are invited.

## Door Rights

- Each house door has its own access list.
- The front door also has a door access list.
- Door rights decide who may open and close that door.
- Door rights do not replace the house invitation list; a character still needs a valid way to be treated as invited or authorized by the house rules.
- If a door is already open, invited characters may pass through even without door rights.
- Official behavior guarantees the owner access to every door.
- Compatibility note: the supplied downgrade reference treats sub-owners as automatically able to use house doors.

## List Syntax

- Put one rule per line.
- A plain character name invites or authorizes that character.
- `*` can match any amount of text.
- A lone `*` invites everyone.
- `?` matches one character.
- `!Name` excludes a matching character.
- Exclusions should appear before broad allows because lists are interpreted top-to-bottom in Tibia Wiki MCP behavior.
- `#` at the start of a line is a comment and has no effect.
- `*@Guild Name` authorizes all members of a guild.
- `Rank Name@Guild Name` authorizes members of a specific guild rank.

## List Limits

- Tibia Wiki MCP behavior says a list can contain at most 100 lines.
- Tibia Wiki MCP behavior says a list can contain at most 1999 characters.
- If the submitted list is too large, the edit should not be accepted and the previous list should remain.
- Compatibility note: the supplied downgrade reference processes up to 100 lines and ignores very long lines.

## Safety Rules

- Wildcards can invite future characters whose names did not exist when the list was written.
- Deleted characters may remain in old invitation lists by name.
- A newly created character with a previously invited name can become invited if the server still uses name-based matching.
- Prefer exact character names when the house should be private.
- Put exclusions before broad wildcard, guild, or rank rules.

## Validation Checklist

- Is the player on the guest list, sub-owner list, owner account, door list, guild rule, or excluded by a higher rule?
- Is the relevant door open or closed?
- Is this the front door or an interior door?
- Does the action require entering, opening, closing, editing, or kicking?
- Is the actor Premium if they rely on sub-owner powers?
- Are broad wildcard rules safely limited by exclusions?
