# Qualicart handoff notes (updated 2026-11-10)

## Store
- Shopify: qualicartshop.myshopify.com, domain qualicartshop.com, currency AUD, ships to Australia and New Zealand.
- Products come from AliExpress via DSers (orders are placed manually). DSers is used on the MacBook.

## Themes
- LIVE since 2026-11-10: "Qualicart - working copy" (gid://shopify/OnlineStoreTheme/196095181094), published from the admin after design round 2. The connector can't write to the live theme.
- Previous live theme "Tinker - Qualicart edit" (gid://shopify/OnlineStoreTheme/196078305574) is now an unpublished draft (fallback; can be deleted later).
- For the next design round: duplicate the live theme, work on the duplicate, publish it.
- Routine: do design/code work on the working copy, preview, then publish it; duplicate the live theme again for the next round. Don't edit the live theme in the Customizer while a copy is being worked on (publishing the copy would overwrite those edits).
- The original "Tinker" theme (194745827622) was deleted on 2026-11-09 at the owner's request.
- Theme files live in Shopify, not in this repo. Sections below marked "on the copy" are now live.
- Later 2026-11-09 work (now live): homepage products section (sections/qc-home-products.liquid: 24 products, 6 per row, sort bar, View all); Collections page rows (sections/qc-collection-row.liquid: title + View all, sort bar + in-row search); policy pages (sections/qc-policy.liquid, templates/page.policy.json, no banner; layout/theme.liquid renders it for /policies/refund|privacy|terms|shipping URLs too); inner-page banners standardised (qc-page-hero: 320px desktop / 200px phone, image 2880x640, overlay None/Light/Dark setting); header country picker moved to the far right (header-group custom CSS); search icon only; product page "check before you buy" note (blocks/qc-buy-note.liquid) and real feature tiles.

## Design round 2 (2026-11-09/10, Mac) - LIVE since 2026-11-10
- snippets/qc-global-styles.liquid (rendered in layout/theme.liquid head) holds the site-wide overrides:
  - all H1 bold, page titles bigger
  - About subtitle max 560px
  - policy "On this page": no long line, marker on the panel's left edge; content full width with 20px padding
  - reviews full width with 20px padding; accordion dividers off
  - footer links orange on hover; orange Add to cart; 80px space after the last Collections row
  - cart drawer floats 10px from top/right/bottom with orange pill buttons and a grey delete button
  - search popup up to 1200px wide, 10 products in 5 columns
- About intro: "Hi, we're Qualicart Shop."
- Footer bottom bar:
  - left: "(c) 2026 Qualicart Shop" + Terms and Policies
  - right: "Powered by The PixelSeed Studio", linked to thepixelseed.com (blocks/qc-footer-credit.liquid)
  - the copyright block has a new "Store name" setting
- Product page: new 2x2 trust tiles (blocks/qc-trust-tiles.liquid, text editable in the editor) replace the old four-tile group.
- Promo banners: sections/qc-promo-banners.liquid, two banners at 160px tall (image 1420x320).
  - At the top of the Products page (templates/collection.json, so also on every individual collection page) and the Collections page (templates/list-collections.json).
  - Hidden until an image is added; dashed placeholders show in the editor. Optional link per banner.
- Sale collection (live, handle "sale", gid://shopify/Collection/684402016550):
  - Smart rule: Sale % equals 1 OR greater than 1. Sale % allows 1-70, so Shopify rejects "greater than 0".
  - Published to Online Store and POS. Link a promo banner to it.
  - Sale % definition now has "smart collection condition" enabled.
- Later round-2 changes (also live):
  - Inner-page banner (qc-page-hero): on phones the H1 and subtext sit above the image; image is a 200px card. Single image only (mobile-image setting removed).
  - Reviews box 40px side padding (24px on phones).
  - Shipping page cards redesigned (sections/qc-shipping-table.liquid): flag, country, Free shipping pill, icon rows, no divider lines.
  - About page highlight boxes: orange icon on the left, value and label beside it.
  - Homepage products: search box in the sort bar. It uses Shopify store-wide search via sections/qc-home-search.liquid (up to 48 results); cards come from snippets/qc-home-card.liquid.
  - Homepage collection cards: titles bold, 20px lower, split before "and" (blocks/collection-title.liquid, homepage only).
  - Hidden "Qualicart" H1 removed from sections/header.liquid (homepage has one H1).
- SEO (2026-11-10):
  - snippets/qc-structured-data.liquid (rendered in layout head): WebSite + OnlineStore on home, Product/ProductGroup with AU/NZ shipping and return policy, breadcrumbs, FAQPage. Shopify's built-in product JSON-LD removed from sections/product-information.liquid.
  - snippets/meta-tags.liquid: description fallbacks, logo as share image, /policies/ pages canonical to /pages/ copies.
  - Store data: SEO titles/descriptions on pages, collections, 4 products, homepage (Online Store > Preferences). /pages/products hidden from search (seo.hidden).
  - All 41 products have a Shopify standard category.
- Google & YouTube channel installed 2026-11-10; Merchant Center "Qualicart" created and linked (qualicartonlineshop@gmail.com); 40 live products published to the channel. Free listings only, no Google Ads account. Check approvals in a few days.
- Shopify gotcha: when a schema setting and its value are uploaded together (e.g. a new block setting plus the group JSON using it), the value is dropped. Upload the JSON again afterwards.

## Done on the copy
- Footer: Shop/Help/About menus (footer-shop, footer-help, footer-about), "We accept" payment icons (Visa, Mastercard, Amex, PayPal, Apple Pay, Afterpay - fixed list in blocks/payment-icons.liquid), "Powered by Shopify" off.
- Header menu: "qc-main-menu" = Collections, Products, About, Shipping, FAQ, Contact (live store still uses main-menu).
- /collections: one product-list section per collection (12 products, 6 per row, "View all" button 36px pill, clickable titles).
- Collection pages: custom section sections/qc-collection-page.liquid (sidebar categories + filters, sort bar, 5-col grid, accent #FFB37D).
- Pages: FAQ (templates/page.faq.json, accordion, one open at a time), Contact (templates/page.contact.json, custom dropdown subject), Shipping (templates/page.shipping.json).
- Shared: sections/qc-page-hero.liquid, sections/qc-faq.liquid (reads Heading 2 questions from the page body).
- About page (2026-11-09): templates/page.about.json = qc-page-hero banner + sections/qc-about.liquid (intro + highlight cards or optional image, 4 value cards, AU/NZ flag cards, CTA). About page's template set to "about". Banner image can be added in the editor (QC page hero > Background image).
- AU/NZ "Ships to" flags (2026-11-09): product metafield qualicart.ships_to (list, choices AU/NZ, pinned in product admin; empty = both). snippets/qc-ship-to.liquid renders flags; blocks/qc-ship-to.liquid added under price in templates/product.json; compact flags on cards in qc-collection-page. Checkout is enforced by shipping profiles: "AU only" (AU zone, free 6–12 days; has the double burner stove) and "NZ only" (NZ zone, free 6–15 days; empty). Automated (2026-11-09): Shopify Flow workflow "New Workflow" (trigger: Product updated, field qualicart.ships_to) runs Send Admin API request deliveryProfileUpdate and moves all the product's variants to: AU only -> "AU only" profile, NZ only -> "NZ only" profile, both/empty -> General profile. So only the Ships to field needs setting. Tested on the stove (both -> General, AU -> AU only). Note: variants added later aren't moved until Ships to is saved again.

## Done on the copy (2026-11-09, later session)
- "View all" buttons and collection titles on /collections: hover turns #FFB37D (blocks/_product-list-button.liquid, blocks/_product-list-text.liquid).
- Product page (templates/product.json): price in #ff6600 at 1.5rem; "Shop The Full Collection" is now 12 products (2 rows of 6) with the same white/bordered cards as /collections plus a "View all" button; Judge.me star rating under the title; new section sections/qc-reviews.liquid (light gray #f4f4f4 rounded container with the Judge.me Review Widget, above the related products).
- Judge.me Reviews installed on the store (free plan to be chosen in its onboarding). App embed enabled and saved on the COPY theme only; the onboarding page checks the live theme and will say "couldn't detect" until the copy is published. Judge.me green overridden to orange (#ff6600) and "Write a review" button made pill-shaped in qc-reviews.liquid.
- snippets/price.liquid: sale price (orange) + gray strikethrough compare-at + "-NN%" tag when compare-at > price; ships-to AU/NZ flags (compact) under the price on every product card except the main product price.
- Products page (sections/qc-collection-page.liquid): price now #ff6600, regular weight (matches homepage).
- Published to the Online Store (store-wide, so LIVE too): 23 Active products that were unpublished (cots, sleeping bags, backpacks, vests, storage bags, markers, etc.). The Draft "Lightweight Blue Nylon Running Vest" stays hidden.

## Sales (2026-11-09, Mac session)
- Theme copy: SALE badge shows automatically when compare-at > price. Orange (#ff6600) built-in card badge (snippets/product-badges-styles.liquid); SALE badge + "-NN%" on QC Products page cards (sections/qc-collection-page.liquid); product page shows a SALE pill, crossed-out price, "-NN%" and "You save A$X" (snippets/price.liquid, main product only).
- Product field "Sale %" (qualicart.sale_percent, whole number 1–70, pinned; definition gid://shopify/MetafieldDefinition/590593229094).
- Shopify Flow workflow "Sale % sets sale price" (ON): trigger Product updated on qualicart.sale_percent; action productVariantsBulkUpdate. Fill Sale % -> compare-at = normal price, price = normal price minus %. Change % -> recalculates from the normal price (no stacking). Clear Sale % -> price back to normal, compare-at removed. Tested on the unpublished blue nylon vest (86.95 -> 73.91 at 15%, 69.56 at 20%, back to 86.95).
- Bulk: Products > select products > Bulk edit > add the "Sale %" column > fill/clear it.
- Keep sales genuine (ACCC / NZ Fair Trading Act): only discount from the real current price, and keep sales time-limited. Do NOT raise compare-at above a price never charged.
- DSers: pricing rule None; Automatic Price Update = Do Nothing (locked on current plan), so sale prices are not overwritten. DSers only writes supplier cost into compare-at when pushing a new product (harmless: lower than price, no badge; cleared when a sale ends).
- Sale prices are rounded to the cent (e.g. 73.91), not to .95 endings.

## Policies (2026-11-09, Mac session)
- Refund policy rewritten and saved (Settings > Policies, "Use automated policy" OFF so Shopify won't overwrite it): no change-of-mind returns; faulty/damaged/wrong/not-as-described items covered under ACL and NZ CGA; report by email with photos; we pay return postage when a return is needed; cancel before dispatch for a full refund. Draft source: policies/refund-policy-draft.md.
- Return rules (Settings > Policies > Default rules) turned OFF (was 30-day returns, free return shipping), so customers can't self-serve change-of-mind returns. Cancellation rules were already off.
- Footer menus (copy theme only) now link to /policies/refund-policy, /policies/privacy-policy, /policies/terms-of-service. The empty pages /pages/returns-and-refunds, /pages/privacy-policy, /pages/terms-of-service are no longer linked and can be deleted.
- Still to do: Contact information policy (draft in policies/contact-information-draft.md, needs ABN/NZBN, business name, address or remove those lines). Privacy, Terms and Shipping policies are Shopify's automated templates (fine for now).
- Products page (copy theme): sidebar redesigned (category rows with counts, chip filters, A$ price inputs, Under $50 / $50-$100 / $100+ quick chips, pill Apply/Clear all), sort bar 20px corners with pill buttons, 30 products per page. Login icon kept.

## Open items from this session
- Compare-at prices on the products are LOWER than the selling price (DSers cost), so no sale tags show. Decide a real "was" price rule (ACCC: must be a genuine previous price) or leave blank.
- Optional: show "from $X - $Y" price ranges on cards for multi-variant products.
- Optional: Judge.me star ratings on product cards; lengthen Judge.me review-request delay for slow AliExpress delivery.
- Chrome: the Chrome signed in as qualicartonlineshop@gmail.com (Zarene Esguerra) is the one that works for Shopify admin work. A leftover live-theme editor tab may have an unsaved Judge.me toggle: close it without saving.

## Collections (handles)
home-and-living, outdoor-and-camping, kitchen-and-dining, toys-and-games, arts-and-crafts (old handles redirect).

## Before publishing the copy
1. Homepage collection list (templates/index.json, collection_list_xpBxCm) still references OLD handles (collection1, collection-2, ...) and shows max 4 of 5 collections. Update to the new handles and raise max to 5.
2. DONE 2026-11-09: Shipping table filled (templates/page.shipping.json): dispatch within 2 business days; AU 6–12, NZ 6–15 business days after dispatch; free.
3. DONE 2026-11-09: Shipping rates. International zone (28 countries, 1,200 PHP) deleted. New zones in General profile: "Australia" = "Free Standard Shipping (6–12 business days)" A$0; "New Zealand" = "Free Standard Shipping (6–15 business days)" A$0. Domestic PH zone left unchanged.
4. Reword or make true: "Delivery times shown before you pay" (announcement bar, FAQ, About, hero). Now true at checkout (range is in the rate name); still check the wording.
5. Enable payment methods that the footer icons show (Settings > Payments), including PayPal and Afterpay.
6. Returns, Privacy, Terms pages are still empty.
7. Contact page: no file upload (Shopify contact form can't); damaged-item note tells customers to reply with photos.

## DSers delivery estimates (checked 2026-11-09, default SKU, ship from CN)
Most products: AliExpress Selection Standard, AU 6–11/7–12 days, NZ 6–13/10–15 days, about US$1.99 per order.
Rechecked with longer load waits (first pass misread slow loads as "No Shipping"):
- Truck blocks (AU 7–12), coffee grinder (AU 6–11), ivory fan (AU 6–11), white fan "White" SKU (AU 6–11, NZ 6–13): all ship. DSers opens the white fan on the "Green" SKU; check its mapping.
- Double burner stove: only one SKU, no NZ shipping (AU 6–12 free). Keep as Draft or sell AU-only.
- Titanium cookware set: Shopify listing is mapped to T-Ta8328BN-1, which ships to AU (6–11) and NZ (8–12), so AU + NZ is correct. T-Ta8326BN-1/-2 and T-Ta8327BN-2 show no shipping to either country (likely out of stock); T-Ta8328BN-2 is AU only.

## DSers recheck of the 24 products published 2026-11-09 (Windows session + titanium set)
All ship to both AU and NZ; Ships to stays AU + NZ, no changes made. Checked per variant:
- Running vests: grey/red (UTOBEST, AU 7–14, NZ 8–13); black S/M/L/XL (WRELS, AU 6–12, NZ 8–12).
- Hiking backpacks red 3L, dark blue 2L, green 1.5L (AU 7–14, NZ 8–13).
- Sleeping bags green 190x75 (mapped SKU, confirmed) and brown 205x85; fleece liners black and coffee; cots black and army green.
- Alcohol markers 122/180 pcs; storage bags 30L/42L black and green (AU 6–10, NZ 7–11).
- Double burner stove rechecked: NZ still "No Shipping" (AU uses "Special Goods" shipping), so it stays AU only.
How to read DSers reliably: the first reading after changing SKU is often a false "No Shipping". Switch country away and back, wait 15+ seconds, and only trust "No Shipping" if it repeats. To see which supplier SKU a Shopify product uses: hover the card > Mapping icon (read only; close and choose DISCARD, never Save).

## Other open items
- Zoho email (zarene@qualicartshop.com): plan choice and DNS (MX, SPF, DKIM) pending.
- Hero images/slides: decide what to change; slides are baked-in images.
- Set DSers push status to Draft.

No secrets (API keys, passwords) belong in this repo.
