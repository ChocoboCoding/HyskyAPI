# HyskyAPI | Intro
Unofficial Hypixel API created for handling Auctions of Skyblock gamemode with ease and efficiency.

# Working with the API
The root access of the API is at https://hysky.000webhostapp.com/apihandle.php

So let me tell you how this API exactly works: 

- First of all there is a cron job that is triggered every **2 minutes** to update (cache) literally every single (Not ended) auction on skyblock.
- Then apihandle.php is what's actually sorting, searching and returning the JSON output of the request through all the Cached auctions.
And that's it really!
- Note that every request will only return up to 200 auctions to ensure convenience and quality performance of the API.

So First of all let's take a look at what are we actually going to be working with:
(Example Output)

```
{
  "item_name": "Spicy Midas' Sword",
  "starting_bid": 10,
  "highest_bid_amount": 74522876,
  "category": "weapon",
  "bid_num": 44,
  "latest_bid": {
    "auction_id": "a9cf36f0f5d1451e86de806af93f91d7",
    "bidder": "30a781a70b4e47a3bbdc1da4e85e1b04",
    "profile_id": "30a781a70b4e47a3bbdc1da4e85e1b04",
    "amount": 74522876,
    "timestamp": 1575039182110
  },
  "tier": "LEGENDARY",
  "end": 1575143380853,
  "highest": 74522876,
  "auctioneer": "7d07eaffb73544e08b998230769efc68",
  "item_lore": "§7Damage: §c+290 §e(+20)\n§7Strength: §c+145 §e(+20) §8(Spicy +5)\n§7Crit Chance: §c+1% §8(Spicy +1%)\n§7Crit Damage: §c+110% §8(Spicy +50%)\n§7Attack Speed: §c+10% §8(Spicy +10%)\n\n§9Critical VI, §9Cubism V\n§9Ender Slayer VI, §9Execute V\n§9Experience IV, §9First Strike IV\n§9Giant Killer VI, §9Impaling III\n§9Lethality V, §9Life Steal IV\n§9Looting III, §9Luck V\n§9Scavenger III, §9Sharpness VI\n§9Telekinesis I, §9Vampirism VI\n\n§6Item Ability: Greed\n§7The strength and damage bonus of\n§7this item is dependant on the\n§7price paid for it at the §5Dark\n§5Auction§7!\n§7The maximum bonus of this item\n§7is §c120 §7if the bid was\n§7§650,000,000 Coins §7or higher!\n\n§7Price paid: §650,040,000 Coins\n§7Strength Bonus: §c120\n§7Damage Bonus: §c120\n\n§6§lLEGENDARY SWORD",
  "uuid": "a9cf36f0f5d1451e86de806af93f91d7",
  "endingtime": 313.0308833333333,
  "item_count": "1",
  "anvils": "5"
}
```

**Let's learn a little bit more about this JSON output:**
- **item_name, starting_bid, highest_bid_amount, category, tier:** Pretty straight forward.
- **bid_num:** Number of bids.
- **latest_bid:** Array containing UUID and other data of the latest player bidding on the auction.
- **end:** Ending time in milliseconds (UNIX).
- **highest:** (used to sort through the auctions on server side).
- **auctioneer:** UUID of the player who created the auction.
- **item_lore:** Item description and details.
- **endingtime:** Ending time in **Minutes**.
- **item_count:** Amount of the items.
- **anvils:** Anvil uses.

Now let's get into how to make requests to the API:

```https://hysky.000webhostapp.com/apihandle.php?key={API_KEY}&req=top```

**This will return the (first 200) most expensive auctions.

---

```https://hysky.000webhostapp.com/apihandle.php?key={API_KEY}&req=search&query={SEARCH_QUERY}```

This will search through the given search query, also note that this exactly works like skyah's search, so if you entered "/ah Mlotov" in the query it will only show the available auctions of that player only.
To get very specific results please remove any white spaces between words, ex: "StrongDragonBoots".

Here's a list of features you can make use of in the search query:

- Smart search, more on that here -> https://skyah.cc/smart

- /ah {Playername} -h to show a player's auctions history.

- /ebs {Enchants} to search for enchanted items, add "book" or "potion" at the end to search for only books or potions.


