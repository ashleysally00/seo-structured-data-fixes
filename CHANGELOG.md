# Ongoing Updates (as of Oct 14, 2025)

> Summary of updates, fixes, and improvements made to the SEO & Schema project.

This file acts as a **changelog** for small, ongoing improvements and SEO/debugging fixes made after the main documentation was completed.

It's meant for quick notes — not full write-ups — so each entry only includes:
- **Date**
- **What changed**
- **Why it was done**
- **Result (if known)**

This keeps the main README organized while still tracking all progress over time.

---

## 2025-10-14 — Fix: Duplicate Title Tags (Squarespace)

**Why**  
SEMrush reported **19 duplicate title tags** on book subpages (e.g., `/for-an-incredible-kid`, `/girls-rule`, etc.).

**Root cause**  
Squarespace's global page-title format for all pages was overriding per-page SEO titles, so many pages rendered the same `<title>` in HTML.

**What we changed (1 setting)**  
Squarespace → **Settings → SEO / AIO → Search appearance → _Pages_**  
In **SEO title format**, replaced the global text with:
```
%p
```
`%p` = use each page's own SEO/Page Title (no global phrase appended).

**Result**  
Each subpage now outputs a unique `<title>` (e.g., _For an Incredible Kid – … by Ashley Rice_), resolving SEMrush's duplicate-title warnings and improving search clarity.

**Verify**  
- View source of a subpage and confirm `<title>` shows the page-specific title.
- Rerun SEMrush Site Audit → Issues → Duplicate title tags should drop.

**Related checks**  
- The "Items" tab in Search appearance (`%i — %s`) did not require changes.
- Per-page SEO titles/descriptions in **Page Settings → SEO** were already customized.

 ### Why Fixing Duplicate Title Tags Matters

Fixing the **19 duplicate title tags** flagged by SEMrush is more than just housekeeping — it’s a foundational SEO improvement that strengthens your site’s visibility and ranking potential.

#### Why Duplicate Title Tags Are a Problem

Think of a title tag as the title of a chapter in a book.  
If 19 chapters all have the same title, it’s confusing for both readers and search engines.  
This causes several issues:

- **Keyword Cannibalization:**  
  When multiple pages share the same title, search engines don’t know which one to prioritize.  
  As a result, all those pages may rank lower because their relevance is diluted.

- **Diluted Link Equity:**  
  When other websites link to your pages, that SEO “credit” (link equity) gets spread thin across duplicates.  
  Unique titles allow all that value to focus on one authoritative page.

- **Lower Click-Through Rate (CTR):**  
  Distinct, descriptive titles are more appealing in search results.  
  Duplicate or generic ones look repetitive and discourage clicks — which can signal to Google that your page is less relevant.

#### What This Fix Improves

- **Improved User Experience:**  
  Visitors now see clear, descriptive titles that help them find exactly what they’re looking for.

- **Better Ranking Potential:**  
  By giving each page a unique title, your site sends stronger relevance signals to Google, consolidates link authority, and improves overall keyword performance.

Even though this type of fix doesn’t skyrocket rankings overnight, it’s one of the most important long-term SEO foundations for building authority and clarity across your site.

