# SEO Structured Data Fixes

## Rich Test Results Snapshot

I was working on my website and got this error when testing structured data.  
When this happens, a good thing to do is go to the **Rich Results Test**.  

The Rich Results Test is a site made by **Google**. It’s free to use and checks whether your structured data (schema markup) is valid and eligible for rich results in search.  
👉 [Try it here](https://search.google.com/test/rich-results)  

This repo includes snapshots from that tool to help document test outcomes, including:  
- **rich-test-results.png** – example of the error message  
- **local-business.png** – example of testing local business schema

## Error 1: LocalBusiness Schema Injected by Squarespace

### What happened
At one point I sold animations directly through my Squarespace site.  
Because of that, Squarespace automatically injected **LocalBusiness** schema into the site template.  

Later, I stopped selling through Squarespace and deleted the commerce pages.  
Now my site only links to outside retailers (Amazon and Barnes & Noble) for my books.  
But the LocalBusiness schema code stayed in the background — even though I was no longer running a business on the site.  

When I ran the Rich Results Test, it still tried to validate my site as a Local Business and threw errors.

Here’s what the tool reported:
<p align="center">
  <img src="https://github.com/ashleysally00/seo-structured-data-fixes/raw/main/rich-test-results.png" width="65%">
</p>


- Missing field **"name"**  
- Missing field **"telephone"** (optional)  
- Missing field **"priceRange"** (optional)  
- Missing field **"address"** (optional)  

---

### Problem code (Squarespace-injected LocalBusiness schema)
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "",
  "address": "",
  "telephone": "",
  "priceRange": ""
}
</script>
````
This block was leftover from Squarespace commerce — but my site was no longer selling directly.
All purchases now happen through Amazon or Barnes & Noble links, not on my site.

### The fix

I removed the LocalBusiness schema completely.
Instead, I kept only the schema that actually applies to my site, like WebSite.

````
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "name": "My Website",
  "url": "https://www.mywebsite.com"
}
</script>
````
