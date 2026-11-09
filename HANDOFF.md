# Qualicart handoff notes (updated 2026-11-09)

## Store
- Shopify: qualicartshop.myshopify.com, domain qualicartshop.com, currency AUD, ships to Australia and New Zealand.
- Products come from AliExpress via DSers (orders are placed manually). DSers is used on the MacBook.

## Themes
- Live theme: "Tinker" (gid://shopify/OnlineStoreTheme/194745827622). Do not edit directly (connector blocks writes to the live theme).
- Working copy: "Tinker - Qualicart edit" (gid://shopify/OnlineStoreTheme/196078305574), UNPUBLISHED.
  Preview: https://qualicartshop.com/?preview_theme_id=196078305574
- All design work so far is on the copy only. Theme files live in Shopify, not in this repo.

## Done on the copy
- Footer: Shop/Help/About menus (footer-shop, footer-help, footer-about), "We accept" payment icons (Visa, Mastercard, Amex, PayPal, Apple Pay, Afterpay - fixed list in blocks/payment-icons.liquid), "Powered by Shopify" off.
- Header menu: "qc-main-menu" = Collections, Products, About, Shipping, FAQ, Contact (live store still uses main-menu).
- /collections: one product-list section per collection (12 products, 6 per row, "View all" button 36px pill, clickable titles).
- Collection pages: custom section sections/qc-collection-page.liquid (sidebar categories + filters, sort bar, 5-col grid, accent #FFB37D).
- Pages: FAQ (templates/page.faq.json, accordion, one open at a time), Contact (templates/page.contact.json, custom dropdown subject), Shipping (templates/page.shipping.json).
- Shared: sections/qc-page-hero.liquid, sections/qc-faq.liquid (reads Heading 2 questions from the page body).

## Done on the copy (2026-11-09, later session)
- "View all" buttons and collection titles on /collections: hover turns #FFB37D (blocks/_product-list-button.liquid, blocks/_product-list-text.liquid).
- Product page (templates/product.json): price in #ff6600 at 1.5rem; "Shop The Full Collection" is now 12 products (2 rows of 6) with the same white/bordered cards as /collections plus a "View all" button; Judge.me star rating under the title; new section sections/qc-reviews.liquid (light gray #f4f4f4 rounded container with the Judge.me Review Widget, above the related products).
- Judge.me Reviews installed on the store (free plan to be chosen in its onboarding). App embed enabled and saved on the COPY theme only; the onboarding page checks the live theme and will say "couldn't detect" until the copy is published. Judge.me green overridden to orange (#ff6600) and "Write a review" button made pill-shaped in qc-reviews.liquid.
- snippets/price.liquid: sale price (orange) + gray strikethrough compare-at + "-NN%" tag when compare-at > price; ships-to AU/NZ flags (compact) under the price on every product card except the main product price.
- Products page (sections/qc-collection-page.liquid): price now #ff6600, regular weight (matches homepage).
- Published to the Online Store (store-wide, so LIVE too): 23 Active products that were unpublished (cots, sleeping bags, backpacks, vests, storage bags, markers, etc.). The Draft "Lightweight Blue Nylon Running Vest" stays hidden.

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
"No Shipping" for the default SKU (needs another SKU or supplier before selling there):
- 1:8 Truck Building Blocks (LIVE): no AU shipping
- Coffee grinder, Ivory foldable fan: no AU shipping
- Double burner stove: no NZ shipping
- White bladeless fan, Titanium cookware set: no AU or NZ shipping

## Other open items
- Zoho email (zarene@qualicartshop.com): plan choice and DNS (MX, SPF, DKIM) pending.
- Hero images/slides: decide what to change; slides are baked-in images.
- Set DSers push status to Draft.

No secrets (API keys, passwords) belong in this repo.
