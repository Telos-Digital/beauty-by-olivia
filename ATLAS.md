## Meta
| Field | Value |
| Project | Beauty by Olivia |
| Last Active | 2026-09-10 |
| Status | shipping |
| Location | /home/wner/beauty-by-olivia |
| Repo | Telos-Digital/beauty-by-olivia (public) |
| Live URL | https://telos-digital.github.io/beauty-by-olivia/ |

## Current State
Live on GitHub Pages, verified by HTTP 200 and a render check on the deployed
URL. One static page, no build step: hero, service menu with three haircut
options and three colour-maintenance plans, a five-tile gallery, an about
section, and an inverted contact block. Booking runs through Olivia's real
Mangomint page at The Blonde Magnolia. Pushed exactly as designed in the
mockup, with no edits to the markup.

## Next Action
Get Olivia's Facebook profile URL so the social mention becomes a real link, and
decide on the `beautybyolivia.com` domain.

## Blockers
None technical. Everything outstanding needs information from Olivia.

## Open Questions
- Facebook profile URL for Olivia Dixon, to turn the mention into a link.
- More photos? Three are up. Six would fill two rows evenly in both designs.
- Does she want a phone number on the site at all, or is booking enough?
- Street address for The Blonde Magnolia, or is the booking link enough?
- Buy `beautybyolivia.com`? It appears unregistered. About $10 the first year,
  $14 to $19 to renew, and it would make a real forwarding email possible.

## Session Log
### 2026-09-10 (correct design promoted)
- **The wrong design had been live all along.** The user clarified that the
  editorial mockup was a throwaway and the gingham one is the real site. Promoted
  `gingham.html` to `index.html` and removed the editorial page from the site.
  It stays in git history.
- Fixed the weight problem as part of the swap: extracted the two decorative
  PNGs that were embedded as base64 into `images/floral-band.webp` and
  `images/scissors.webp`. **The HTML went from 3,233 KB to 17 KB**, with 132 KB
  and 4 KB of images beside it. The floral band was downscaled to 760px tall,
  twice its 380px display height, and still tiles seamlessly.
- Verified no request failures and no `base64` string left in the page.
### 2026-09-10 (moved to Telos-Digital)
- Moved the site off the personal account. Full history, both designs and all
  three photos now live at `Telos-Digital/beauty-by-olivia`, verified serving at
  https://telos-digital.github.io/beauty-by-olivia/.
- Route taken: the user created the empty repo in the browser and added
  `jimmyardis` as a collaborator; I accepted the invitation over the API and
  pushed. `gh auth login` was a dead end — its device flow needs an interactive
  terminal and hangs in this environment.
- **Collaborators on a personal repo only ever get write access.** Role levels
  like Admin are an organization feature. That means the repo owner has to
  enable Pages in the browser; it cannot be done over the API from here.
- The old repo at `jimmyardis/beauty-by-olivia` is still live and untouched,
  pending the user's decision to delete or archive it.
- Local remotes: `origin` now points at Telos-Digital, `jimmyardis-old` at the
  original.
### 2026-09-10 (photos)
- Added three real photos of Olivia's work, supplied by the salon owner, to both
  designs. Every "photo coming soon" placeholder is gone.
- Converted to WebP at 1000px wide, quality 80: 530 KB of JPEG became 352 KB.
  Lazy-loaded, with width and height set so the layout holds while they load.
- Both galleries are now a three-up. The editorial mosaic became a plain
  portrait grid, since the original mosaic assumed landscape crops and these are
  all 3:4 portrait.
- Caught an aspect-ratio bug in the render check: the `height` attribute beat the
  CSS `aspect-ratio` because `width` was also set, stretching every tile to its
  full 1333px. Fixed with `height:auto`.
- The third photo shows a client's face. Held it back until the user confirmed
  the owner had her consent, then added it.

### 2026-09-10 (later)
- Removed every invented detail from both live designs: the phone number
  `(000) 000-0000`, the address `hello@beautybyolivia.com`, and the unconfirmed
  Instagram handle `@beautybyolivia`. The client confirmed the email was not
  real.
- The contact card now leads with online booking, which is the only real
  channel, and names Olivia Dixon on Facebook as plain text. Deliberately not
  linked: a name is not a URL, and guessing one risks pointing at a stranger.
- Verified on both live URLs that nothing fake survives.
- Checked domain availability: `beautybyolivia.com` has no DNS records and
  appears unregistered.

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
