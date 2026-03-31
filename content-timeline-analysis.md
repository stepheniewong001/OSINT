# Extension: Content Timeline & Modification Analysis

> This analysis builds on the original investigation:  
> [Reconstructing a Deleted Digital Footprint](https://github.com/stepheniewong001/OSINT/blob/main/Digital%20Footprint%20Analysis/README.md)

## Objective
Analysed a target webpage using publicly available artifacts (XML sitemap, HTML metadata, and HTTP headers) to reconstruct its creation date, last modification timestamp, and visibility across archival layers, and to assess whether historical versions of the page could be recovered.

### Skills Learned

- Timeline reconstruction using sitemap, metadata, and HTTP headers
- Interpretation of CMS-generated metadata (published_time vs modified_time)
- Understanding limitations of archival systems (cache vs archive vs live state)
- Correlating multiple data sources to validate system state

### Tools Used

**Web Analysis**
- XML Sitemap
- HTML Metadata Inspection (View Page Source)
- Chrome DevTools (Network → Headers)

## Steps

### 8. Sitemap Analysis (Last Modified Time)
Located the site’s XML sitemap (< root domain url >/sitemap.xml) and navigated to the relevant sitemap file (post-sitemap.xml) to search for the target URL.

Observed entry:

    <loc>https://www.indsights.sg/event-indsights-business-leaders-forum-2025/</loc>
    <lastmod>2026-03-23T03:00:00+00:00</lastmod>


- Interpretation
    - The page was last modified on 23 March 2026, 03:00 UTC
    - Converted to Singapore Time (UTC+8):
       → 23 March 2026, 11:00 AM SGT

- Insight:
    - Sitemap provides last modification timestamp only
    - It does not provide creation date or edit history

---

### 9. Metadata Analysis (Creation vs Modification)
Inspected the HTML source and identified metadata fields:

      article:published_time = 2024-12-05
      article:modified_time  = 2026-03-23

- Interpretation:
     - Page was initially created on 5 December 2024
     - Last updated on 23 March 2026

- Insight:
    - Metadata allows differentiation between:
       - creation (published_time)
       - latest update (modified_time)
     - However, intermediate edits are not visible (no version history exposed)

---

### 10. Attempt to Retrieve Historical Versions

#### 10.1 Wayback Machine
  - No archived snapshots found

#### 10.2 Google Cache
  - No cached version available

---

### 11. Network Header Validation
Used Chrome DevTools:

- Steps:
    - Inspect page → Network tab
    - Reload page
    - Select main document request
    - Inspect Response Headers

- Checked for:
    - Last-Modified
    - ETag

- Observation:
    - Last-Modified aligns with sitemap/metadata timestamp

- Insight:
     - Confirms server-side last update timing
     - Does not provide historical edit records

---

### Consolidation of Findings
- Page lifecycle:
  - Created: Dec 2024
  - Last updated: Mar 2026
- No historical snapshots available via:
  - Wayback Machine
  - Google Cache
- No residual data found in:
  - HTML source
  - DOM (Elements)
  - API responses

Conclusion:
- No historical versions could be reconstructed due to:
  - lack of archival capture
  - absence of caching
- Sitemap and metadata provide point-in-time signals, not full edit history


Resource Referenced:
- [How to find out when a website was last updated](https://www.youtube.com/watch?v=wA8QoInDMYg)


