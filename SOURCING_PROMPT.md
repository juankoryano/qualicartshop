# Qualicart product sourcing prompt (reusable, version 5, works in ChatGPT and Claude)

What changed from version 4 (owner decisions, 14 Nov 2026):
- Two price tiers. Standard products (Australian price under A$300) need a price of at least 3x base cost (200%+ markup). High-ticket products (A$300+) need at least 2x base cost (100%+ markup) and have no profit cap.
- Pooled AliExpress "Choice" listings (no store stats) are now allowed if every other rule passes; flag them in the report.
- High-ticket items may take up to 18 days to deliver, but only if the seller ships within 24 hours of the order being placed.
- Search starts from AliExpress best-sellers and matches them to the identical item on Amazon AU (generic products work best; branded items rarely reach 2-3x).
- Unshippable or sold-out variants are deleted in DSers after import.

How to use it:
1. Copy everything in the block below into a new chat and fill in WHAT I WANT.
2. In ChatGPT, use a mode that can browse (agent mode or search). Plain chat can't check live prices and the prompt tells it not to guess.
3. If the assistant can use a browser signed in to your AliExpress and DSers, it can do every step and add products to DSers. If it can only read public pages, it gives you a "Check in DSers" list instead.

```
Find products on AliExpress for my Qualicart store that sell in Australia at a big markup, check every rule below, and add the ones that pass to my DSers import list. Report ONLY the products that pass. Mention rejects in one short line at most. If you can't find enough, keep searching other products and niches before stopping, and say honestly how many you found.

STORE CONTEXT
- Qualicart (qualicartshop.com), Shopify, prices in AUD, dropshipping from AliExpress through DSers.
- Sells to Australia only for now (check New Zealand delivery too if you can, and say if you didn't).
- Also selling on Kogan Marketplace.
- Payments: PayPal only, so Shopify adds its 2% third-party transaction fee.
- Never type passwords, never log in for me, never place orders, never pay, never push to Shopify or publish, never solve CAPTCHAs or slider checks. If a page needs a login or shows a bot check, stop and ask me.

WHAT I WANT THIS TIME
- Niche(s): [e.g. "tools and home improvement", "car accessories", "organizers", or "you choose"]
- Tier: [standard / high-ticket / both]
- How many products: [e.g. 5]

HONESTY RULES (most important)
A. Every number (price, cost, shipping, delivery dates, rating, sold count, feedback %, followers, marketplace price) must come from a page you opened in this session, with the link. Never estimate or fill from memory.
B. If something wasn't shown or you couldn't open the page, write NOT VERIFIED. A product with NOT VERIFIED on a pass/fail rule is not approved; list it under "Needs checking by you".
C. State the date checked and the exchange rates used (USD to AUD, AUD to PHP) and their source.
D. Markup is always a percent: markup % = (price - base cost) / base cost x 100. Never an AUD amount.

THE TWO TIERS
| | Standard | High-ticket |
|---|---|---|
| Typical Australian price | under A$300 | A$300 or more |
| Minimum selling price | base cost x 3 (200%+ markup) | base cost x 2 (100%+ markup) |
| Clean profit per sale | PHP 1,000 to 10,000 | more than PHP 1,000, no cap |
| Delivery to Australia | 5-14 days | up to 18 days, only if the seller ships within 24 hours of the order (show where the page says so; if not shown, NOT VERIFIED) |
| Shipping cost | free or at most US$1.99 | free or at most US$1.99 |
In both tiers the selling price must also be BELOW the typical Australian price. If the only way to reach the minimum is pricing at or above the Australian price, reject.

HOW TO FIND PRODUCTS THAT PASS (what has worked)
1. Start from AliExpress best-sellers in the niche (sorted by orders), then search Amazon AU for the same item using the first 6-8 words of the AliExpress title, and compare photos side by side. Generic products whose Amazon AU listing reuses the AliExpress photos or title are where 3x gaps exist.
2. Branded products (Godox, FeiyuTech, Viltrox, KZ, etc.) are usually only 1.2-2.8x cheaper on AliExpress; they rarely pass 3x and are hard to get to 2x.
3. Big gaps between DIFFERENT brands or models don't count (e.g. a generic trail camera vs a Moultrie). Same model, same contents, same size only.
4. Standard tier: the Australian price needs to be about A$40+ and the AliExpress base cost about a third of it. High-ticket: Australian price A$300+ and base cost about half.
5. Skip very bulky items (they get "Oversized" shipping of US$20+).
6. Products that passed this way: 10-19 mm universal socket with drill adapter (222%), hanging suitcase shelves (250%), round EV charging-cable bag (303%).

SUPPLIER RULES
1. Regular store listing ("Sold By <store>" with feedback % and followers): rating 4.5+, 20+ sold (the product's own count), store feedback 90%+, store followers 100+.
2. Pooled "Choice" listing (no store stats shown): allowed if rating 4.5+, 20+ sold and every other rule passes. Say "pooled - no store stats" in the report.
3. Cheapest passing seller: compare all sellers of the SAME product (same model, contents, pack size, variant) and pick the lowest DSers cost + shipping among those that pass. An official or brand store is NOT required.

SHIPPING AND DELIVERY
4. Must ship to Australia. Shipping free or at most US$1.99 (in USD, as DSers shows it) for the exact variant.
5. Delivery limit per the tier table (use the upper date shown, counted from today).
6. Check shipping per variant: one colour or size can show "No shipping methods are available" while another ships.

COST
7. Base cost = DSers "product cost" for the exact variant (the stable API price shown in the DSers box, not the new-shopper page price) + shipping, converted to AUD.
8. Base cost must be at least A$10.

PRICE PROOF (Amazon AU, Kogan or eBay AU)
9. Find the SAME product (same model, contents, pack size, size in cm; compare photos and the "package includes" list) on Amazon AU, Kogan or eBay AU. Use 2-3 listings when they exist; if only one exists, say so. Similar-but-different products don't count. No identical listing = reject.
10. Selling price = below the typical (lowest/middle) Australian price, rounded to .95, and at least the tier minimum.

PROFIT AFTER FEES
11. Shopify sale: fees = 2% Shopify + PayPal 4.4% + A$0.30 (unless I give my real rate). Clean profit = price - base cost - fees.
12. Kogan sale: fees = about 10% commission (plus A$50/month store fee, not per sale). Clean profit = price - base cost - commission.
13. Convert clean profit to PHP. Show both channels. Must be more than PHP 1,000 on both; standard tier also at most PHP 10,000.

RISKY PRODUCTS AND PLUGS
14. Batteries, rechargeable/USB electronics, Bluetooth or other radio, RC toys, mains-powered items, strong magnets, knives, and brand/character goods are allowed ONLY if Kogan sells the same kind of product; give the Kogan link. A Kogan listing doesn't prove the exact AliExpress unit is compliant; say so.
15. Mains plugs must be AU plug (3-pin 230V); exclude other plug variants.
16. Avoid probable clones of brand items sold by non-official stores at suspiciously low prices, and unlicensed character/movie designs.

VARIANTS AND PHOTOS
17. Check the variant you priced matches the Australian listing (model, size, colour, pack, contents). Don't trust AliExpress's "AI overview" for contents; use the variant photo, the "Color/Size" label and the per-piece price line.
18. Note very low stock ("Only 2 left") in the report.

WHAT TO DO WITH PASSING PRODUCTS
19. Add to the DSers import list only (the "Add To DSers" button in the main product section of the AliExpress page). Confirm "AliExpress product import success!" and that it shows at the top of dsers.com/application/import_list. Don't push to Shopify.
20. In DSers, open the product (pencil > Variants) and delete variants that show stock 0 or don't ship to Australia, then Save. Leave other variant choices for me and list them in "Before publishing".
21. Close every browser tab you opened when you finish (close the first tab of your group last).

REPORT BACK (tables in the reply only; no spreadsheet or file unless I ask)
- One line: access level, date, exchange rates and source.
- One table of PASSING products with: Product | AliExpress link | Store (feedback %, followers, or "pooled") | Rating / sold | Variant | DSers cost + shipping (USD) | Base cost (AUD) | AU delivery (days) | Australian listings used (marketplace, price, link) | Kogan check (if risky) | Tier | Suggested price | Markup % | Clean profit via Shopify (AUD and PHP) | Clean profit via Kogan (AUD and PHP) | Added to DSers (yes/no)
- "Before publishing" notes per product (variants to remove, low stock, single price-proof listing, compliance).
- "Needs checking by you" list (NOT VERIFIED items).
- Rejects: one line total at most.
- Running list of everything added to DSers so far, with which tier rule each one meets.
```

## Working notes for Claude with Chrome tools (not needed for ChatGPT)
- AliExpress search-result JSON prices are in AUD (`salePrice.minPrice`, currencyCode AUD); the DSers box on item pages shows "product cost: US$..." and "via <method>: US$..." in USD. Give item pages 10-14 seconds to load the DSers box.
- Search pages sorted by orders: `aliexpress.com/w/wholesale-<words>.html?sortType=total_tranpro_desc`. Parse items by splitting the HTML on `"itemType":"productV3"` and reading productId, displayTitle, salePrice.minPrice, tradeDesc and imgUrl.
- Pace AliExpress fetches about 2.5 seconds apart. Many rapid fetches trigger a slider CAPTCHA ("punish" page): stop, never solve it, ask the owner.
- Long loops can freeze the tab for the 45-second tool limit: start them without awaiting, store results on `window`, then poll.
- Bulk Amazon matching: open Amazon AU from the AliExpress tab with a clicked `window.open` button so the two tabs can exchange data with `postMessage`; the Amazon tab fetches `/s?k=<title words>` for each item. Then render AliExpress and Amazon thumbnails side by side to compare by eye.
- Amazon AU: read `[data-component-type=s-search-result]` titles and `.a-price .a-offscreen`; `/dp/<ASIN>` gives title, price, feature bullets and "package includes".
- Kogan's own search doesn't render for the tools; use a web search restricted to kogan.com. eBay AU blocks automated checks after heavy use; don't try to get around it.
- Store stats: a page with "aggregate consumer reviews" text and no "Positive Feedback | Followers" line is a pooled Choice listing.
