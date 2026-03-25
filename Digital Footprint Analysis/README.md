# OSINT Exercise: Reconstructing a Deleted Digital Footprint

## Objective
This project aimed to examine how data persists across web systems after deletion from a primary source. The investigation involved testing multiple layers, including search engine indexing, web archives, cache, and frontend/API inspection, to assess whether removed content could still be recovered. This hands-on exercise was designed to build a deeper understanding of data lifecycle, limitations of OSINT tools, and how modern web systems store and deliver information.

### Skills Learned

- Understanding of data persistence across web layers (backend, frontend, search index, cache, archives).
- Applied search refinement (exact match, exclusion) to isolate relevant information from noisy results.
- Conducted multi-layer validation of data availability across search, cache, archives, and live systems.
- Basic understanding of API-driven web architecture (GraphQL / Voyager).
- Used browser DevTools to inspect page structure and analyze network requests.
- Identified limitations of OSINT tools and differences between live, cached, and archived data.
- Applied hypothesis-driven investigation and analytical reasoning.

### Tools Used

**Search & Discovery**
- Google Search Operators (exact match, exclusion operators)

**Archival & Cache Analysis**
- Wayback Machine
- Google Cache

**Web Analysis**
- Chrome DevTools (Elements, Network)
- HTML Source inspection

## Steps

### 1. Initial Search & Problem Identification
Conducted an initial Google search on the individual.

Observed that results were highly noisy due to name ambiguity, with multiple unrelated entries and dominant but irrelevant results appearing.

To improve result quality, refined queries using:
- exact match: "..."
- exclusion operators: -keyword

This helped isolate relevant references and reduce noise.

---

### 2. Identification of Residual Data
From the refined search results, identified Google snippets that displayed information about the individual (e.g. roles, affiliations).

Upon clicking into the webpage, observed that the same information was no longer present on the live site.

This indicates that:
- the content had been removed from the website
- but still persisted in Google’s indexed snippet

📸 Screenshot:
- Include: Google search result showing snippet with removed information

---

### 3. Attempted Historical Recovery

#### 3.1 Wayback Machine
Checked the URL using Wayback Machine to determine if a historical snapshot existed.

Result:
- No archived version found

Insight:
- Not all pages are archived
- Archiving depends on crawl timing or manual submission

📸 Screenshot:
- Include: Wayback Machine showing no snapshots

---

#### 3.2 Google Cache
Attempted to retrieve a cached version using:
cache:<URL>

Result:
- No cached page available (likely refreshed or cleared)

Insight:
- Google cache is temporary
- Snippets may persist even when full cached pages are no longer available

📸 Screenshot:
- Optional (skip unless clean)

---

### 4. Page Source Analysis (HTML Level)
Viewed the page source to check whether removed information still existed within the HTML.

Specifically checked for:
- visible text remnants
- comments
- metadata (e.g. <meta> tags)

Result:
- No relevant data found

Insight:
- Page source reflects the current state of the webpage
- Removed content is not retained in the HTML once deleted server-side

---

### 5. Frontend Inspection (DevTools – Elements)
Used browser DevTools (Elements tab) to inspect the page structure (DOM).

Purpose:
- To determine whether the content was still present but hidden (e.g. via CSS or dynamic rendering)

Result:
- No hidden or residual content identified

Conclusion:
- The data was not hidden; it had been fully removed from the page
  
---

### 6. Network / API Analysis (Backend Check)
Opened the Network tab in DevTools and reloaded the page to observe requests (e.g. GraphQL / Voyager).

Purpose:
- To determine whether the backend was still returning the removed data

Observation:
- API responses only contained current data
- No historical or removed information was returned

Insight:
- Modern web applications load content dynamically via APIs
- Once data is removed from the backend, it is no longer accessible through frontend or network requests

---

### 7. Consolidation of Findings
Tested data availability across multiple layers:
- Search index (Google snippet)
- Archive (Wayback)
- Cache (Google)
- Frontend (live page)
- Source/DOM (HTML & Elements)
- Backend (API responses)

Conclusion:
- Data persisted only in the search engine snippet
- It was not recoverable from any current technical layer
- The information is no longer accessible through public-facing systems
