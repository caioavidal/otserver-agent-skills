# Shared Experience

Use this file for the rules that govern shared experience in a party.

## Canonical Sources

- TibiaWiki Party: shared-experience section
- Tibia Fandom Party: shared-experience section
- Reference implementation: `C:\Sources\forgottenserver-downgrade\src\party.cpp`

## Core Rule

- Shared experience is leader-controlled.
- It should only be active when the party is eligible.
- If eligibility is lost, shared experience should turn off or become inactive until the party qualifies again.

## Common Eligibility Rules

- Members must be close enough to the leader.
- The lowest party level must be at least two-thirds of the highest party level.
- Members must be within the allowed level range.
- Members must be actively contributing according to the ruleset in use.
- If low stamina changes the share, note that explicitly in the acceptance criteria.

## Source Differences

- TibiaWiki and Fandom disagree on the exact vocation mix bonus percentages.
- TibiaWiki says the bonus split is 20% / 35% / 70% / 100%.
- Fandom says the bonus split is 20% / 30% / 60% / 100%.
- TibiaWiki describes activity as healing or attacking; Fandom describes contribution within the last 2 minutes.
- TibiaWiki says the range is 30 squares including one floor above or below.

## Player-Visible Behavior

- Shared experience can be toggled by the leader.
- The party interface should show whether shared experience is active or inactive.
- When shared experience is on, the experience should be split according to the party ruleset and fractional results should round up.
- In some rulesets, active members can also gain soul points.

## Compatibility Notes

- The reference implementation re-checks eligibility when party combat points change.
- The reference implementation can represent shared experience as activated but currently disabled if members fail the checks.
- Use that only as a compatibility note when the user is working with the supplied downgrade server.
