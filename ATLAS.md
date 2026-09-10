## Meta
| Field | Value |
| Project | Beauty by Olivia |
| Last Active | 2026-09-10 |
| Status | shipping |
| Location | /home/wner/beauty-by-olivia |
| Repo | jimmyardis/beauty-by-olivia (public) |
| Live URL | https://jimmyardis.github.io/beauty-by-olivia/ |
| Alt design | https://jimmyardis.github.io/beauty-by-olivia/gingham.html |

## Current State
Live on GitHub Pages, verified by HTTP 200 and a render check on the deployed
URL. One static page, no build step: hero, service menu with three haircut
options and three colour-maintenance plans, a five-tile gallery, an about
section, and an inverted contact block. Booking runs through Olivia's real
Mangomint page at The Blonde Magnolia. Pushed exactly as designed in the
mockup, with no edits to the markup.

## Next Action
Pick which of the two designs is the real site, then replace the placeholder
phone number `(000) 000-0000`, which is visible on both.

## Blockers
None technical. Everything outstanding needs information from Olivia.

## Open Questions
- Editorial or gingham? Both are live; only one should be.
- What is the real phone number, and should it appear at all?
- Does `hello@beautybyolivia.com` exist as a mailbox?
- Is `@beautybyolivia` the correct Instagram handle?
- Street address for The Blonde Magnolia, or is the booking link enough?
- Is there a custom domain, or does the github.io URL stand?

## Session Log
### 2026-09-10
- Pushed the gingham design as `gingham.html` alongside the editorial
  `index.html`, so both art directions are live and comparable. Chose not to
  overwrite the live index, since the ask was to push the file, not to replace
  the site. Reversible either way.
- The gingham file is the *earlier* mockup, saved three minutes before the
  editorial one that shipped yesterday. Four byte-identical copies were sitting
  in Downloads.
- Flagged a real performance problem: `gingham.html` is 3.3 MB because two
  decorative PNGs are embedded as base64 data URIs, one of them 2.4 MB. That
  needs extracting and compressing before this version could be the main site.
- Verified both URLs return 200 with the correct content.

### 2026-09-09
- Took the approved mockup from Windows Downloads, set it up as a repo, and
  shipped it to GitHub Pages as `jimmyardis/beauty-by-olivia`.
- Pushed the markup byte-for-byte as designed. Launch hygiene was deliberately
  left off rather than changing an approved design without asking: no meta
  description, no Open Graph tags, no favicon, no LocalBusiness structured data.
- Live with five placeholder contact and gallery values, listed in the README.
  The phone number `(000) 000-0000` is the one that actually looks broken to a
  visitor.
- The repo is public because GitHub Pages requires it on this account tier.
