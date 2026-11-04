## Meta
| Field | Value |
| Project | Beauty by Olivia |
| Last Active | 2026-11-03 |
| Status | shipping |
| Location | /home/wner/beauty-by-olivia |
| Repo | Telos-Digital/beauty-by-olivia (public) |
| Live URL | https://telos-digital.github.io/beauty-by-olivia/ |

## Current State
Live on GitHub Pages with the gingham design. Hero: five real shoot photos in
the double-gold frame. About: a muted looping clip of Olivia. Gallery now has
seven real photos (favorites view shows five) plus the first real before-and-
after pair (grown-out blonde to bright blonde). Products I Love is filled in:
four milk_shake leave-ins (Whipped Cream, Incredible Milk, No Frizz Glistening
Milk, No Frizz Glistening Spray), each card a bottle photo cropped from
Olivia's own shelf shot, a one-sentence description, and a link to the
brand's US store. One "photos coming soon" before-and-after placeholder remains.

## Next Action
Ask Olivia about extensions (her shirt lists it as a service), the phone
number on her shirt, and her Facebook URL; add more gallery pairs as they come.

## Blockers
None technical. Everything outstanding needs information from Olivia.

## Open Questions
- Where should the scissors go on phones, if anywhere? They're hidden at 760px and narrower.
- Keep the name "Olivia's Favorites"? The user was unsure about naming it.
- Is "black gloss" right under Dimensional Brunettes? It was a guess.
- Facebook profile URL for Olivia Dixon, to turn the mention into a link.
- More photos? Three are up. Six would fill two rows evenly in both designs.
- Does she want a phone number on the site at all, or is booking enough?
- Street address for The Blonde Magnolia, or is the booking link enough?
- Buy `beautybyolivia.com`? It appears unregistered. About $10 the first year,
  $14 to $19 to renew, and it would make a real forwarding email possible.

## Session Log
### 2026-11-03 (video autoplay on phones)
- The user's phone showed a play button on the About clip instead of playing.
  Two likely causes: iOS Low Power Mode blocks autoplay until a touch, and
  the reduced-motion guard stripped autoplay when iOS Reduce Motion is on.
  Removed the guard; added JS that sets muted/defaultMuted, calls play() on
  load, and retries on the first touchstart/scroll/click/keydown and on
  visibilitychange, unhooking once the video reports "playing". preload is
  now "auto". Could not reproduce Low Power Mode headlessly; needs the
  user's phone to confirm.
### 2026-11-03 (milk_shake products, four more gallery photos)
- The user dropped two shelf photos of Olivia's milk_shake products and four
  client photos into Downloads. Products identified from the bottles: Whipped
  Cream (leave-in foam), Incredible Milk (12 effects leave-in), No Frizz
  Glistening Milk (125 ml), No Frizz Glistening Spray (100 ml).
- Official product pages are on us.milkshakehair.com. The site answers 429 to
  every direct fetch (bot protection), so the URLs were confirmed through the
  search index of that domain, not by loading them. Spot-check in a browser.
- Products section rebuilt: the fixed wash-day/color-care/styling/treatment
  labels are gone (the user said the slots need not keep them). Each card is
  now an `<a>` to the product page with a bottle crop
  (`images/product-*.webp`, cut from IMG_4960) shown via object-fit:contain
  in a 210px box, the script kicker reads "milk_shake", and a small "shop it"
  underline sits at the bottom.
- Gallery: `blonde-before.webp` + `blonde-after.webp` are the same client in
  the same pink floral top, so they became the first real `.ba-pair`. The
  after shot also stands alone under Blonding (favorite). Two copper shots
  went under Dimensional Brunettes (`copper-waves.webp` favorite,
  `copper-waves-2.webp`). Favorites view now shows 5 tiles (4 + 1).
### 2026-11-03 (real photos in the hero, video in About)
- The user dropped seven photos and one short video from Olivia's branded
  shoot into Windows Downloads. Five photos replaced the four faceless stock
  hero slides (`images/olivia-*.webp`, pre-cropped to 4:5 at 960x1200, q80).
  Two full-length shots (IMG_4958 with extension swatches, IMG_4959 skirt
  swish) were left out of the hero; keep them in Downloads for later use.
- The About "O" monogram became the video: `images/olivia-twirl.mp4` (540px
  wide, h.264 crf 30, no audio, 457 KB) with `olivia-twirl-poster.webp`.
  Autoplay muted loop playsinline; JS strips autoplay under reduced-motion.
  Frame is a 4:5 double-gold rectangle (300px, 260px on phones) rather than
  the old 220px circle, because a full-body twirl is too small in a circle.
- Photos revealed two leads: Olivia's shirt lists EXTENSIONS as a service
  (not on the site) and carries a phone number, partly hidden. Ask her.
- Stock hero WebPs (`salon-*.webp`) deleted from the repo.
### 2026-09-22 (roomier hero)
- The user said the hero words felt squished, especially on mobile, and asked
  for a bigger section. Hero padding went up on every layout (computer 76/92px,
  stacked 72/88px, phone 60/76px), the gap between words and photo grew
  (56px stacked, 48px phone), and the phone headline went from 2.1 to 2.35rem
  with more space under it and the description. The words were already full
  width on phones, so this was about vertical room.
### 2026-09-19 (mobile opens at bottom)
- The user reported that the site jumped straight to the bottom on their phone
  when opening the link. It couldn't be reproduced in Chromium's iPhone
  emulation, and WebKit isn't installed. Likely causes: a shared or reopened
  URL carrying `#contact` (nav taps wrote the hash into the address bar), or
  Safari scroll restoration.
- Fix: `history.scrollRestoration = 'manual'`, strip any hash on load, and
  `scrollTo(0,0)`. In-page links now `scrollIntoView` smoothly without
  writing the hash. Tested hash URL, menu taps, and reload after scrolling.
  Still needs confirming on the user's real phone.
### 2026-09-19 (roomier hero text, scissors closer)
- Computer hero: the photo column is 0.7fr against 1.3fr for the words, the
  text max-width is 540px (the lead paragraph now fits on two lines), and the
  scissors sit at `left:calc(100% - 12px)`, tucked into the centered text's
  empty right margin, with a 170px reserve. Swept 1440 to 761 wide: no
  overlap and no overflow.
### 2026-09-19 (tall upright scissors)
- The user said the small scissors looked like an emoji. "welcome, y'all" is
  back to centered on its own. The scissors are baked upright with blades up
  into `images/scissors-upright.webp` (rotated 137 degrees, 510x834), and
  absolutely positioned at `left:calc(100% + 26px)` of `.hero-inner`, with
  `top:0; bottom:0`, so they match the text's height exactly.
  `.hero-words` padding-right reserves their width.
- Dead end: sizing a flex column from the text's height (with aspect-ratio or
  a ResizeObserver) creates a feedback loop, because wider scissors squeeze
  the text, which gets taller, which widens the scissors. Absolute
  positioning avoids it.
- The headline now uses `clamp(2.3rem, 3.5vw, 3rem)` with nowrap, and the
  columns change at 1200px, so the scissors never pass the gutter. Swept
  widths from 1440 down to 400: no headline overflow and no horizontal
  scroll. Hidden at 760px and narrower; phone placement is an open question.
### 2026-09-19 (bigger scissors accent)
- The user wanted the scissors bigger: 108px on computer, 78px on phone. A
  negative top margin lets them grow into spare space above without pushing
  the headline down. The first try overlapped the "f" in "feels", so they got
  a small bottom margin to stay clear of the headline.
### 2026-09-19 (rectangle photos, scissors as accent)
- The user said the phone layout looked horrible with the scissors as their
  own element beside the photos. The scissors are now a 62px accent (48px on
  phone) inline next to "welcome, y'all", so the words get the space.
- Arch frame changed to a rectangle, keeping the double gold border. Computer
  layout is two columns, photos then words; tablet and phone stack words over
  photos.
- Lesson: the user wants the scissors as a small accent near the text, never
  a standalone element that claims space.
### 2026-09-19 (hero layouts, spray photo)
- The user asked for separate computer and phone layouts. It's one CSS grid
  with `grid-template-areas`: "photos words scissors" above 1000px, and
  "words words" / "photos scissors" below that. The scissors are a grid child
  again, back at full size and tilted, and never overlap the frame. On phones
  I checked there's a measured gap between the frame and the scissors.
- The user found the color-bowl photo gross, so it's replaced with
  `salon-spray.webp` (Pexels 28994645, a hand spraying a bottle onto copper
  hair from behind, no faces). No visible mist; the only mist close-ups found
  were skincare or plant shots.
### 2026-09-19 (faceless hero photos)
- The user doesn't want faces or stylists in the stock photos, because it's a
  one-woman business, not a salon company. Removed `salon-stylist` and
  `salon-color`. Added `salon-roundbrush` (Pexels 14615061) and
  `salon-colorbowl` (Pexels 3993292). Re-cropped `salon-curls` to remove a
  blurred background face, and confirmed the `salon-blowdry` crop leaves out
  the stylist's smile.
- The user disliked the scissors overlapping the photo frame, so they're now a
  small flourish under the hero buttons, not overlapping anything.
### 2026-09-19 (hero photo slideshow)
- Added four free stock photos to the hero, cropped to 4:5 WebP at 960x1200
  (~60-120 KB each) in `images/salon-*.webp`. Sources: Pexels 10028673
  (blow-dry with round brush), Unsplash WXmHwPcFamo by Adam Winger (stylist
  blow-drying), Pexels 3065171 (curls), and Pexels 3993312 (color
  application). Both licences are free for commercial use with no attribution
  required; the IDs are recorded in an HTML comment.
- They crossfade every 5.5 seconds inside an arched gold frame, echoing the
  About monogram. The scissors moved onto the frame's corner.
- The user doesn't want to hard-refresh after pushes. GitHub Pages sends
  `max-age=600` and that header can't be changed, so the page can be up to 10
  minutes stale for recent visitors only. Stopped telling the user to press
  Ctrl+F5.
### 2026-09-19 (smoother slideshow, products)
- The "+ all categories" toggle is now small, soft text with no box.
- Slideshow transition: the old set slides out with a fade, the new set
  slides in from the direction of travel, and the stage height eases between
  categories. A step counter stops rapid clicks from tangling, and motion is
  skipped under prefers-reduced-motion.
- Added a "Products I Love" section on blush between the gallery and About,
  plus a Products nav link. Four text-only cards say "Her pick coming soon",
  with no invented brand names.
- Pushed the code and these notes together, so Pages runs one build. Last time
  a second push cancelled the first build and delayed going live by a few
  minutes.
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
