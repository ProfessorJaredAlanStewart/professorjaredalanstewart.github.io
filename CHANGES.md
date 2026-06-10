# Site upgrade — June 2026

Drop these files into the repo root (they replace existing files and add new ones).
Old .jpg files are included in optimized form so nothing external breaks, but all
pages now serve .webp.

## Fixed
- **Duplicate Open Graph tags** on index.html — two competing sets meant link
  previews (Canvas, Teams, social) could grab the wrong title/description.
  Now one canonical set.
- **Social card**: og:image was a 509KB portrait photo; platforms want 1200×630
  landscape. New `og-card.jpg` generated from the JFK photo, used sitewide.
- **No reduced-motion support**: reveal animations, stripe shimmer, and smooth
  scroll now all respect `prefers-reduced-motion` (CSS + JS).
- **No skip-to-content link**: added (keyboard/screen-reader users).
- **Images**: all photos converted to WebP (~1MB lighter sitewide), QR card
  PNGs quantized (roughly half size), `loading="lazy"`, `decoding="async"`,
  and explicit width/height added to prevent layout shift.

## New
- **JSON-LD structured data** on index.html: Person schema + each flagship
  project marked up as a free `LearningResource`. This is what lets Google
  surface CAP/TIA/Treks for education-related searches. Validate at
  https://search.google.com/test/rich-results
- **"Mark Your Ballot" wayfinding strip** under the hero quote: routes
  students → Treks, instructors → projects, the curious → impact stories.
  Checkbox fills in on hover. (See note on the #impact anchor below.)
- **404.html** — on brand. "What's next?"
- **robots.txt + sitemap.xml** — then submit the sitemap in Google Search
  Console (free, 5 minutes) so the LearningResource markup gets crawled.
- **License line in the footer**: I used CC BY-NC-SA 4.0 as the suggested
  default — *confirm this is the license you actually want* (BY-NC-SA = credit
  required, no commercial use, adaptations shared alike). Swap the link/text
  if you prefer CC BY or another.

## After deploying
1. Submit sitemap.xml in Google Search Console.
2. Re-scrape your URL at https://developers.facebook.com/tools/debug/ and
   https://www.linkedin.com/post-inspector/ so cached previews update.
3. Confirm the license choice in the footer.

## Round 2 (same day)
- **Image stretch fix**: the width/height attributes added for layout stability
  map to CSS properties as low-priority hints; the stylesheet overrode width
  but not height, so the clapperboard photo rendered 340px x 1200px. Added a
  base `img { height: auto; }` rule to all four pages — attributes still
  reserve layout space, class-level rules (gallery crops) still win.
- **"Drop CAP into your LMS" panel** on projects.html, directly under the CAP
  card: collapsible 5-step adoption guide (skim → scope → LMS assignment →
  rubric → localize) with an email CTA. The home-page ballot's instructor
  choice now deep-links to it (projects.html#adopt-cap) and it auto-opens
  on arrival.

## Round 3 — Show Up in Fort Worth (publish-ready)
- New page show-up-fort-worth.html with verified speaker/comment card
  mechanics from the City Secretary's instructions.
- "Show Up" added to the nav on all four existing pages; the new page's nav
  highlights itself in gold like the others.
- sitemap.xml updated with the new URL.
