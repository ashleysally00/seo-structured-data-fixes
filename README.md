# Website SEO & Schema Debugging

This repo documents my process of fixing **SEO** and **structured data** issues on my Squarespace site. I'm using **SEMrush** and **Google's Rich Results Test** to identify problems, apply fixes, and track improvements.

## Table of Contents
- [Next Actions Checklist](#next-actions-checklist) ✅
- [Notes to Self / Next Steps](#notes-to-self--next-steps) 😎☀️
- [SEMrush Integration](#semrush-integration)
- [Fix: Redirects](#fix-redirects)
- [Fixing Duplicate Title Tags](#fixing-duplicate-title-tags)
- [Fixing Meta Descriptions & Removing Blog SEO](#fixing-meta-descriptions--removing-blog-seo)
- [Verifying Domain in Google Search Console](#verifying-domain-in-google-search-console)
- [SEO Structured Data Fixes (In Progress)](#seo-structured-data-fixes-in-progress)
- [Snapshot References](#snapshot-references)
- [Store / Commerce Pages and Schema](#store--commerce-pages-and-schema)
- [Lessons Learned](#lessons-learned)

## SEMrush Integration

The SEMrush report highlighted:
* **Broken links**: Many from old Pinterest pins pointing to pages I deleted when restructuring my site.
* **Visibility**: 0% — the site is being rebuilt for search ranking.
* **Backlinks**: 285 currently, though some point to broken pages.

## Fix: Redirects

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

## Fixing Duplicate Title Tags

Next, I decided to address the duplicate title tags. Duplicate titles happen when more than one page on your site has the exact same SEO title. This confuses search engines because they can't tell which page should rank for a keyword, and it can hurt your overall SEO visibility.

In my case, SEMrush flagged **12 issues with duplicate title tags.** All of them were using the same default title:

```
Blog — Ashley Rice books and greeting cards
```

This included even some old pages that I had hidden but never deleted. Since I recently shortened and simplified my site, a quick fix was to delete those unused pages entirely.

For the remaining active pages, I updated their titles in Squarespace under **Page Settings → SEO** so that each one was unique and descriptive.

**Examples of changes I made:**
* Old: `Blog — Ashley Rice books and greeting cards`
* New (Books page): `Ashley Rice Books – Poems, Quotes & Girl Power`
* New (Work & Projects page): `Work & Projects – Books, E-Cards & Educational Games | Ashley Rice`

Now, each page has a clear, keyword-friendly title that better reflects its content and avoids duplication.

## Fixing Meta Descriptions & Removing Blog SEO

After cleaning up duplicate title tags, I found that my meta descriptions were doubling in length.  
Squarespace was stacking the Blog Collection description on top of my page-level SEO description, which pushed some pages to 240+ characters and triggered SEMrush warnings.

### How I Fixed It
1. **Identify page type**  
   - Go to **Pages** in the left sidebar.  
   - Hover over a page:  
     - If it has nested posts/items → it's a **collection (Blog, Store, Products)**.  
     - If it's just a plain page icon → it's a **regular page**.  

2. **Delete unused Blog collections**  
   - My site still had a leftover "Blog" template (empty but active).  
   - Squarespace was pulling its SEO description into every page.  
   - Fix: hover over **Blog → trash can icon → Delete**.  

3. **Clean up SEO Title Format**  
   - In **SEO → Search Appearance**, my format was still set to:  
     ```
     Blog — %s
     ```  
   - I replaced it with:  
     ```
     %s | Ashley Rice
     ```  
   - Now every page shows its own title without the "Blog—" prefix.  

4. **Add unique, short SEO descriptions**  
   - Each page gets one concise summary (150–160 characters).  
   - I double-check length with an external [character counter](https://charcounter.com), since Squarespace's built-in counter often overestimates.  

### Examples I Added
- **Books:**  
  `Books by Ashley Rice for girls and tweens, with poems, quotes, and art that share encouragement, love, friendship, and confidence.` (141 chars)  

- **About:**  
  `Ashley Rice is the author and illustrator of inspiring books for girls and tweens about girl power, creativity, and confidence.` (132 chars)  

- **Wholesale:**  
  `Order Ashley Rice's books, greeting cards, calendars, and notepads wholesale, all with girl-power themes of love, encouragement, and confidence.` (158 chars)  

- **Contact:**  
  `Contact Ashley Rice for wholesale orders, media or speaking requests, or to connect directly with the author.` (147 chars)  

### Lessons Learned
- Squarespace blog templates auto-stack SEO text if not deleted.  
- "Blog—" in title previews comes from site-wide title format settings.  
- The built-in character counter is unreliable — always confirm externally.  
- One page = one clean, unique description under 160 characters.

## Verifying Domain in Google Search Console

After addressing duplicate title tags, I moved on to verifying my site with **Google Search Console**.

The reason I did this is because Google Search Console gives you direct data from Google about how your site is performing in search. It shows which pages are indexed, what keywords you're ranking for, and any errors that could limit visibility. Having this data is essential for tracking whether my SEO changes are making a difference.

**How I verified my site (DNS method):**
1. In Google Search Console, I chose the option to verify my domain using a **DNS TXT record**.
2. Google provided me with a unique verification code that looks like this:

```
google-site-verification=xxxxxxxxxxxxxxxxxxxxxxxx
```

3. I went into Squarespace → **Settings → Domains → DNS Settings**.
4. Under **Custom Records**, I added a new **TXT record** with:
   * Host: `@`
   * Type: `TXT`
   * Data: the Google verification code.
5. Saved the changes.
6. Returned to Google Search Console and clicked **Verify**.

⚠️ **Important:** DNS changes do not update instantly. It can take several hours (sometimes up to 24–48 hours) for the TXT record to propagate across the internet. That means even if you add the record correctly, Google may still say "Verification failed" at first. The fix is simply to **wait and click Verify again later**.

After the TXT record is verified, I will see that my domain is connected in Search Console. Then I'll be able to track performance data, keywords, and any future SEO issues directly from Google.

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

⚠️ **Note:** This change has not been applied yet. The LocalBusiness schema is still active and continues to trigger errors. This section remains open until it's resolved.

## Snapshot References

This repo includes screenshots of test outcomes for documentation:
- `rich-test-results.png` – error message example
- `local-business.png` – failed LocalBusiness validation
- `semrush-broken-links.png` – SEMrush report

## Store / Commerce Pages and Schema

At one point I experimented with selling animations directly through Squarespace's built-in commerce features. Even after deleting those store pages, Squarespace left behind LocalBusiness schema in the template.

That legacy schema is what triggered the Rich Results errors above. Since I no longer sell directly through my site (all book sales go to Amazon and Barnes & Noble), the fix is to:
1. Remove the leftover LocalBusiness schema, and
2. Keep only schema relevant to my site, such as WebSite.

## Next Actions Checklist
- [x] ~~Fix broken Pinterest backlinks (301 redirect or remove)~~
- [ ] Remove LocalBusiness schema from Squarespace template
- [ ] Add WebSite schema only
- [ ] Re-run Google Rich Results Test after changes
- [ ] Monitor SEMrush for visibility and keyword improvements

## Lessons Learned

1. **Redirects matter**: Old backlinks from Pinterest and other sites can still drive traffic. Redirecting them preserves value instead of losing it to 403/404 errors.

2. **Structured data lingers**: Even if you delete pages in Squarespace, injected schema (like LocalBusiness) may remain in the template and cause validation errors.

3. **Schema should match reality**: Since I no longer sell directly through my site, LocalBusiness is incorrect. WebSite schema is the right fit.

4. **Tools help uncover hidden issues**: SEMrush and Google's Rich Results Test revealed problems I couldn't see just by browsing the site.

5. **SEO is iterative**: Each fix leads to the next test. Visibility builds through steady corrections, not one-time changes.

## Notes to Self / Next Steps ✨

- Start with writing unique meta descriptions for Home, Books, About, Contact, Wholesale
- After Search Console verifies domain, check Index Coverage to confirm all 5 main pages are indexed
- Use Rich Results Test again to confirm schema cleanup (WebSite vs. LocalBusiness)
- Consider adding 150–300 words of intro text to Books and About pages for SEO
- Re-run SEMrush once quota resets to confirm errors are resolved
