# Marketeer Data

The full archive of [Melon Marketeer](https://melonmarketeer.com), an Animal Jam Classic price tracker that ran from June to September 2026.

Marketeer's bots visited player dens and recorded what was for sale in their shops, and at what price. This repo is everything it collected. It is free to use for price guides, research or your own tools.

**Download:** grab the files from the [latest release](../../releases/latest).

## Files

| File | What it is |
|---|---|
| `price_observations.csv.gz` | Every shop listing seen: seller, item, price, currency, color, time seen. The main dataset. |
| `item_stats.csv.gz` | Price summary per item and currency: listings, sellers, min, max, average, median. |
| `item_color_stats.csv.gz` | The same summary split by item color. |
| `tradelist_items.csv.gz` | Items players had on their trade lists. |
| `usernames.csv.gz` | Every player username the bots came across, with first and last time seen. |
| `dens.csv.gz` | Every den visited: owner, number of items for sale, visit result. |
| `item_definitions.csv.gz` | Item id to item name lookup, decoded from the game's definition packs. |
| `wiki_items.csv.gz`, `wiki_color_worth.csv.gz` | Worth references collected from the Animal Jam fan wiki. |
| `marketeer-public.sqlite.gz` | All of the above in one SQLite database, plus a `colors` lookup table. |

## Columns worth knowing

- `item_type`: `0` = den item, `1` = pet, `2` = clothing.
- `currency`: `gems` or `diamonds`. In the SQLite file this is `currency_type` (`3` = diamonds, anything else = gems).
- `color_raw`: the color value as the game sends it. For clothing, `color_hex` (`#AARRGGBB`) and `color_name` are our best decode of it. Den items have no color, and pet colors are left raw because they do not decode reliably. Pet looks are in `pet_appearance`.
- Times are UTC. CSVs use ISO 8601. The SQLite file keeps raw milliseconds since 1970.
- `cost` is the asking price the seller set, not a confirmed sale.

## What is not included

- Anyone who asked to be removed from Marketeer.
- The names of our scraper bot accounts.
- Anything from the website itself: Discord logins, shop claims, profiles, uploaded images, reports, watchlists and supporter data.

## Notes

Prices are what sellers asked for, so treat them as a guide. Coverage depends on which dens the bots happened to reach.

Melon Marketeer was an unofficial fan project and was not affiliated with WildWorks. Animal Jam is a trademark of WildWorks. Wiki data comes from the Animal Jam fan wiki community and is shared under its CC BY-SA license.

Made by [glvckoma](https://github.com/glvckoma).
