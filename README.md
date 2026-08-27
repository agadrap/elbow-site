# elbow-site

Marketing + legal site for **elbow**, served at [elbow-app.com](https://elbow-app.com).

Static, hand-coded HTML — no build step. Mirrors the structure of `life-in-uk-site`.

## Structure

```
index.html            Landing page (hero, inside-the-app, features, how-it-works, privacy, CTA)
about/index.html      About / story
privacy/index.html    Privacy Policy   →  /privacy/
terms/index.html      Terms of Use     →  /terms/
support/index.html    Support + FAQ    →  /support/  (contact: hello@byaga.dev)
assets/site.css       Shared nav + footer + subpage typography
assets/logo-wordmark.png   Licensed "elbow" wordmark (white, transparent) — used for the logo lockups
assets/logo-mark.png       "e" mark (white, transparent)
assets/app-icon-1024.png   App icon — source for the favicons
assets/og-image.png        1200×630 social share image (headline + three angled phones)
assets/og-card-source.html Source used to render og-image.png
assets/screen-*.webp       App screens, 760px wide, web-optimised
                           (dashboard, rooms, appliance, stains, appliances)
favicon.ico, favicon-16/32, apple-touch-icon, android-chrome-192/512   (generated from the app icon)
robots.txt, sitemap.xml, site.webmanifest
```

## Brand usage

The **elbow** name is set in a licensed display font whose licence covers image use only.
Always present the wordmark as the supplied picture (`assets/logo-wordmark.png`) — never as live
text rendered in that font. Plain-text mentions of "elbow" in body copy use the site's normal
web fonts (Sora / DM Sans) and are fine.

The app links to `/privacy/`, `/terms/`, and `/support/` on this domain (from Settings and the paywall).

## Regenerating the share card

`assets/og-card-source.html` is a standalone 1200×630 page; `assets/og-image.png` is a
screenshot of it. It pulls in `app-icon-1024.png`, `logo-wordmark.png` and three of the
`screen-*.webp` files from the same folder, so open it straight from `assets/`.

Render at 1200×630 with a 2× device scale factor, then downsample to 1200×630 — that keeps
the type crisp. Anything that screenshots a page will do (headless Chrome, Playwright, or
just a browser window sized to 1200×630).

**After changing the image, bump the cache-buster.** `index.html` points at
`og-image.png?v=2`; Slack, LinkedIn, X and iMessage cache share previews aggressively by
URL, so a new card at the same URL will not appear until the query string changes.

## The "Inside elbow" section

`#inside` on the landing page: a decorative fan of all five screens, then a viewer that
shows one screen with its copy. Self-contained — CSS and the small script both live in
`index.html`, no dependencies.

- Auto-advances every 15 s. The active dot is a pill that fills over the dwell, so the
  rotation reads as deliberate rather than twitchy.
- Pauses on hover, on keyboard focus, when scrolled out of view, and when the tab is
  hidden. Clicking a dot jumps to that screen and restarts the 15 s clock.
- `prefers-reduced-motion: reduce` disables the auto-advance, the crossfade and the fill.
- Left/Right arrows move between dots.

To change the dwell, edit `DWELL` in the script **and** the `15s` in the
`.inside-dot[aria-current="true"] .fill` animation — they have to match.

Adding or removing a screen means adding a `.inside-slide` in both `.inside-shots` and
`.inside-copies` (matching `data-slide` index) plus one more `.inside-dot`. The script
picks up the count on its own.

## Screen captures

The `screen-*.webp` files come from the raw iOS Simulator captures in
`../elbow-screens/` (iPhone 17, 1206×2622), **not** from `../elbow-screens/app-store/` —
those have App Store marketing captions and device frames baked in, which clash with the
site's own layout and framing.

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
