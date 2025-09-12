# Website SEO & Schema Debugging

This repo documents my process of fixing **SEO** and **structured data** issues on my Squarespace site. I'm using **SEMrush** and **Google's Rich Results Test** to identify problems, apply fixes, and track improvements.

## 📚 Books Quiz  
Find which Penelope book fits you best — take the fun quiz!  
[Take the quiz!](https://ashleysally00.github.io/seo-structured-data-fixes/books_quiz.html)


## Table of Contents
- [Next Actions Checklist](#next-actions-checklist) ✅
- [Notes to Self / Next Steps](#notes-to-self--next-steps) 😎☀
- [SEMrush Integration](#semrush-integration)
- [Fix: Redirects](#fix-redirects)
- [Fixing Duplicate Title Tags](#fixing-duplicate-title-tags)
- [Fixing Meta Descriptions & Removing Blog SEO](#fixing-meta-descriptions--removing-blog-seo)
- [Addressing Low Word Count (On-Page SEO)](#addressing-low-word-count-on-page-seo)
- [Verifying Domain in Google Search Console](#verifying-domain-in-google-search-console)
- [SEO Structured Data Fixes (In Progress)](#seo-structured-data-fixes-in-progress)
- [Snapshot References](#snapshot-references)
- [Books Page Redesign (Squarespace 7.1)](#books-page-redesign-squarespace-71) 📖
- [Books Quiz](#books-quiz) ✨📚
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

## 📚Books Page Redesign (Squarespace 7.1)

The original Books section was hard to get the covers the same size and to line up at the same time due to Squarespace limitations. The old layout snapped image blocks to the grid with inconsistent padding, so covers never matched size reliably. We got around this by making the books into a **gallery** with a fixed 2:3 aspect ratio so all covers align cleanly.

### Why this was difficult

Squarespace galleries don't allow adding text blocks underneath each image.  

If we had simply switched to a gallery without a workaround, we would have lost both:
- **Technical SEO progress** → the unique H1 setup and heading hierarchy I had already fixed (no duplicates, one clear H1 per page).  
- **On-Page SEO signals** → meaningful content like H2 book titles, H3 bylines, and keyword-rich summaries that Google needs to understand the page.  

### Workaround: Markdown/HTML inside captions

To preserve both visual consistency *and* SEO:
- We added **Markdown/HTML directly in the gallery description fields**:
  - `<h2>` for the book title.  
  - `<h3>` for the byline ("Written and illustrated by Ashley Rice").  
  - `<span>` for the description (treated as paragraph text).  
- This ensured the Books page kept a crawlable heading structure, instead of collapsing into just images with single-line captions.  

**Example caption HTML:**
```html
<h2>Girls Rule</h2>
<h3>Written and illustrated by Ashley Rice</h3>
<span>Girls Rule is filled with cute poems, quotes, and drawings that apply to everyday life. Perfect for tweens who love inspiring words, creativity, and art.</span>
```

### Implementation steps

1. Built the new gallery section with consistent covers and structured captions.
2. Hit the heart (favorite) to save it to the Library.
3. Went to the Books page → Add Section → My Library → inserted the saved gallery.
4. Deleted the messy old Books section with uneven image blocks.
5. Saved changes — leaving us with a clean, SEO-friendly gallery section.

### Why this matters

- Solves the alignment/padding issues of the old Books section.
- Retains all previous technical SEO fixes (unique H1, no duplicate titles).
- Adds proper on-page SEO content (H2 titles, H3 bylines, keyword-rich summaries).
- Improves both visual authority and search authority at the same time.


## Addressing Low Word Count (On-Page SEO)

The next issue flagged by SEMrush was a **“low word count” warning.**  
This showed up because the Books page only had about ~40 words of text.  

This wasn’t a technical SEO error — it was an **on-page content issue**.  
The page needed more written content so Google could understand what it was about and rank it properly.

**Error flagged by SEMrush:**  
- *“11 pages have a low word count (Warning)”*  
- The Books page (`/books`) was included.  


**Why this mattered:**  
- Google considers pages with very short text to be “thin content.”  
- Thin pages are less likely to rank because search engines can’t determine the topic or relevance.  

**Fix applied:**  
- Expanded the Books intro to ~150 words in Penelope’s voice.  
- Added natural keywords like *books for girls, poems, quotes, drawings, confidence, friendship*.  
- On mobile, reordered the page so the intro text appears above the illustration, ensuring Google and readers see meaningful content first.  

**Result:**  
- Books page now meets SEO best practice (150–300 words of intro text).  
- Still feels authentic to the brand and voice, while improving chances of ranking.  
- Other pages (About, Wholesale, Contact) are still flagged for low word count and will be addressed next.  

## On-Page SEO Decisions (About vs. Wholesale)

### Why prioritize the About page over Wholesale

- **Search intent:** The About page is where most new visitors land to understand who I am and what the site is about.  
- **SEO value:** Strengthening the About page supports E-E-A-T (experience, expertise, authoritativeness, trust).  
- **Audience:** Wholesale is important, but it's for a narrower group (buyers/partners). About reaches a broader audience and builds brand trust.  

### Keyword focus on About

- Added natural keywords: *books for girls*, *tweens*, *girl power*, *confidence*, *poems*, *quotes*, *illustrator*.  
- Expanded intro copy to 150–300 words, balancing authentic voice with keyword clarity.  

### Targeted H1 fix (About page only)

On the **About page** → **Page Settings** → **Advanced** → **Page Header Code Injection**:

```html
<style>
/* About page H1 override */
#block-yui_3_17_2_1_1757466580852_5138 h1 {
  font-size: 32px !important;   /* adjust to taste */
  line-height: 1.2em !important;
  margin-top: 0.5em !important;
  margin-bottom: 0.5em !important;
  font-weight: 500 !important;
}
</style>
```


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

## SEMrush Limits & Google Search Console Insights

SEMrush is free up to a certain point — you can run a site audit and a few keyword checks. After that, you have to either wait a month for the free credits to reset or upgrade to a paid plan.

Since I had already hit the free limit, I switched to **Google Search Console** for direct data from Google.

## What We Found

Looking at the Queries report for `ashleyrice.net` (last 3 months):

* **"ashley rice"** → 1,487 impressions, 18 clicks
* **"ashley rice books"** → 80 impressions, 5 clicks
* **"ashley rice, latest"** → 81 impressions, 0 clicks

Most visitors searching *"ashley rice books"* were still being sent to the **homepage** instead of the Books page.

## Action Taken

Because users clearly wanted the books but landed on the homepage first, I added a **prominent button + arrow at the top of the homepage**. The button links directly to the `/books` page, making it easy for visitors to jump straight into the collection.

This adjustment aligns the homepage with actual user intent:

* **Homepage = entry point**
* **Button = immediate path to books**

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

## Books Quiz

As part of improving on-page engagement, I built an interactive quiz:  
**“Which of Penelope’s Books Fits You Best?”**  

It’s a simple multiple-choice quiz that links readers to the book that matches their answers, providing both fun interaction and additional internal linking for SEO.  

👉 [Take the quiz!](https://ashleysally00.github.io/seo-structured-data-fixes/books_quiz.html)

## Store / Commerce Pages and Schema

At one point I experimented with selling animations directly through Squarespace's built-in commerce features. Even after deleting those store pages, Squarespace left behind LocalBusiness schema in the template.

That legacy schema is what triggered the Rich Results errors above. Since I no longer sell directly through my site (all book sales go to Amazon and Barnes & Noble), the fix is to:
1. Remove the leftover LocalBusiness schema, and
2. Keep only schema relevant to my site, such as WebSite.

## 🎉 Schema Validation Success

As of **September 8, 2025**, our structured data now passes Google’s Rich Results Test with **no critical issues detected**.  

This milestone was achieved by:
- Removing Squarespace’s auto-injected `LocalBusiness` schema (which required an address field).  
- Replacing it with a clean `Person` + `WebSite` schema tailored for an author/creator site.  

✅ Result: Google now recognizes valid schema with **0 errors**.

---

### 🔧 Footer Code Injection Used

The following code was added in **Squarespace → Settings → Advanced → Code Injection → Footer** to override and clean up schema:

```
html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Person",
  "name": "Ashley Rice",
  "url": "https://www.ashleyrice.net",
  "image": "https://static1.squarespace.com/.../AshleyRiceLogo.png"
}
</script>

<script>
(function () {
  function removeLocalBusiness() {
    document.querySelectorAll('script[type="application/ld+json"]').forEach(s => {
      try {
        const j = JSON.parse(s.textContent || '{}');
        const types = Array.isArray(j['@type']) ? j['@type'] : [j['@type']];
        if (types && types.map(String).map(x=>x.toLowerCase()).includes('localbusiness')) {
          s.remove();
        }
      } catch (_) {}
    });
  }
  if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', removeLocalBusiness);
  } else {
    removeLocalBusiness();
  }
  new MutationObserver(removeLocalBusiness).observe(document.documentElement, { childList: true, subtree: true });
})();
</script>
yaml
````

## Next Actions Checklist
- [x] ~~Fix broken Pinterest backlinks (301 redirect or remove)~~
- [x] ~~Remove LocalBusiness schema from Squarespace template~~
- [x] ~~Add WebSite schema only~~
- [x] ~~Re-run Google Rich Results Test after changes~~
- [ ] Monitor SEMrush for visibility and keyword improvements

## Lessons Learned

1. **Redirects matter**: Old backlinks from Pinterest and other sites can still drive traffic. Redirecting them preserves value instead of losing it to 403/404 errors.

2. **Structured data lingers**: Even if you delete pages in Squarespace, injected schema (like LocalBusiness) may remain in the template and cause validation errors.

3. **Schema should match reality**: Since I no longer sell directly through my site, LocalBusiness is incorrect. WebSite schema is the right fit.

4. **Tools help uncover hidden issues**: SEMrush and Google's Rich Results Test revealed problems I couldn't see just by browsing the site.

5. **SEO is iterative**: Each fix leads to the next test. Visibility builds through steady corrections, not one-time changes.

### Notes to Self / Next Steps✨
- ~~Fix broken Pinterest backlinks (301 redirect or remove)~~  
- ~~Start with writing unique meta descriptions for Home, Books, About, Contact, Wholesale~~  
- After Search Console verifies domain, check **Index Coverage** to confirm all 5 main pages are indexed  
- ~~Use **Rich Results Test** again to confirm schema cleanup (WebSite vs. LocalBusiness)~~  
- ~~Consider adding 150–300 words of intro text to Books and About pages for SEO~~  
- Re-run SEMrush once quota resets to confirm errors are resolved
- Fix the mobile view — check alignment of covers + captions in one-column layouts.
- Verify with SEMrush or Google crawler that H2/H3 headings inside captions are being read correctly.
- Look into: compressing book covers to lighter WebP/PNG for better performance (improves Core Web Vitals).


