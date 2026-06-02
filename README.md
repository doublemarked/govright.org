# GovRight.org — Static Backup

A self-contained static snapshot of the WordPress site **http://govright.org**
("GovRight | Government is People"), captured **2026-06-02**.

## How to use it

The site lives in the **`docs/`** folder and is hosted on **GitHub Pages**
(served from `main` branch → `/docs`).

You can also browse it locally: open **`docs/index.html`** in any web browser
(double-click it). The whole site works offline — every page, image, stylesheet,
and script is local. Links are document-relative, so the same files work both
offline and when served from any static host (GitHub Pages, Netlify, S3, etc.).

## What's included

- **All 14 pages** and **19 posts** (news articles)
- The **2 project pages** (MENA, Eastern Europe) and their category archives
- **Blog pagination** and author archive
- **148 media files** — every image referenced by the site plus the full-size
  originals (~62 MB total, 245 files)
- The complete **Divi theme** styling, fonts, and scripts

## Capture notes

- Mirrored with `wget`, then post-processed for clean offline use:
  - Post **shortlinks** (`/?p=NNN`) were remapped to their pretty permalinks and
    duplicate copies removed.
  - WordPress **discovery metadata** (XML-RPC/RSD/pingback, feed and oEmbed
    `<link>` tags) was stripped — invisible plumbing that pointed back at the
    live server.
  - The theme's broken `/2/ /3/ /4/` pagination links (which 404 on the live
    site) were repointed at the real `page/N/` pages so they work here.
  - The **Google Analytics** tracker (`UA-53749874-2`) was removed — it was
    broken offline (protocol-relative URL) and shouldn't track visitors of an
    archive.
  - Two icon-font files wget mis-saved as `*.ttf.html` were renamed to `.ttf`
    and their CSS references corrected.
  - Asset files whose names contained `?` (e.g. `style.css?ver=5.0.3.css`, a
    wget artifact that breaks on web servers) were renamed to clean names
    (`style.css`) with all references updated — so the site serves correctly
    over HTTP, not just `file://`.
  - WordPress's **emoji loader** script was removed (non-essential plumbing that
    fetched a polyfill from the live server).
  - The header logo and homepage hero image were hard-coded (by the Divi page
    builder) to an old `*.sites.empathic.io` staging domain over `http://`,
    which an HTTPS host blocks as mixed content. Those assets were pulled into
    the archive and re-pointed at same-origin paths.
- **Verified with a full headless-browser audit served over HTTP** (every page
  loaded via the Chrome DevTools Protocol, the same way Pages serves it): all
  **52 pages** render correctly with **0** broken links, **0** missing
  resources, **0** failed HTTP requests, **0** JavaScript errors, and **0**
  console errors.

## Still loads from the network (when online)

A few resources are intentionally left as external links because they don't
belong to this site: **Google Fonts** (web fonts — text falls back to system
fonts if offline), WordPress emoji, embedded **Twitter** content, and outbound
links to partner sites (legislationlab.org, participation.ma, etc.).
