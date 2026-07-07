# University Syllabus Revision Portal
 
A lightweight, front-end-only web app for students to log in and browse their
semester-wise course syllabi (PDFs) from a single dashboard.
 
## Information
 
- **Type:** Static web application (HTML/CSS/JS, no backend/server)
- **Pages:**
  - `project.html` — Login screen
  - `project2.html` — Student dashboard with semester filter and course cards
- **Purpose:** Give students a quick, single-page way to find and open the
  correct syllabus PDF for each subject, organized by semester (1–8)
## Key Features
 
- **University email login gate** — restricts access to emails ending in a
  specific domain (currently `@ppsu.ac.in`)
- **Semester filter dropdown** — instantly shows/hides course cards for the
  selected semester (1 through 8) without a page reload
- **Course card grid** — responsive grid (`auto-fit`, `minmax`) that reflows
  from multi-column to single-column on smaller screens
- **Direct PDF access** — each course card links straight to its syllabus PDF,
  opened in a new tab
- **Responsive design** — mobile-friendly layout via CSS media queries on both
  pages
- **Simple visual branding** — university logo, consistent color palette
  (navy/blue/red), card shadows and hover states
## Technical Architecture
 
| Layer | Details |
|---|---|
| Markup | Plain HTML5, two standalone pages |
| Styling | Inline `<style>` blocks per page, CSS custom properties (`:root` variables) for theming, Flexbox + CSS Grid for layout, `@keyframes` for entrance animation |
| Logic | Vanilla JavaScript, no frameworks or build tools |
| Data | Hardcoded in markup — no database or API calls |
| Navigation | Plain `window.location.href` redirect from login to dashboard |
| Assets | Local image files (logo, icons) and local PDF files referenced by relative path |
 
### Page flow
 
```
project.html (Login)
      │
      │  validates email domain + password client-side
      ▼
project2.html (Dashboard)
      │
      │  semester dropdown → filterSemester()
      ▼
  Course cards (filtered by data-semester attribute)
      │
      ▼
  Syllabus PDF (opens in new tab)
```
 
> **Note:** The current login check runs entirely in client-side JavaScript
> (email domain + a fixed password string). This is fine as a UI mock/prototype,
> but it is **not secure** — anyone can view the source and see the check, and
> there's no real authentication, session, or backend. If this is meant for
> real deployment, swap this out for a proper backend auth service before use.
 
## Project Structure
 
```
project-root/
├── project.html          # Login page (entry point)
├── project2.html          # Dashboard page (post-login)
├── universitylogo.jpeg     # Logo used on login page
├── uni logo.png            # Icon used on each course card
├── README.md
└── syllabus PDFs/          # Referenced PDF files (relative paths), e.g.
    ├── Joy of Programming (SECE1120).pdf
    ├── Cyberspace Awareness (SEIT1110).pdf
    ├── Conceptual Experimental Physics (SESH1130).pdf
    ├── Core Engineering Concept (SECV1110).pdf
    ├── Linear Algebra (SESH1120).pdf
    ├── Fundamental Chemistry and Environmental Science (SECH1110).pdf
    ├── Competitive Quantitative Aptitude (SEIT1120).pdf
    ├── data stucture.pdf.pdf
    └── ... (additional semester PDFs)
```
 
## Getting Started
 
1. Place all HTML, image, and PDF files in the same folder (matching the
   relative paths used in the code).
2. Open `project.html` in a browser.
3. Log in with a `@ppsu.ac.in` email (see note above on the current
   client-side-only check).
4. On the dashboard, pick a semester from the dropdown to view its courses,
   then click **Open PDF** on any course card.
## Possible Improvements
 
- Move authentication to a real backend (server-side validation, hashed
  passwords, sessions/tokens)
- Fix duplicate/placeholder PDF links (several semester 3–5 cards currently
  point to the same `PRAC 8 AI(193).pdf` file)
- Standardize file naming (e.g. `data stucture.pdf.pdf` has a typo and double
  extension)
- Move course/PDF data into a JSON file or database instead of hardcoding
  cards in HTML
- Add an "All Semesters" option to the dropdown
 
