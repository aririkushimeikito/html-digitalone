# Changelog — SEO & Schema Overhaul

Date: 2026-08-24

This pass brings every page up to a complete on-page SEO + structured-data standard,
fixes specific bugs, and rewrites copy where instructed. No visual design or CSS was changed.

---

## Files touched

### Pages (head standard + JSON-LD @graph + copy)
- `index.html` — new title/description/H1; @graph (Organization, WebSite, WebPage, Service, VideoObject);
  Service Area section added; testimonial placeholders added; Key-Benefit card links repointed;
  stats counters now render real numbers (95 / 88 / 90) in markup; "Who we are" rewritten.
- `services.html` — new title/description/H1; H2 → "Built for restaurants, bars and local businesses"; @graph.
- `review-management-services.html` — new title/description/H1; @graph + Service + FAQPage; Doylestown/Warrington added.
- `reputation-management.html` — repositioned as the platform/software page; @graph + Service + FAQPage + VideoObject.
- `local-listings.html` — GBP-focused rewrite; @graph + Service + FAQPage.
- `web-development.html` — breadcrumb "Services" link fixed → `/services.html`; `[TOWN], PA` placeholders in all 24 cards;
  `rel="noopener" target="_blank"` on all client links; @graph + Service + FAQPage + ItemList (24 sites).
- `video-production.html` — breadcrumb fixed; `preload="none"` + `playsinline` + poster on all videos;
  `[TOWN], PA` placeholders; WordPress video URLs repointed to `/videos/…` (see TODO below); @graph + VideoObjects.
- `social-media-management.html` — three body sections rewritten with concrete local examples; @graph + Service + FAQPage.
- `about.html` — new title/description; copy updated to three-region phrasing + Jamison home base; @graph (AboutPage).
- `blog.html` — all 11 "Read article" links repointed to `/blog/<slug>.html`; "Browse All Articles" → `/blog.html`;
  @graph (CollectionPage + Blog + blogPost list).
- `review-stand.html` — new title/H1; video gets `preload="none"` + poster; ReviewPro Cards sentence added;
  @graph + Product + VideoObject.
- `contact.html` — "nationwide" removed → standard service-area phrase; @graph (ContactPage + contactPoint).
- `privacy-policy.html` — `noindex, follow`; keywords removed; title fixed; `<!-- TODO: paste full legal text -->`.
- `tos.html` — `noindex, follow`; keywords removed; title fixed; `<!-- TODO: paste full legal text -->`.
- `thank-you.html` — set to `noindex, follow`; @graph; keywords removed.

### Site-wide
- Removed `<meta name="keywords">` from every page.
- Internal links converted to root-relative (`/about.html`, and `index.html` → `/`).
- Footer NAP rewritten as an `<address>` block: business name, Jamison PA 18929 (no street), phone, email, service-area phrase.
- Added GA4 snippet (placeholder `G-XXXXXXXXXX`) and Search Console tag (placeholder) to every indexable page.

### New files
- `blog/` — 11 static post shells (site header/footer, BlogPosting schema, breadcrumb, related-services box).
- `robots.txt` — Allow all, disallow `/thank-you.html`, sitemap reference.
- `sitemap.xml` — every indexable page + 11 blog posts, live domain, lastmod dates.
- `404.html` — site header/footer with links to Home, Services, Contact.
- `redirects.txt` — old WordPress URLs → new URLs (301) for Cloudflare Redirect Rules.

---

## Placeholders Joe still needs to fill in

1. **GA4 Measurement ID** — replace `G-XXXXXXXXXX` (every page) with the real GA4 ID.
2. **Search Console token** — replace `content="PLACEHOLDER"` in every `google-site-verification` tag.
3. **Town names** — replace `[TOWN], PA` in `web-development.html` (24) and `video-production.html` (12) client cards.
4. **Homepage testimonials** — fill `[CLIENT NAME]`, `[RESTAURANT]`, `[TOWN]`, `[QUOTE]` in the "Our Happy Clients" block.
5. **Blog article bodies** — each `/blog/<slug>.html` has `[ARTICLE BODY …]`; paste the text from WordPress.
6. **Optional founder** — if Joe supplies a last name + headshot, add the Person schema and the About-page founder block
   (see the SEO prompt). Until then, About copy stays "founded in 2017".
7. **Video files to download from WordPress before launch:**
   - `86 West` → save as `/videos/86-west-promo.mp4` (was `wp-content/uploads/2023/03/86West_StateStreetPOLISHED-With-Voice-Over.mp4`)
   - `Dog & Bull` → save as `/videos/dog-bull-promo.mp4` (was `wp-content/uploads/2024/08/Dog-Bull-VER2-1.mp4`)
8. **Video poster images** — the `<video poster="/images/posters/<slug>.jpg">` references and blog featured images
   assume image files exist; add/compress as needed.
9. **Review Stand demo video** — the page still points at the old external `media.orderchop.cloud` clip.
   Upload the replacement video to `/videos/` and update the `<source>` when ready.
10. **Full legal text** — paste the complete Privacy Policy and Terms of Service where marked
    `<!-- TODO: paste full legal text -->`, then flip both pages back to `index, follow`.
11. **Cloudflare redirects** — load `redirects.txt` into Cloudflare Redirect Rules (GitHub Pages can't do server-side 301s).
12. **Images over 200 KB** — compress before launch (e.g. `images/thumbnails/reeses-tavern.jpg` and any large hero/blog images).
