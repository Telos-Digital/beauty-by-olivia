## Meta
| Field | Value |
| Project | Beauty by Olivia |
| Last Active | 2026-09-19 |
| Status | shipping |
| Location | /home/wner/beauty-by-olivia |
| Repo | Telos-Digital/beauty-by-olivia (public) |
| Live URL | https://telos-digital.github.io/beauty-by-olivia/ |

## Current State
Live on GitHub Pages with the gingham design. The gallery works as a category
slideshow: it shows one category at a time by name ("1 of 9"), prev/next
arrows and swiping step through them, and a "+ all categories" button opens
the full list. It opens on Olivia's Favorites. Before & Afters are pairs of
photos side by side. The hero scissors use the floral band pattern.

## Next Action
Add the new batch of photos the user is sending, each tagged with its category.

## Blockers
None technical. Everything outstanding needs information from Olivia.

## Open Questions
- Keep the name "Olivia's Favorites"? The user was unsure about naming it.
- Is "black gloss" right under Dimensional Brunettes? It was a guess.
- Facebook profile URL for Olivia Dixon, to turn the mention into a link.
- More photos? Three are up. Six would fill two rows evenly in both designs.
- Does she want a phone number on the site at all, or is booking enough?
- Street address for The Blonde Magnolia, or is the booking link enough?
- Buy `beautybyolivia.com`? It appears unregistered. About $10 the first year,
  $14 to $19 to renew, and it would make a real forwarding email possible.

## Session Log
### 2026-09-19 (category slideshow)
- The user found the category row crowded. It was fine with borders, just not
  pill-shaped ones. The gallery now shows one category at a time: the current
  name in script with "N of 9", square arrows on each side of the photos, and
  swipe on touch. The full list hides behind a "+ all categories" toggle (the
  + becomes a − when open) and closes after a pick. The list buttons are
  squared, thin-bordered boxes, with the selected one filled in wine.
- The arrows sit outside the photos above 1240px and overlap the edges below
  that, at a smaller size on phones. Pushed in commit 140608e.
### 2026-09-19 (floral scissors)
- The hero scissors now use the floral band pattern instead of solid pink. I
  baked them into `images/scissors-floral.webp` by clipping the floral tile to
  the scissors' alpha and adding a thin wine outline. Opacity went from 0.55 to
  0.8 on desktop and to 0.6 on phone, because the pattern is lighter. The old
  `scissors.webp` is kept but no longer used. Pushed in commit b4f6f9f.
### 2026-09-19 (favorites, before & after pairs)
- Replaced "All" with Olivia's Favorites, which is also the default view. The
  user didn't want the name "Highlight" because it clashes with the hair
  service. All three current photos are marked as favorites.
- Before & Afters became `.ba-pair` cards: two halves side by side with a wine
  line between them, labeled before/after. There are two placeholder pairs,
  which stack one per row on a phone.
- The user disliked the pill-shaped tab borders, so the tabs are now plain
  italic text with an underline on the selected one. Tried gold dot separators
  first and dropped them, because each wrapped line started with a stray dot.
- The gallery layout switched from CSS grid to flex so a category with a
  single tile shows it centered. Pushed in commit 5137b02.
### 2026-09-19 (gallery categories)
- Olivia asked for her work to be grouped by category: Blonding, Highlights &
  Lowlights, Balayage, Lived-In Color, Dimensional Brunettes, Fashion Color,
  Haircuts & Styling, and Before & Afters.
- Added filter buttons above the gallery. The grid is now four columns on desktop.
  Photos are tagged with `data-category`, and a script builds a patterned
  placeholder tile for any category without a photo. Adding a photo is one
  `<div class="gallery-item" data-category="...">` line.
- Tagged the existing photos. Caramel is balayage and honey is highlights. Black
  gloss went under brunettes as a guess, still to be confirmed.
- Pushed in commit 8d85d0b. New photos from the user come next.
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
