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
- [Anchor Links to Jump Directly to Books Section](#anchor-links-to-jump-directly-to-books-section)
- [Making Book Titles Clickable](#making-book-titles-clickable)
- [Accessibility Fixes: Buttons & Logo Alt Text](#accessibility-fixes)
- [Fix: Button Linking Directly to Form](#fix-button-linking-directly-to-form)
- [SEO Structured Data Fixes (Completed)](#seo-structured-data-fixes-completed)
- [Snapshot References](#snapshot-references)
- [Books Page Redesign (Squarespace 7.1)](#books-page-redesign-squarespace-71) 📖
- [Penelope’s Corner SEO Update](#penelopes-corner-seo-update)
- [External Links Used](#external-links-used)
- [Social Proof & Authority: Reader Reviews](#social-proof--authority-reader-reviews-) ⭐⭐⭐⭐⭐
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

## Anchor Links to Jump Directly to Books Section

One issue we found was that homepage buttons pointing to `/books` only took users to the top of the Books page. Visitors still had to scroll down to reach the actual book covers.

To improve usability, we added an **anchor link** so the buttons jump directly to the book section.

### How It Works

1. **Add a Section ID**
   * On the Books page, edit the section where the book covers start.
   * In Section Settings, set the **Section ID** to:

```
books-section
```

2. **Update Button Links**
   * Instead of linking homepage buttons to `/books`, link them to:

```
/books#books-section
```

### Result

Now, when visitors click **"See All Books"** on the homepage, they are taken directly to the book covers on the Books page without extra scrolling.

## Making Book Titles Clickable

The Books page redesign used a Squarespace gallery to align all book covers in a consistent grid. By default, only the **covers** were clickable links to individual book pages. While this worked, it wasn’t always obvious to visitors that the covers could be clicked.  

Adding separate buttons inside or under the gallery would be clunky and disrupt he clean layout. To improve usability without cluttering the design, we made the **book titles (h2s)** clickable as well.  

### Implementation

1. **Updated Gallery Captions**  
   - Wrapped each `<h2>` book title in an `<a>` tag linking to its internal book page.  
   - Example:  
     ```html
     <h2>
       <a href="https://www.ashleyrice.net/girls-rule">Girls Rule</a>
     </h2>
     <h3>Written and illustrated by Ashley Rice</h3>
     <span>Book description here...</span>
     ```

2. **Styled Links with Custom CSS**  
   - By default, links add underlining, which made every book title look cluttered.  
   - To fix this, we added custom CSS in **Squarespace → Design → Custom CSS**:  
     ```css
     .sqs-gallery-block .gallery-caption h2 a {
       text-decoration: none;   /* removes underline */
       color: inherit;          /* keeps same color as h2 */
     }

     .sqs-gallery-block .gallery-caption h2 a:hover {
       text-decoration: underline; /* underline on hover only */
       cursor: pointer;            /* shows hand icon on hover */
     }
     ```
### Result

- Book titles are now **clickable links** to their dedicated pages.  
- Visitors can use either the **cover image** or the **title text** to navigate.  
- The page stays clean (no stacked buttons, no permanent underlines), with a clear hand cursor on hover for accessibility.
## Homepage & Page SEO Updates

Looking at Google Search Console results, we saw that most people searched for **"ashley rice books"** but were landing on the homepage instead of the Books page. Since users clearly wanted the books, we made "Ashley Rice Books" an action item by adding buttons and arrows linking directly to the Books section.

At the same time, we refined the meta descriptions across key pages (Home, Books, About, Wholesale, Contact) to better reflect search behavior and user intent. The goal was to emphasize **Ashley Rice Books** while keeping the wording inviting, not pushy.

### Books Page SEO Update

**Original Description:**  
Girl-power poems, quotes, and books by Ashley Rice for girls and tweens, with messages of encouragement, love, and friendship. (274 chars)  

**Updated SEO Title:**  
Ashley Rice Books – Inspiring Poems & Girl Power Reads for Tweens  

**Updated SEO Description:**  
Discover Ashley Rice books for girls and tweens—filled with poems, doodles, and quotes that inspire confidence, friendship, and girl power. (160 chars)  

This update directly targets user search behavior, makes the Google snippet more engaging, and reinforces the Books page as the main destination for the query *"ashley rice books."*
oks."

### Wholesale Page SEO Update

We refined the Wholesale page metadata to better match user intent and avoid sounding too pushy. The previous description emphasized "ordering," while the new version highlights *seeing current titles available wholesale*, which feels friendlier and aligns with the actual content.

**Original SEO Title:**  
Wholesale – Ashley Rice books, greeting cards, calendars, and notepads  

**Original SEO Description:**  
Order Ashley Rice's books, greeting cards, calendars, and notepads wholesale, all with girl-power themes of love, encouragement, and confidence. (158 chars)  

**Updated SEO Title:**  
Ashley Rice Books – See Current Titles Available Wholesale  

**Updated SEO Description:**  
See Ashley Rice’s current titles available wholesale—books, greeting cards, and calendars featuring poems, quotes, and girl-power themes of confidence and friendship. (159 chars)  

This update improves clarity, keeps the wording natural, and still reinforces keywords like **Ashley Rice books** and **wholesale**.

## Penelope’s Corner SEO Update ✨

We created a new page on the site called **Penelope’s Corner**, designed as a reader-first space that highlights Ashley Rice’s **most-quoted and most-reposted poems** — the ones people often search for, share on social media, or post on quote sites.

### Why this matters
- **SEO boost** → By including the full text of popular poems (e.g., *Friends*, *Women Who Change the World*), the page captures search traffic and helps people find Ashley’s work through Google.  
- **Reader engagement** → The page is written in Penelope’s voice, making it feel like a personal gift rather than a sales page.  
- **Good faith / authenticity** → While optimized for SEO, the intent is primarily to serve readers by giving them direct access to the words they love.  

### How poems are presented
Each featured poem is shown in **two ways**:
1. **Text version** → ensures accessibility, readability on all devices, and SEO indexing.  
2. **Image version** → shows the original illustrated card/book pages from Blue Mountain Arts, keeping the charm and authenticity of the original design.  

### Image optimization
We optimized all images in **Photoshop** before uploading:
- **Width:** ~1200px (sized for clean display across desktop and mobile).  
- **Resolution:** 72 dpi (standard for web, prevents oversized files).  
- **Format:** JPEG (balance of quality and load speed).  

This choice keeps pages visually rich while still loading quickly, which supports both **user experience** and **Core Web Vitals**.  

### Result
*Penelope’s Corner* is now both **reader-first and search-friendly**:
- Fans can read and share Ashley Rice’s most-loved poems in one place.  
- The page reinforces **Ashley Rice poems** as a searchable entity in Google.  
- Combining text + optimized images balances authenticity, SEO, and performance.


### About Page SEO Update

The About page originally had a short description that mentioned Ashley Rice as an author and illustrator, but it didn’t clearly distinguish her from other people with the same name. It also didn’t emphasize **Ashley Rice Books** as a branded keyword.

**Original SEO Title:**  
About – Ashley Rice  

**Original SEO Description:**  
Ashley Rice is the author and illustrator of inspiring books for girls and tweens about girl power, creativity, and confidence. (132 chars)  

**Updated SEO Title:**  
About Ashley Rice – Author & Illustrator of Girl Power Books  

**Updated SEO Description:**  
Learn about Ashley Rice, author and illustrator of girl-power books for girls and tweens—filled with poems, quotes, doodles, and creativity. (157 chars)  

This update strengthens branding, improves clarity, and helps Google distinguish Ashley Rice (author/illustrator) from other people with the same name, while reinforcing the connection to **Ashley Rice Books**.

### SEO Content Adjustments  

**Fix: Goodreads profile link**  
Instead of just a button, we added a sentence with context:  
*“Discover what readers are sharing on [Goodreads](https://www.goodreads.com/author/show/93018.Ashley_Rice), the world’s largest book review site.”*  
Why: This explains what Goodreads is, builds credibility, and helps parents/grandparents (buyers) understand it’s a trusted review source. Improves E-E-A-T signals (Experience, Expertise, Authoritativeness, Trust).  

**Fix: Internal linking**  
Added keyword-rich internal links between pages (e.g., About → Books).  
Why: Helps readers (and Google) move smoothly between pages, reinforces “Ashley Rice books” as a brand keyword, and distributes ranking authority across the site.  
 

### Homepage SEO Update

Google Search Console showed that most visitors searching for **"ashley rice books"** were landing on the homepage first. To better align with this behavior, we refined the homepage metadata to reinforce the brand and guide users toward the Books page without sounding pushy.

**Original SEO Title:**  
Ashley Rice – Author & Illustrator  

**Original SEO Description:**  
Inspiring poems, quotes, and books by Ashley Rice for girls and tweens—celebrating confidence, friendship, and creativity. (164 chars)  

**Updated SEO Title:**  
Ashley Rice Books – Inspiring Poems, Quotes & Girl Power for Tweens  

**Updated SEO Description:**  
Discover Ashley Rice Books—poems, quotes, and doodles for girls and tweens that celebrate confidence, friendship, and creativity. See current titles today. (159 chars)  

This update emphasizes the query **"ashley rice books"**, strengthens the homepage as the main entry point, and provides a clear action path for visitors to view current titles.

## Adding Alt Text in Squarespace 7.1 Galleries

Squarespace 7.1 handles gallery image alt text in two ways:

1. **Captions / Descriptions**  
   - If you type text into the image **Caption** or **Description** field, Squarespace will use that text as the image’s alt text.  
   - ⚠️ However, this text will also **display on the page**. Since we were already using custom HTML (`<h2>`, `<h3>`, `<span>`) in descriptions for book titles and summaries, adding alt text here would clutter the design.  

2. **Asset Library Filenames (Hidden Alt Text)**  
   - If you rename the image in the **Asset Library**, Squarespace will use the file name as the invisible `alt` attribute.  
   - This gives you proper alt text for SEO and accessibility without adding visible text on the page.  

### How We Fixed It
1. Go to **Website → Assets**.  
2. Find each gallery image (book covers, calendars, illustrations).  
3. Click the **⋯** next to the image → **Rename**.  
4. Enter a descriptive filename in plain English (no dashes), e.g.:  
   - `You Are a Girl Who Can Do Anything by Ashley Rice book cover.jpg`  
   - `Girls Rule Ashley Rice book cover.jpg`  
   - `You Are an Amazing Girl Ashley Rice calendar cover.jpg`  
   - `Penelope J Miller narrator illustration Ashley Rice.jpg`  
   - `Heart arrow doodle illustration.png`  
   - `Ashley Rice with earlier books cards and stationery.jpg`  

### Result
By renaming images in the Asset Library, we ensured each gallery image has proper invisible alt text for screen readers and search engines, while keeping the visible layout clean.

### About Page Internal Link
To improve navigation and SEO, we added a keyword-rich internal link at the bottom of the About page:
- Check out her current books here!

This reinforces the query **"Ashley Rice books"** with descriptive anchor text while giving visitors a direct path to the Books section.

### External Links Used

As part of the SEO updates, we added direct catalog and retailer links to guide users toward Ashley Rice’s books and strengthen entity recognition:

- [Amazon Author Page](https://www.amazon.com/stores/Ashley-Rice/author/B001JPAHAS?ref=ap_rdr&isDramIntegrated=true&shoppingPortalEnabled=true&ccs_id=6ddd6743-9783-47e3-95c6-fbcf0629e45f)  
- [Barnes & Noble Author Listings](https://www.barnesandnoble.com/s/%22Ashley%20Rice%22;jsessionid=5C96C22DF928CDA02A68F31B8AF4EDDF.prodny_store01-atgap06?Ntk=P_key_Contributor_List&Ns=P_Sales_Rank&Ntx=mode+matchall)  
- [LibraryThing Author Profile](https://www.librarything.com/author/riceashley) — backlink to a bibliographic database used by readers and librarians, supporting SEO credibility in Google Search.  
- [Google Books](https://www.google.com/books/edition/You_Are_a_Girl_Who_Can_Do_Anything/B_KWnAEACAAJ?hl=en) — specific title reference on Google Books for entity alignment and catalog verification.  

These links were integrated into site content as follows:  
- **About Page (final line):** “Check out her current books here” → linked to Amazon.  
- **Wholesale Page (caption under photo):** Added links for Amazon and Barnes & Noble to provide non-wholesale options.  

**Why this matters:** Adding external catalog and retailer references improves trust signals, supports entity building across book databases, and strengthens overall SEO visibility.

### Social Proof & Authority: Reader Reviews ⭐⭐⭐⭐⭐
To strengthen **E-E-A-T (Experience, Expertise, Authoritativeness, Trustworthiness)** signals on the site, we added select Amazon reviews to the landing page.

- **Why this matters**  
  - Reviews act as **social proof**, showing real-world impact and building trust.  
  - They reinforce **author authority**, demonstrating that books are widely read and valued.  
  - While reviews don’t directly improve SEO rankings, they **increase engagement metrics** (time on page, scroll depth) that search engines consider as positive signals.  
  - Outbound links to Amazon also support book visibility where reviews and rankings drive discovery.  

- **Why these reviews**  
  - We chose a mix for maximum impact:  
    - Bullying story → emotional resonance.  
    - Repeat buyer → loyalty and credibility.  
    - Kid’s own words → authenticity from the target audience.  
  - Only short excerpts were used, attributed as “— Amazon Reviewer,” keeping within fair use.  


# Accessibility Fixes

### Fix 1: Buttons

**Before:**
- Buttons used the Squarespace default **light lavender background** with **white text**.
   - This combination failed WCAG contrast checks and was flagged in WAVE as *low-contrast text*.
- Some buttons had **long labels** (e.g., *“Shop Ashley Rice Calendar at Hallmark”*) that wrapped onto two lines.
   - WAVE flagged these as accessibility errors because wrapped button text is harder for screen readers and reduces usability.
- Example:
   - *"Sign Up"* button in the footer appeared pale and was difficult to read against its background.
   - The *“Shop Ashley Rice Calendar at Hallmark”* button appeared oversized and cluttered due to the wrapping text.

**After:**
- All buttons were updated to use **dark purple** (`#5A2D82`) backgrounds with **white** (`#FFFFFF`) text.
   - This pairing passes WCAG AA/AAA contrast requirements (contrast ratio ~9.85:1).
- Button labels were shortened (e.g., *“Shop Ashley Rice Calendar at Hallmark”* → *“Shop the calendar”*).
   - Shorter text prevents wrapping, improves readability, and ensures screen readers announce the label clearly.
- Example:
   - *"Sign Up"* footer button now displays with a bold purple background and high-contrast white text, making it much more legible.
   - *“Shop the calendar”* button is concise, balanced, and no longer wraps across multiple lines.

**Outcome:**
- All buttons across the site now use consistent colors and shorter, accessible text.
- Both **contrast errors** and **button text wrapping errors** flagged by WAVE were resolved.
- Calls-to-action are easier to see, understand, and interact with, improving both usability and inclusivity.

---

### Fix 2: Logo Alt Text

**Before:**
- The site logo was pulling a long **Site Title** string into its alt text:
  *“Ashley Rice | Girl Power Author & Illustrator of Poems, Tween Books & Cute Art.”*
- WAVE flagged this as an **error** because alt text was too long, keyword-stuffed, and not descriptive in a simple way.
- Long alt text makes it harder for screen readers to announce the logo clearly.

**After:**
- The **Site Title** was shortened so that the logo’s alt text is concise and clear.
- Final version: *“Ashley Rice | Author & Illustrator”*
   - This keeps it descriptive without overloading keywords.
   - Screen readers can now announce the logo properly without extra clutter.

**Outcome:**
- The **logo alt text error flagged by WAVE was resolved**.
- The site is now more accessible for users who rely on screen readers.
- SEO is unaffected since other metadata and headings provide keyword context.

# Fix: Button Linking Directly to Form

While editing buttons, we noticed that the **"Share your own answer"** button did not jump directly to the form. Instead, it only sent users to the **top of the Books page**, which meant they had to scroll down to find the form manually.

To improve usability and accessibility, we updated the button to link **directly to the form block** on the Books page.

## How We Fixed It

Squarespace 7.1 gives each block on a page a unique ID (e.g., `block-yui_...`). By finding the ID of the form block and appending it to the page URL, we created a button that jumps to the exact section.

### Steps:

1. Open the page in your browser (Chrome recommended).
2. Right-click on the block you want to target (in this case, the form) → choose **Inspect**.
3. In the HTML panel, find the `<div>` with an `id` that starts with:

   ```
   block-yui_...
   ```

   Example:

   ```
   id="block-yui_3_17_2_1_1757901031143_2230"
   ```

4. Copy that full ID.
5. Edit the button link and format it like this:

   ```
   /pagename#block-yui_3_17_2_1_1757901031143_2230
   ```

   - `/pagename` = the slug of the page (e.g., `/books`)
   - `#block-yui_...` = the block ID you copied

**Example used here:**

```
/books#block-yui_3_17_2_1_1757901031143_2230
```

## SEO Structured Data Fixes (Completed)

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

4. **Tools help uncover hidden issues**: SEMrush and Google's Rich Results Test revealed proems I couldn't see just by browsing the site.

5. **SEO is iterative**: Each fix leads to the next test. Visibility builds through steady corrections, not one-time changes.

### Notes to Self / Next Steps✨
- ~~Fix broken Pinterest backlinks (301 redirect or remove)~~  
- ~~Start with writing unique meta descriptions for Home, Books, About, Contact, Wholesale~~
- After Search Console verifies domain, check **Index Coverage** to confirm all 5 main pages are indexed  
- ~~Use **Rich Results Test** again to confirm schema cleanup (WebSite vs. LocalBusiness)~~  
- ~~Consider adding 150–300 words of intro text to Books and About pages for SEO~~  
- Re-run SEMrush once quota resets to confirm errors are resolved
- ~~Fix the mobile view — check alignment of covers + captions in one-column layouts.~~
- Verify with SEMrush or Google crawler that H2/H3 headings inside captions are being read correctly.
- Look into: compressing book covers to lighter WebP/PNG for better performance (improves Core Web Vitals).


