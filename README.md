# Website SEO & Schema Debugging

This repo documents my process of fixing **SEO** and **structured data** issues on my Squarespace site. I'm using **SEMrush** and **Google's Rich Results Test** to identify problems, apply fixes, and track improvements.

## SEMrush Integration

The SEMrush report highlighted:

* **Broken links**: Many from old Pinterest pins pointing to pages I deleted when restructuring my site.
* **Visibility**: 0% — the site is being rebuilt for search ranking.
* **Backlinks**: 285 currently, though some point to broken pages.

### Fix: Redirects

I created **301 redirects** in Squarespace under **Developer Tools → URL Mappings** so old URLs now point to my live `/books` page.

```
/about -> /books 301
/any-day -> /books 301
/ashley-lynn-rice -> /books 301
/bio -> /books 301
/birthday-cards -> /books 301
/birthdaycards -> /books 301
/baby -> /books 301
```

This preserves traffic from Pinterest and passes SEO value from old backlinks.

## SEO Structured Data Fixes (In Progress)

### Rich Test Results Snapshot

Running Google's Rich Results Test flagged errors caused by Squarespace's **LocalBusiness schema**.

**Errors reported:**
* Missing field `"name"`
* Missing field `"telephone"` (optional)
* Missing field `"priceRange"` (optional)
* Missing field `"address"` (optional)

**Problem code (Squarespace injected):**

```json
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "",
  "address": "",
  "telephone": "",
  "priceRange": ""
}
```

### Next Step

Replace the incorrect LocalBusiness schema with WebSite schema:

```json
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "name": "Ashley Rice - Author & Illustrator",
  "url": "https://www.ashleyrice.net"
}
```

⚠️ **Note**: This change has not been applied yet. The LocalBusiness schema is still active and continues to trigger errors. This section remains open until it's resolved.

## Snapshot References

This repo includes screenshots of test outcomes for documentation:

* `rich-test-results.png` – error message example
* `local-business.png` – failed LocalBusiness validation
* `semrush-broken-links.png` – SEMrush report

## Store / Commerce Pages and Schema

At one point I experimented with selling animations directly through Squarespace's built-in commerce features. Even after deleting those store pages, Squarespace left behind **LocalBusiness schema** in the template.

That legacy schema is what triggered the Rich Results errors above. Since I no longer sell directly through my site (all book sales go to Amazon and Barnes & Noble), the fix is to:

* Remove the leftover LocalBusiness schema, and
* Keep only schema relevant to my site, such as **WebSite**.

## Next Actions Checklist

- [ ] Fix broken Pinterest backlinks (301 redirect or remove)
- [ ] Remove LocalBusiness schema from Squarespace template
- [ ] Add WebSite schema only
- [ ] Re-run Google Rich Results Test after changes
- [ ] Monitor SEMrush for visibility and keyword improvements

## Lessons Learned

* **Redirects matter**: Old backlinks from Pinterest and other sites can still drive traffic. Redirecting them preserves value instead of losing it to 403/404 errors.
* **Structured data lingers**: Even if you delete pages in Squarespace, injected schema (like LocalBusiness) may remain in the template and cause validation errors.
* **Schema should match reality**: Since I no longer sell directly through my site, LocalBusiness is incorrect. WebSite schema is the right fit.
* **Tools help uncover hidden issues**: SEMrush and Google's Rich Results Test revealed problems I couldn't see just by browsing the site.
* **SEO is iterative**: Each fix leads to the next test. Visibility builds through steady corrections, not one-time changes.
