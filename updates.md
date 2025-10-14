# Ongoing Updates (as of Oct 14, 2025)

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

