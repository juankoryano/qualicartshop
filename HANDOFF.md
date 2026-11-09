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

## Collections (handles)
home-and-living, outdoor-and-camping, kitchen-and-dining, toys-and-games, arts-and-crafts (old handles redirect).

## Before publishing the copy
1. Homepage collection list (templates/index.json, collection_list_xpBxCm) still references OLD handles (collection1, collection-2, ...) and shows max 4 of 5 collections. Update to the new handles and raise max to 5.
2. Fill the Shipping table in the theme editor with real delivery ranges and cost (currently generic text).
3. Shipping rates: International rate is 1,200 PHP flat with no estimate. Split into Australia / New Zealand rates in AUD with the delivery range in the rate name.
4. Reword or make true: "Delivery times shown before you pay" (announcement bar, FAQ, About, hero).
5. Enable payment methods that the footer icons show (Settings > Payments), including PayPal and Afterpay.
6. Returns, Privacy, Terms pages are still empty.
7. Contact page: no file upload (Shopify contact form can't); damaged-item note tells customers to reply with photos.

## Other open items
- Zoho email (zarene@qualicartshop.com): plan choice and DNS (MX, SPF, DKIM) pending.
- Hero images/slides: decide what to change; slides are baked-in images.
- Set DSers push status to Draft.

No secrets (API keys, passwords) belong in this repo.
