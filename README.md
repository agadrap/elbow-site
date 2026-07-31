# elbow-site

Marketing + legal site for **elbow**, served at [elbow-app.com](https://elbow-app.com).

Static, hand-coded HTML — no build step. Mirrors the structure of `life-in-uk-site`.

## Structure

```
index.html            Landing page (hero, features, how-it-works, privacy, CTA)
about/index.html      About / story
privacy/index.html    Privacy Policy   →  /privacy/
terms/index.html      Terms of Use     →  /terms/
support/index.html    Support + FAQ    →  /support/  (contact: hello@byaga.dev)
assets/site.css       Shared nav + footer + subpage typography
assets/logo-wordmark.png   Licensed "elbow" wordmark (white, transparent) — used for the logo lockups
assets/logo-mark.png       "e" mark (white, transparent)
assets/app-icon-1024.png   App icon — source for the favicons
assets/og-image.png        1200×630 social share image
assets/og-card-source.html Source used to render og-image.png
favicon.ico, favicon-16/32, apple-touch-icon, android-chrome-192/512   (generated from the app icon)
robots.txt, sitemap.xml, site.webmanifest
```

## Brand usage

The **elbow** name is set in a licensed display font whose licence covers image use only.
Always present the wordmark as the supplied picture (`assets/logo-wordmark.png`) — never as live
text rendered in that font. Plain-text mentions of "elbow" in body copy use the site's normal
web fonts (Sora / DM Sans) and are fine.

The app links to `/privacy/`, `/terms/`, and `/support/` on this domain (from Settings and the paywall).

## Deploy

Any static host works (GitHub Pages, Netlify, Cloudflare Pages). Point the `elbow-app.com`
domain at it and ensure clean URLs resolve `/privacy/` → `/privacy/index.html`.

## Copyright & licence

© 2026 Aga Drapinska-Tonge. All rights reserved.

This repository is public for transparency and hosting only — **no licence is granted**. The code,
content, design, and assets here may not be copied, reproduced, modified, or reused without written
permission. The **elbow** name, wordmark, "e" mark, and app icon are brand assets / trademarks of
Aga Drapinska-Tonge and are not licensed for any use.

Built by [byaga.dev](https://byaga.dev).
