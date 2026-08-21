# PUP BS Statistics 2026 | Official Website

Welcome to the source for the official digital space of the Bachelor of Science in Statistics program at the Polytechnic University of the Philippines (PUP).

This repository stores a simple, responsive static website (HTML/CSS/JS) that showcases the BS Statistics program: curriculum overview, faculty, career pathways, student organizations, photo gallery, and an interactive directory of academic papers and presentations produced by the current batch.

Motto: "Estadistika ng Bayan, para sa bayan"

---

## Table of Contents

- [Demo / Preview](#demo--preview)
- [What this project contains](#what-this-project-contains)
- [Features](#features)
- [Tech stack](#tech-stack)
- [How to run locally](#how-to-run-locally)
- [How to contribute (step-by-step)](#how-to-contribute-step-by-step)
- [How to add or update papers](#how-to-add-or-update-papers)
- [How to add images and media](#how-to-add-images-and-media)
- [Accessibility & best practices](#accessibility--best-practices)
- [GitHub Pages (publish the site)](#github-pages-publish-the-site)
- [Maintainers / Contact](#maintainers--contact)

---

## Demo / Preview

Open `index.html` in a modern browser to view the site locally. The site is a single-page layout with sections for Home, About, Academic Papers, and Contact. The theme toggle (dark/light) and an auto-advancing image carousel are implemented in vanilla JavaScript.

---

## What this project contains

Key files and directories:
- `index.html` — the full website (HTML/CSS/JS combined). Primary source of content and logic (navigation, theme toggle, carousel, modal, and papers directory).
- Images referenced in `index.html` (e.g., `iskatistics_logo.jpg`, `blk_two_tailed.jpg`, `batchpic1.jpg`, `placeholder.jpg`) — keep them in the repo root or an `assets/` directory and update paths in `index.html`.
- This README (you are reading it).

The site stores a client-side array `allPapers` inside `index.html` for the batch research directory. Papers are rendered dynamically and can be searched using the search box.

---

## Features

- Responsive layout (desktop & mobile).
- Light / Dark theme persistence via `localStorage`.
- Image carousel with indicators and auto-advance.
- Accessible modal for events, resources, and paper abstracts.
- Searchable research directory (client-side).
- Faculty, career pathways, FAQs, and contact details for two sections:
  - BSSTAT 4-1: Iskatistics — stats1.1.2022@gmail.com, facebook.com/Iskat1st1cs
  - BSSTAT 4-2: Blk Two-tailed — bsstatsone2.pup@gmail.com, facebook.com/blktwotailed

---

## Tech stack

- Plain HTML (single page)
- CSS (inlined in `index.html`)
- Vanilla JavaScript (inlined in `index.html`)
- No build step required

---

## How to run locally

Option A — quick (recommended for editing/testing):
1. Clone the repository:
   git clone https://github.com/iskatistics/pup_bsstat2026_website.git
2. Open `index.html` in your browser:
   - double-click `index.html`, or
   - right-click → Open with → choose your browser

Option B — local static server (better for AJAX-like behaviors and consistent URL handling):
1. From the project directory run a simple HTTP server:
   - Python 3: `python -m http.server 8000`
   - Node (http-server): `npx http-server -p 8000`
2. Open http://localhost:8000 in your browser.

---

## How to contribute (step-by-step)

Contributions are welcome for content updates, bug fixes, accessibility improvements, adding papers, images, or UI improvements.

1. Fork the repository on GitHub.
2. Clone your fork:
   git clone https://github.com/<your-username>/pup_bsstat2026_website.git
3. Create a feature branch:
   git checkout -b feat/describe-change
   - Use branch names like `fix/`, `feat/`, `chore/` and a short kebab-case description.
4. Make your changes:
   - Prefer small, focused commits.
   - If editing content such as faculty, FAQ, or contact, update `index.html` where those sections are defined.
   - When adding images, place them in `assets/` (create it if missing) and reference them with relative paths in `index.html`.
   - When adding or editing papers, update the `allPapers` array in the JS portion of `index.html` (see the example below).
5. Test locally (open `index.html` or run a local server; check mobile and desktop layouts).
6. Commit with a clear message:
   git add .
   git commit -m "feat: add new research entry for student X"
7. Push your branch:
   git push origin feat/describe-change
8. Open a Pull Request to the main branch of the upstream repository:
   - Describe the change and include screenshots if UI changes occurred.
   - Link any issue(s) if relevant.
9. Wait for review. Address requested changes by committing to the same branch; the PR will update automatically.
10. After approval, PR is merged. Optionally delete the feature branch.

Contribution guidelines and helpful notes:
- Keep filenames lowercase and avoid spaces (use dashes `-` or underscores `_`).
- Compress/resize large images before adding them (helps page load).
- Include `alt` attributes for all images.
- When updating UI behavior, explain the reason and cross-test on mobile.
- If you add many papers or content, consider moving the papers list into a JSON file (e.g., `data/papers.json`) and modify `index.html` to fetch it — this keeps the HTML cleaner. Open an issue first if you propose refactor.

---

## How to add or update papers

Papers are stored in the `allPapers` JS array inside `index.html`. Each entry uses this structure:

{
  sec: "4-1",
  title: "Title of the Paper",
  res: "Author 1, Author 2, ...",
  // optionally you can add fields like abstract or file links
}

Example — add this inside the array:

{ 
  sec: "4-1",
  title: "A New Study on Data and Society",
  res: "Juan Dela Cruz, Maria Santos"
},

After updating `allPapers`:
- Save `index.html`.
- Open the page and verify the new paper appears in the Research Directory and that the modal opens with the expected content.
- If your entry includes special characters or single quotes, ensure proper escaping in the inline `onclick` modal call.

If you plan to add many papers, consider:
- Moving the array to `data/papers.json` and load it via fetch (requires running from a web server, not via file://).
- Adding an "abstract" property and rendering it in the modal.

---

## How to add images and media

- Create an `assets/` directory (recommended) and commit images there.
- Use consistent naming, e.g., `batchpic1.jpg`, `faculty_katrina.jpg`.
- Update `index.html` image src paths accordingly.
- Keep images reasonably sized (e.g., max width 1600px, optimized JPG/WEBP).
- Add descriptive `alt` text to each image for accessibility.

Carousel considerations:
- The carousel expects 4 slides in the current DOM — if you add or remove slides, ensure the indicators and JS logic still match the number of `.carousel-slide` elements. The script uses the number of `.carousel-slide` elements to determine limits; adding slides should work automatically but validate indicators.

---

## Accessibility & best practices

- Provide meaningful `alt` text for images.
- Ensure buttons and interactive elements are keyboard accessible.
- Use semantic headings and ARIA attributes if adding dynamic components.
- Prefer readable contrast values between text and background; the page already includes a light/dark theme toggle — test both themes for contrast.
- Keep modals focus-trapped when you implement full a11y improvements (current modal is simple — consider improving for full accessibility).

---

## GitHub Pages (publish the site)

To publish the site using GitHub Pages:
1. Push your branch/changes to the repository.
2. In the repo settings → Pages, set the source to the `main` (or default) branch and the root (`/`) directory.
3. Save and wait a few minutes. The site will be available at `https://iskatistics.github.io/pup_bsstat2026_website/` (or the username repo URL). Adjust and verify correctly.

If you prefer `docs/` folder publishing:
- Move `index.html` and assets to a `docs/` folder and set the Pages source to `main` branch / `docs` folder.

---

## Maintainers / Contact

Primary contacts referenced in site:
- BSSTAT 4-1: Iskatistics — stats1.1.2022@gmail.com — https://www.facebook.com/Iskat1st1cs
- BSSTAT 4-2: Blk Two-tailed — bsstatsone2.pup@gmail.com — https://www.facebook.com/blktwotailed

