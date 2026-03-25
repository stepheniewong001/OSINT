# OSINT Exercise: Reconstructing a Deleted Digital Footprint

## 🎯 Objective
To investigate whether information removed from a website can still be recovered using public sources and technical methods, and to understand how data persists across different layers of the web.

---

## 🔍 Methodology

### 1. Search Engine Analysis
Initial searches returned mostly irrelevant results due to name ambiguity.

Refined queries using:
- exact match (`"..."`)
- exclusion operators (`-keyword`)

This helped isolate relevant references and reduce noise.

**Finding:**
Search results still displayed descriptive snippets of previously available content, even after the live page was updated.

![Google Snippet](screenshots/google-snippet.png)

---

### 2. Web Archive Check
Checked the Wayback Machine for historical snapshots of the page.

**Result:**
No archived version of the page was available.

**Insight:**
Not all pages are archived. Capture depends on crawl timing or manual submission.

![Wayback Result](screenshots/wayback-no-archive.png)

---

### 3. Cache Verification
Attempted to retrieve cached versions using:

**Result:**
No cached version found.

**Insight:**
Search engine cache is temporary and may be removed after re-crawling, even if snippets remain.

---

### 4. Frontend Inspection
Viewed page source and inspected the page using browser DevTools.

**Result:**
No residual references found in the HTML or visible page structure.

**Insight:**
Frontend reflects only the current state and does not retain historical content.

---

### 5. Network / API Analysis
Explored network requests (GraphQL / Voyager) to understand how content is loaded.

**Result:**
Only current data was returned. No historical content was accessible.

**Insight:**
Modern web applications load content dynamically via APIs.  
Once data is updated or removed server-side, previous versions are not accessible through frontend or API.

---

### 6. Metadata Review
Checked `<head>` section for meta tags (e.g. description, Open Graph).

**Result:**
No relevant references found.

**Insight:**
Metadata is typically updated alongside page content and does not preserve previous versions.

---

## 🧠 Key Learnings

### 1. Data exists in layers
Information may exist across:
- Backend (source of truth)
- Frontend (UI)
- Search engine index
- Cache
- Archive

---

### 2. Deletion is not immediate across systems
Search engines may temporarily retain outdated snippets even after content is removed.

---

### 3. True deletion occurs at backend level
Once data is removed from the server/database, it is no longer recoverable via:
- Inspect (HTML)
- API requests
- Network analysis

---

### 4. Tools have limitations
- Wayback Machine is incomplete  
- Google cache is temporary  
- DevTools only show current state  
- APIs return only live backend data  

---

### 5. Investigation includes ruling out possibilities
Confirming where data does *not* exist is part of the analytical process.

---

## 🧭 Conclusion

The original content could not be recovered through technical methods.  
However, residual traces in search engine snippets confirmed that the data previously existed.

This demonstrates how information persists temporarily across systems before full removal.

---

## 🪞 Reflection

Initially, the focus was on recovering deleted content.  
Through the process, the more important takeaway was understanding:

- where data still exists  
- where it no longer does  
- and why  

This exercise reinforced that effective investigation is not just about finding information, but also about identifying the limits of its availability.

---

## 📸 Evidence

Screenshots included:
- Search engine snippet showing residual data  
- Wayback Machine result showing no archive  
