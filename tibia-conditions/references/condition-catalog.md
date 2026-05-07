# Condition Catalog

Use this file to map player language to Tibia condition names and categories.

## Canonical Sources

- Official manual: special conditions section.
- Tibia Wiki special conditions page.
- MCP catalog: `getConditions` and `getConditionByName`.

## Catalog Guide

The MCP catalog is the best quick index for exact player-facing names and short meanings.

### Harmful Conditions

- Agony
- Bleeding
- Burning
- Cursed
- Dazzled
- Drowning
- Electrified
- Freezing
- Poisoned

### Negative Conditions

- Drunk
- Feared
- Hexed
- Powerless
- Rooted
- Slowed

### Positive Conditions

- Haste
- Strengthened
- Magic Shield
- Within Protection Zone
- Within Active Resting Area

### Neutral Conditions

- Hungry
- Logout Block
- Protection Zone Block
- Within Resting Area

### Mixed Or Boss-Linked Conditions

- Bakragore's Taints
- Goshnar's Taints

### Broader Status Markers On The Wiki

- Skull system icons
- Party icons
- War icons
- Guild icons

## Important Lookup Notes

- Some names are shared with spells or other pages, so always verify the meaning before writing a rule.
- The same visible label may mean a status effect, a marker, or a broader system flag.
- If the user says "poison", "haste", or "drunk", check whether they mean the condition, the spell, or the page title.

## When To Use Each Source

- Use the manual for the basic official rule.
- Use the wiki for the expanded player-facing explanation and newer markers.
- Use the MCP catalog when you need a quick condition list or exact page match.
- Use the code only when you need compatibility behavior or exact refresh/removal rules.
