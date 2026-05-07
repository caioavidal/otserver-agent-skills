# Canonical House Rules

Use this file for broad Tibia house behavior. Keep outputs player-facing and source-prioritized.

## Canonical Sources

- Official Tibia manual, Houses: `https://www.tibia.com/gameguides/?subtopic=manual&section=houses`
- Tibia Wiki MCP: `getHouseFeatureInfo`
- Tibia Wiki house article: `https://www.tibiawiki.com.br/wiki/Casas`
- Reference implementation: `C:\Sources\forgottenserver-downgrade\src\house.cpp`

Official gameplay behavior wins when sources conflict.

## What Houses Are

- Houses, shops, and guildhalls are rentable private buildings.
- House interiors are protection zones.
- Only invited characters should be able to enter a house.
- A house can safely store and display items because uninvited players cannot enter.
- Containers in houses do not use the normal depot item limit, so houses are commonly treated as unlimited storage.

## Protection And Recovery

- A character standing in a house is protected like in other protection zones.
- A character standing in a protection zone does not regenerate hit points or mana just because they are there.
- Beds allow offline recovery for Premium characters when bed rules are satisfied.
- While sleeping in a bed, a character restores soul points over time.
- Hit points and mana recover while sleeping as long as the character had eaten enough food before going to bed.
- Sleeping can also train skills while the character is offline.

## Getting A House

- A character needs Premium status to rent, bid for, or buy a house.
- An account can rent up to three houses.
- A guild leader can rent one guildhall in addition to house limits.
- A character can only have one house transaction active at a time.
- Official rules require the character to have left Newhaven or Rookgaard before renting or bidding.

## Auctions

- Empty houses can be auctioned through the official website or the Cyclopedia.
- An auction lasts seven days from the first bid.
- A bid is a bid limit, not always the final price.
- The bidder must have enough bank money for the bid limit and the first rent.
- Reserved auction money cannot be spent while the bid is active.
- A confirmed bid cannot be withdrawn.
- A bidder may lower the bid limit to the current highest bid or raise it.
- The winner pays the final winning bid plus the first rent from the bank balance.
- If Premium status ends during an auction, the auction continues. If the player wins as a Free Account, official behavior charges the amount but the house is not assigned and returns to auction.

## Transfers

- A house owner can set up a safe transfer to another character.
- The transfer date must be in the future and no more than 30 days away.
- The owner chooses the receiving character, transfer date, and price.
- The receiver must accept before the transfer date and must have the required bank money.
- The owner can cancel the transfer until the receiver accepts.
- If the receiver rejects, does not accept, or lacks money, the transfer is cancelled.
- If all requirements are met, the transfer happens at the server save on the chosen date.
- The former owner should remove belongings before transfer, because ordinary items left behind become controlled by the new owner unless a server has a special move-out rule.
- Official modern behavior sends Store-purchased house items back to the former owner's inbox.

## Moving Out

- An owner can choose to move out on a date 1 to 30 days in the future.
- Moving out completes at server save on the selected date.
- After moving out, the former owner can bid for or rent another house again.
- Ordinary items left in the house are moved automatically to the former owner's depot inbox in official behavior.

## Rent And Eviction

- Rent is paid in advance.
- Rent is automatically debited from the owner's bank balance.
- Rent is normally due every 30 days.
- If the owner lacks money when rent is due, the owner receives warning letters for one week.
- If rent is not paid during that week, the owner is evicted.
- On rent eviction, belongings are moved to the owner's inbox in official behavior.
- Large furniture that cannot fit in a backpack may remain in the house under official behavior.
- After rent eviction, all characters on the account are blocked from renting, bidding for, or receiving houses for 30 days.
- If the owner is banished, rent still tries to debit the bank normally.

## Premium Expiry

- If Premium status expires, the house is lost at the next server save.
- A Free Account player may still transfer the house before the loss occurs.
- If a transfer and Premium-loss eviction are both scheduled for the same server save, official behavior applies the transfer first.

## Reference Implementation Compatibility Notes

Use these only when the user is working with the supplied downgrade reference or asks about old-server behavior.

- Every house tile is marked as a protection zone.
- On owner change or loss, the old owner's movable pickupable items are moved to the old owner's depot for the house town.
- For non-pickupable containers, contained items may be moved while the container stays.
- Players inside are kicked to the house entry position when ownership changes or access is removed.
- Sleepers in house beds are woken when ownership changes or the house is lost.
- Guest and sub-owner list changes immediately remove players who are no longer invited.
- Door-list changes do not automatically remove players already inside.
- Rent warnings may be tracked as up to seven warning letters before ownership is removed.
