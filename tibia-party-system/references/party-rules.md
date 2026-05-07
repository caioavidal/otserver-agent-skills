# Party Rules

Use this file for the player-facing party lifecycle: forming, inviting, joining, leading, leaving, disbanding, and party status markers.

## Canonical Sources

- TibiaWiki Party: `https://www.tibiawiki.com.br/wiki/Party`
- Tibia Fandom Party: `https://tibia.fandom.com/wiki/Party`
- Reference implementation: `C:\Sources\forgottenserver-downgrade\src\party.cpp`

## Core Roles

- Leader: the player who formed the party, or the member who received leadership.
- Member: a player who has accepted the invite and joined.
- Invited player: a player who has been asked to join but has not accepted yet.
- Invite sender / inviter: the leader or current leader-authorized actor who issued the invite.

## Forming And Joining

- A party starts when a player invites someone and the invite is accepted.
- A player can belong to only one party at a time.
- Joining is not the same as being invited.
- All party members should be placed in the party channel.

## Leadership

- The leader controls invitations and shared experience in the player-facing rules.
- Leadership can be transferred to another member.
- If the leader leaves or logs out, leadership can move to another member or the party can end if nobody remains.
- Leadership changes should be visible to the party.

## Leaving And Disbanding

- A player can leave their party.
- The party can also be disbanded.
- When the party ends, members and invitees should lose party state and the party channel should close.
- If the leader leaves and no replacement is available, the party ends.

## Party Markers

- Party markers can show leader, member, invited-by-you, invited-you, and shared-experience state.
- One source says these markers are only visible to party members.
- Treat marker visibility as player-facing UI behavior, not a combat rule.

## Access And Restrictions

- A player already in a party should not be able to join another one.
- Invite revocation should remove the invite state.
- Rejected or cancelled invites should leave the party intact unless it becomes empty.
- Keep party behavior separate from guild, war, and skull systems.
